---
title: "Something is wrong with my package managing system"
date: 2024-03-12
forum: General Help
---

### Post by donnstewart on 2024-03-12
I like to use Synaptic to install and remove packages. I have rtl-sdr in my system, and I wanted to use it to look at FLEX pager traffic. I installed multimon-ng using Synaptic, that was fine, but the version there did not have support for FLEX pagers, so I went to GitHub to install from source the most recent version that has the FLEX pager demodulator. That build went fine, and I stopped before doing make-install. So I went to uninstall the package that came through synaptic, but I got an error, and the package did not uninstall (sorry I closed and rebooted without copying the error). But now Synaptic does not list the package as installed, that is, a white checkbox, not the green box for an installed package. if I check the box in Synaptic it only gives me the option to install. But the package seems to be still installed because if I put in the command multimon-ng in the terminal the program runs. And it is the Synaptic-installed version, not the one I built from source.

I am a little afraid to start a lot of command line stuff because I don't want to mess up my system. Any recommendations? Ubuntu 23.10, Linux 6.5.0-25-generic

Tried sudo apt-get upgrade and got these errors:

Building module:
Cleaning build area...
make -j6 KERNELRELEASE=6.5.0-25-generic -C /lib/modules/6.5.0-25-generic/build M=/var/lib/dkms/8192cu/1.10/build...(bad exit status: 2)
ERROR (dkms apport): binary package for 8192cu: 1.10 not found
Error! Bad return status for module build on kernel: 6.5.0-25-generic (x86_64)
Consult /var/lib/dkms/8192cu/1.10/build/make.log for more information.
dkms autoinstall on 6.5.0-25-generic/x86_64 succeeded for xtrx
dkms autoinstall on 6.5.0-25-generic/x86_64 failed for 8192cu(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.5.0-25-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.5.0-25-generic (--configure):
 installed linux-image-6.5.0-25-generic package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-6.5.0-25-generic
 linux-headers-generic
 linux-generic
 linux-image-6.5.0-25-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

