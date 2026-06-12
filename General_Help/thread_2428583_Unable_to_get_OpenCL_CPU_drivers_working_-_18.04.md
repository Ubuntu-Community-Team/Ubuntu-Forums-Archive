---
title: "Unable to get OpenCL CPU drivers working - 18.04"
date: 2019-10-05
forum: General Help
---

### Post by heydoubleu on 2019-10-05
I'm using Autodesk Maya on Ubuntu 18.04LTS and noticed slow performance along with this warning message
```
CPU acceleration for OpenCL is not supported; falling back to non-accelerated mode. Check that you have installed an OpenCL CPU driver on your system
```

After struggling for a bit installing various OpenCL related things with no success, I tried on CentOS 7.7 and was able to get it working installing the drivers from this page:
[https://software.intel.com/en-us/articles/opencl-drivers](https://software.intel.com/en-us/articles/opencl-drivers)

Just clicking the download button under "Intel® CPU Runtime for OpenCL™ Applications 18.1 for Linux* OS (64bit only)" and running the installer. Unfortunately doing the same on Ubuntu 18 the installer warns that the version is not supported (but is supported on 16.04LTS) and sure enough continuing the install anyway, still no luck.

As I mentioned I have also tried installing a lot of other things, pretty much anything with opencl in the name, including this:
[https://github.com/intel/compute-runtime/blob/master/documentation/Neo_in_distributions.md](https://github.com/intel/compute-runtime/blob/master/documentation/Neo_in_distributions.md)

which I thought was just a newer version of the same driver but that didn't work either, unless I installed it wrong. I really like 18 so I'd hate to have to use centOS or an older version of ubuntu just for this one thing so any help here is really appreciated!

---

### Post by dino99 on 2019-10-06
Follow this howto : [https://linuxhint.com/install_autodesk_maya_ubuntu_1804/](https://linuxhint.com/install_autodesk_maya_ubuntu_1804/)

---

