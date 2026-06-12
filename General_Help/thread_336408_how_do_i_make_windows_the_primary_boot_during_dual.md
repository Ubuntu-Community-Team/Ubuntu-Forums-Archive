---
title: "how do i make windows the primary boot during dual boot?"
date: 2007-01-11
forum: General Help
---

### Post by noktekniq on 2007-01-11
i have a laptop and i've recently partitioned the laptop to use dual boot. one partition for windows and another for ubuntu. i was wondering if it is possible to make windows the primary boot instead of the primary boot to be ubuntu. and how would i go about setting the time limit to choose the boot

---

### Post by bodhi.zazen on 2007-01-11
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by noktekniq on 2007-01-11
done thanks

---

### Post by zippy028 on 2007-01-11
Open in your favorite text editor " /boot/grub/menu.lst"  toward the middle of the file look for this section:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

 Beginning here you will see listed all of the kernels or OS's you are running. Windows will likely be the last entry and should be listed at the end of the file. scroll down the file and begin counting from zero to determine which in the sequence is windows. On my system it is six.  At the top of the menu.lst file find this section: 

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default	        6	

Change whatever number is currently there to whatever number your windows install is.

HTH,

John Wheat

---

### Post by marx2k on 2007-01-11
Remember that anything that takes a line (including "Other OS'es -- or whatever that line says) is considered an index item

So in this list:

Ubuntu
Ubuntu (Generic)
MemTest
[Other OS'es]
Windows XP
Windows Vista
MacOS X x86

XP would be index item 4

---

