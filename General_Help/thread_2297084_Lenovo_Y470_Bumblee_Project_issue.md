---
title: "Lenovo Y470 Bumblee Project issue"
date: 2015-10-01
forum: General Help
---

### Post by legume2 on 2015-10-01
Hello All,

I have a Lenovo Ideapad Y470 running Ubuntu 14.04 LTS smoothly. 


This Laptop has a switchable graphics card and I have read extensively on people getting it to work. (I have an Nvidia 550M)

I was using this link: [https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo](https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo) under the section, "
[h=2]Lenovo IdeaPad Y470/Y570 and Toshiba SATELLITE P870"[/h]
So, here is what I did so far,

$ git clone git://github.com/Bumblebee-Project/bbswitch.git -b hack-lenovo
$ cd bbswitch
$ mkdir /usr/src/acpi-handle-hack-0.0.2
# cp Makefile acpi-handle-hack.c /usr/src/acpi-handle-hack-0.0.2
# cp dkms/acpi-handle-hack.conf /usr/src/acpi-handle-hack-0.0.2/dkms.conf

all good until this command
[B]
# dkms install -m acpi-handle-hack -v 0.0.2 


[/B]The error I get is: 

"Building module:
cleaning build area....
make KERNELRELEASE=3.19.0-30-generic KVERSION=3.19.0-30-generic modname=acpi-handle-hack....(bad exit status: 2)
ERROR (dkms apport): binary package for acpi-handle-hack: 0.0.2 not found
Error! Bad return status for module build on kernel: 3.19.0-30-generic (x86_64)
Consult /var/lib/dkms/acpi-handle-hack/0.0.2/build/make.log for more information"

The log file contains,

"DKMS make.log for acpi-handle-hack-0.0.2 for kernel 3.19.0-30-generic (x86_64)
Wed Sep 30 23:22:24 PDT 2015
make -C /lib/modules/3.19.0-30-generic/build M="$(pwd)" modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-30-generic'
  CC [M]  /var/lib/dkms/acpi-handle-hack/0.0.2/build/acpi-handle-hack.o
/var/lib/dkms/acpi-handle-hack/0.0.2/build/acpi-handle-hack.c: In function ‘dev_set_acpi_handle’:
/var/lib/dkms/acpi-handle-hack/0.0.2/build/acpi-handle-hack.c:68:20: error: ‘struct dev_archdata’ has no member named ‘acpi_handle’
  pdev->dev.archdata.acpi_handle = handle;
                    ^
make[2]: *** [/var/lib/dkms/acpi-handle-hack/0.0.2/build/acpi-handle-hack.o] Error 1
make[1]: *** [_module_/var/lib/dkms/acpi-handle-hack/0.0.2/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-30-generic'
make: *** [default] Error 2"


If someone could help me get this working I would be so happy.

Best Regards,
L

---

