---
title: "compile ideviceinstaller from Source Issue"
date: 2014-07-11
forum: General Help
---

### Post by abbas-h on 2014-07-11
hi

i install laitest libimobiledevice from source successfully 
all idevice command like ideviceinfo work like a charm ...

but when

i try get lastest version of ideviceinstaller and compile it get this error while make :

```
ideviceinstaller.c: In function ‘afc_upload_dir’:
ideviceinstaller.c:546:13: error: ignoring return value of ‘readlink’, declared with attribute warn_unused_result [-Werror=unused-result]
     readlink(fpath, target, st.st_size);
             ^
cc1: all warnings being treated as errors
make[2]: *** [ideviceinstaller-ideviceinstaller.o] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

```

install ideviceinstaller from apt-get wont work because is older than usbmux that i compiled

please help

---

### Post by mooreted on 2014-07-11
"[ideviceinstaller-ideviceinstaller.o] Error 1"

It looks like it can't compile a kernel module against the running kernel. Check the system requirements of the code and see if it requires a specific kernel version and make sure you have the linux headers installed for the current running kernel.

---

### Post by abbas-h on 2014-07-11
> **mooreted said:**
> "[ideviceinstaller-ideviceinstaller.o] Error 1"

It looks like it can't compile a kernel module against the running kernel. Check the system requirements of the code and see if it requires a specific kernel version and make sure you have the linux headers installed for the current running kernel.

how i check thiese item ?

in [https://github.com/libimobiledevice/ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller) i wont found any things

---

### Post by mooreted on 2014-07-11
Looks like a problem they are working on:

[https://github.com/libimobiledevice/ideviceinstaller/pull/6](https://github.com/libimobiledevice/ideviceinstaller/pull/6)

Here is their mailing list. I don't know if they answer support questions:

[http://lists.libimobiledevice.org/mailman/listinfo/libimobiledevice-devel](http://lists.libimobiledevice.org/mailman/listinfo/libimobiledevice-devel)

---

