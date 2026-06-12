---
title: "Newb needs help with a external hard drive"
date: 2008-02-08
forum: General Help
---

### Post by aimhigher101 on 2008-02-08
I have a external hard drive and Ubuntu wont recognize it at all so im unable to access whats upon my hard drive (BTW its a usb hard drive) can any1 help me with this problem? need to know asap 
thanks

---

### Post by vanadium on 2008-02-08
Attach it to a windows system, have it checked, shut down Windows completely, then start windows up again and shut it down another time. After that, the file system will be clean and the drive will mount automatically under windows.

This might or might not help. You did not provide any information, so I cannot know what is causing the behaviour in your case. However, it frequently occurs that an external ntfs does not mount in Ubuntu because it was not properly disconnected at one time. Then what I said is the cure. If that does not work (it can't harm anyway), then the cause is somewhere else and we will need some more detail to tell what is wrong.

---

### Post by z-itou16 on 2008-02-08
hi.

i have a question, do you tried with other usb ports? 

also can you please open the terminal and type this 
> lsusb

please paste what output you get
thank i will try to help the most i can

---

### Post by aimhigher101 on 2008-02-08
this is what it said 
xeon@xeon:~$ lsusb
Bus 001 Device 006: ID 15d9:0a37  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 004 Device 001: ID 0000:0000

---

### Post by z-itou16 on 2008-02-08
ok thanks.

most of the time it should be mount in a tmp folder or something, anyways check in COMPUTER under places. check if you can find your hdd there. if not then reboot the machine with the hdd plug and check if it is mount. let us know.

---

### Post by aimhigher101 on 2008-02-08
i can see the hard drive but when i click upon it, it says :
Unable to mount the volume 'USB Virtual Machines'
Details:
$Log File indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1: Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have Windows then disconnect the external devices by      Clicking on the 'Safety Remove Hardware' icon in the Windows      taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for     your own responsibility. For Example type on the command line:    Mount -t ntfs-3g/dev/sdb1/ media/USB Virtual machines -o force Or add the option to the relevant row in the /etc/fstab file:     /dev/sdb1/media/USB Virtual Machines ntfs-3g defaults, force 0 0

all help is much appreciated

---

### Post by vanadium on 2008-02-08
You already got the help in the second post of this thread. From your last post, we are sure this is the cause.

---

