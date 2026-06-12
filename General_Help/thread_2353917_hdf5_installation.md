---
title: "hdf5 installation"
date: 2017-02-26
forum: General Help
---

### Post by pasal on 2017-02-26
hey guys how can i see that i have installed *parallel* hdf5 (i.e. openmpi) and its path. In any case is there any link or way to install it properly.

---

### Post by oldos2er on 2017-02-26
Which version of Ubuntu?

Something like ```
apt policy libhdf5-openmpi*
``` should show if it's installed or not.

---

### Post by pasal on 2017-02-26
14.04
Generally i am trying to install the astrophysical hydro code FLASH


actually i typed 
 bin/suggestMakefile.sh
Searching for the following libraries: mpi hdf5 fftw netcdf papi
mpi found at:
   /usr/lib/openmpi
hdf5 found at:
fftw found at:
netcdf found at:
papi found at:


Although i have typed 
sudo apt-get install libhdf5-openmpi-dev
and there are also many hdf5 file in my system, I dont think I have installed it properly. I have searched everywhere and i stilled cant install it as i can see.
Any suggestions?

---

