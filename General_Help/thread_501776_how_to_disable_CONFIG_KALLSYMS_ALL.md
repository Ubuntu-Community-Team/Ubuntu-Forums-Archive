---
title: "how to disable CONFIG_KALLSYMS_ALL"
date: 2007-07-15
forum: General Help
---

### Post by stepan2 on 2007-07-15
hi guys. I was told on ubuntu kernel forums that in order to make my compiled kernel smalled , i was to disable CONFIG_KALLSYMS_ALL. Could you please tell me where i can disable this when compiling?

---

### Post by geraldm on 2007-07-16
In the top directory of the linux kernel source, you would normally prepare the source by

make mrproper
make menuconfig # use your choice of the option selection executables

After you have selected the options, you should have declined to select CONFIG_KALLSYMS
After the selections, there will be a hidden file named ".config" in the top directory.

Confirm this with 

grep "CONFIG_KALLSYMS" .config # should reply with something like this:
# CONFIG_KALLSYMS is not selected

# NOTE: I did not use CONFIG_KALLSYMS_ALL because I was referencing linus-2.6.21.1.
A later kernel may have that symbol, but the one I used does not have it. 

As an alternate method, if you have the file .config from the kernel you created,
/lib/modules/`uname -r`/source/.config
save this file; then in the top directory do "make mrproper", then copy the 
.config file into that directory;  edit the line(s) to comment out the symbol; then
do "make oldconfig"
This is a bit of quick and dirty work when the option changes are just one or two
simple changes.  This method is not guaranteed to work if there are dependency
changes. If it does not compile clean, use the first method only.

Gerald

---

### Post by stepan2 on 2007-07-16
thank you for the reply gerald. However , my problems have not been fixed as i hoped it would. the option only took of a couple of kbs on the deb package.i wonder how the ubuntu guys made their kernel so much smaller . myne is `93 mb9in .deb format while theirs is about 75 mb. i followed the following tut to compile the kernel:[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

