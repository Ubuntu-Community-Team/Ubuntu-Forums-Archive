---
title: "cp command"
date: 2014-06-07
forum: General Help
---

### Post by moehbon on 2014-06-07
Hi, 

I have been strugling in using this command for run a test a NETCDF-test. Thus, this test asks to include file from the NETCDF package be in this directory and copy it using cp command. Then:
cp ${NETCDF}/include/netcdf.inc

My only path to sth similar to /include/netcdf.inc is /home/my_user/WRF/Build_WRF/LIBRARIES/netcdf/include/netcdf.inc

However it keeps showing me this error:
cp: missing destination file operand after &#8216;/include/netcdf.inc&#8217;
Try 'cp --help' for more information.

How do I work with cp command? 


thanks

---

### Post by steeldriver on 2014-06-07
You need to tell it where to copy the file *to* - if you just want to copy it to the directory you're currently in, then you can specify that with a '.' or './'i.e.

```

cp /home/my_user/WRF/Build_WRF/LIBRARIES/netcdf/include/netcdf.inc  **.**

```
or (abbreviated)

```

cp ~/WRF/Build_WRF/LIBRARIES/netcdf/include/netcdf.inc  **.**

```

---

### Post by moehbon on 2014-06-07
Oh ok, 

I thought I had to use $ as well. 

thanks a lot

---

