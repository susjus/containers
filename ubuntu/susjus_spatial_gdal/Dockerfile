# We recommend using Databricks Runtime versions 13.3 LTS
FROM databricksruntime/standard:13.3-LTS

RUN apt-get update \
  && apt-get install -y openssh-server \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Warning: the created user has root permissions inside the container
# Warning: you still need to start the ssh process with `sudo service ssh start`
RUN id -u ubuntu &>/dev/null || useradd --create-home --shell /bin/bash --groups sudo ubuntu

# https://mothergeo-py.readthedocs.io/en/latest/development/how-to/gdal-ubuntu-pkg.html
# GDAL Install
RUN sudo add-apt-repository ppa:ubuntugis/ppa && sudo apt-get update \
  && sudo apt-get update \
  && sudo apt-get install gdal-bin -y \
  && sudo apt-get install libgdal-dev -y \
  && export CPLUS_INCLUDE_PATH=/usr/include/gdal \
  && export C_INCLUDE_PATH=/usr/include/gdal \
  && pip install GDAL databricks-mosaic


