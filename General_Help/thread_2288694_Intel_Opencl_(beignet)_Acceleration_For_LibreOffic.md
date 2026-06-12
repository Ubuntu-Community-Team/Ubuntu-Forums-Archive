---
title: "Intel Opencl (beignet) Acceleration For LibreOffice - How Can I ?"
date: 2015-07-29
forum: General Help
---

### Post by redger on 2015-07-29
I'm running a standard Ubuntu Trusty install, upgraded to current.

I'd like to use OpenCl to accelerate spreadsheet calculations in LibreOffice Calc .... making use of the iGPU on my Haswell CPU

I tried install beignet from this ppa  [https://launchpad.net/~pmjdebruijn/+archive/ubuntu/beignet-testing]("https://launchpad.net/~pmjdebruijn/+archive/ubuntu/beignet-testing") along with   ocl-icd-libopencl1.   It didn't seem to make any difference
I also found [https://github.com/OpenKinect/libfreenect2/issues/109]("https://github.com/OpenKinect/libfreenect2/issues/109"), which i didn't completely follow because there is some discussion at the end related to "just" using the ppa, and I didn't want to litter my installation with unnecessary packages (it's a host for many operations)

Presumably I've overlooked something ... but I don't know what. Can anyone advise ?

Also for reference [http://en.libreofficeforum.org/node/9119]("http://en.libreofficeforum.org/node/9119"), suggests there might be some challenges, though it's a bit out of date

---

### Post by grahammechanical on 2015-07-29
Do you have Libreoffice 4.2 or later? I do not use 14.04. I know what version is in 15.10 but not the version on 14.04.

Have you enabled OpenCL in Libreoffice Calc?

[http://en.libreofficeforum.org/node/7540](http://en.libreofficeforum.org/node/7540)

If you have Synaptic Package Manager installed you can search for OpenCL and you may find a library listed related to the video driver. The Software Centre does not help us here but Synaptic does.

I have Nvidia graphics and I am using the 304 driver and that package includes nvidia-opencl-icd-304. You may find something similar for Intel graphics.

Regards.



[URL="http://en.libreofficeforum.org/node/7540"]


[/URL]

---

### Post by redger on 2015-07-29
yes, I only ever use Synaptic :) and am using LibreOffice 4.2.8.2 and have enabled OpenCL.
As it happens I've also tried LibreOffice 4.4.5.2, which seems to have auto-enabled OpenCL

Beignet is the Intel software for OpenCL support, it's an add-on rather than being built into the standard i915 driver. Further, the version in the standard repositories is very old (v0.3 whereas v1.0+ is required) so I installed from a PPA, along with the OpenCL loader ocl-icd-libopencl1 ..... but LibreOffice didnt' recognise OpenCL

When I went to install the clinfo program it wanted to install NVidia packages, which i don't want on my system so I stopped short of that

Any suggestions welcome

---

