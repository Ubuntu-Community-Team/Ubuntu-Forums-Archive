---
title: "kernel deb package install error"
date: 2015-12-21
forum: General Help
---

### Post by ryadav on 2015-12-21
While updating the kernel (linux-image-extra-4.2.0-22-generic) using the package manager, part way through the GUI updater crashed. I am using kubuntu 15.10.

I am unable to correct the problem with, "sudo apt-get -f install", here is the output which say the, "unexpected end of file or stream".

$ sudo apt-get -f install

[sudo] password for yadav:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-extra-4.2.0-22-generic
The following NEW packages will be installed:
  linux-image-extra-4.2.0-22-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 162 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 265144 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-4.2.0-22-generic_4.2.0-22.27_amd64.deb ...
Unpacking linux-image-extra-4.2.0-22-generic (4.2.0-22.27) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-image-extra-4.2.0-22-generic_4.2.0-22.27_amd64.deb (--unpack):
 cannot copy extracted data for './lib/modules/4.2.0-22-generic/kernel/drivers/media/usb/pvrusb2/pvrusb2.ko' to '/lib/modules/4.2.0-22-generic/kernel/drivers/media/usb/pvrusb2/pvrusb2.ko.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-extra-4.2.0-22-generic_4.2.0-22.27_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How can I correct this error, doing an apt-get purge tell me to do a "apt-get -f install".

---

### Post by ian-weisser on 2015-12-21
install -f is the wrong tool; you don't have dependencies to resolve.

You must replace the broken package with a working package. That's easy.
Try:
```
sudo apt update                                        ## Update the package database
sudo apt-get clean linux-image-extra-4.2.0-22-generic  ## Delete broken package from local cache so it doesn't get reinstalled
sudo apt upgrade                                       ## Test the fix; download and install a fresh version of the package
```

---

