---
title: "Problem with installing digimend kernel drivers"
date: 2018-06-16
forum: General Help
---

### Post by goldencoin44 on 2018-06-16
From what I understand to use the huion h610 pro tablet I need to install digimend kernel drivers. But when I try it I get this error 


/home/user/Documents/drivers/digimend-kernel-drivers-7/hid-uclogic-core.c:433:18: error: &#8216;HID_QUIRK_NO_EMPTY_INPUT&#8217; undeclared (first use in this function); did you mean &#8216;HID_QUIRK_MULTI_INPUT&#8217;?
  hdev->quirks |= HID_QUIRK_NO_EMPTY_INPUT;
                  ^~~~~~~~~~~~~~~~~~~~~~~~
                  HID_QUIRK_MULTI_INPUT
/home/user/Documents/drivers/digimend-kernel-drivers-7/hid-uclogic-core.c:433:18: note: each undeclared identifier is reported only once for each function it appears in
scripts/Makefile.build:312: recipe for target '/home/user/Documents/drivers/digimend-kernel-drivers-7/hid-uclogic-core.o' failed
make[2]: *** [/home/user/Documents/drivers/digimend-kernel-drivers-7/hid-uclogic-core.o] Error 1
Makefile:1577: recipe for target '_module_/home/user/Documents/drivers/digimend-kernel-drivers-7' failed
make[1]: *** [_module_/home/user/Documents/drivers/digimend-kernel-drivers-7] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.17.1-041701-generic'
Makefile:10: recipe for target 'modules' failed
make: *** [modules] Error 2

By installing it I just extracted the files from digimend-kernel-drivers-7.tar.gz, placed them in the documents/drivers/. then I opened the terminal and typed in 

cd Documents
cd drivers
cd digimend-kernel-drivers-7 
make.

---

### Post by mörgæs on 2018-06-17
HI, welcome to the fora.
Please begin with a link to the guide you are using.

---

