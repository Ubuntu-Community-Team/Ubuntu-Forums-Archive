---
title: "Can't configure/install med-2.3.1 because of hdf5"
date: 2007-10-10
forum: General Help
---

### Post by SI23 on 2007-10-10
I'm trying to install the med-2.3.1 library but when I ./configure I get the following error...

checking for H5open in -lhdf5... no
configure: error: either use HDF5HOME env. var. or --with-hdf5=<path>

I've got hdf5-tools and libhdf5-serial are both installed.  I've tried setting the HDF5HOME environment variable to various paths but I still get the same error.

From another website I think med-2.3.1 checks for libhdf5.so.0.0.0 and libhdf5.settings but libhdf5.settings is not in the ubuntu version of hdf5-tools and libhdf5-serial.  It is however in the Debian version.  Will it work if I use the Debian library or is there a better fix??

Thanks.

---

### Post by SI23 on 2007-10-10
After a day of looking at a problem 5mins after making the post I find the answer myself....typical

just apt-get install the libhdf5-serial-dev library!

---

### Post by Visitor.Q on 2008-06-04
Thanks, this hint is still helping people :)

Now my question would be what the use is of the other package, as it does not provide headers...

---

