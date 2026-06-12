---
title: "newbie broke ubuntu :( live cd wont help"
date: 2013-02-17
forum: General Help
---

### Post by yellowmans on 2013-02-17
hello newbie here
got this notebook, with old version of ubuntu instaled update, it crashed now im left w nothing eccept grub, terminal options at start up are : 
I-ubuntu 10.04.4 LTS kernel 2.6.32-45 generic
II-ubuntu 10.04.4 LTS kernel 2.6.32-45 recovery mode
III-ubuntu 10.04.4 LTS kernel 2.6.24-16 generic
IV-ubuntu 10.04.4 LTS kernel 2.6.24-16 recovery mode
1.option one will show 1.351596 kernel panic
2.option two will show command but no terminal
3.option three will show (initramfs)
4.option four (2.6.2416 recovery) will show dev/disk/by-uuid/b1e6baae-...does not exist doping to a shell(initramfs)
live cd will not load  help ;)its an old fujitsu with 500mb ram

---

### Post by Zteam on 2013-02-17
Is your BIOS settings set to boot from CD/DVD?

You need to have that at first boot prioritory otherwise it will try to use the installation on your harddrive.

On most compumters you can just press F12 or F2, to Select boot device (just for that boot session)

Hope that helps you :)

---

### Post by Bashing-om on 2013-02-17
yellowmans; Hi ! Welcome to the forum.

See if these tutorials get you back up.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)
[https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode](https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode)
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

Specific questions ? By all means post back.
[INDENT][INDENT]hope this helps

[/INDENT][/INDENT]

---

### Post by yellowmans on 2013-02-18
hello thank you for your response
yes i tried,i change boot in BIOS to CD rom but no luck, i think my disk wasnt the correct one, or that the notebook does not want to boot from it thanks

---

### Post by Bashing-om on 2013-02-18
yellowmans;
To verify the integrity of the .iso and the burned image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

How else can we assist to get you up on ubuntu ?
Not knowing your specs; UEFI or smart response might be factors.
[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by yellowmans on 2013-02-25
hello bashing om
i follow the instructions, it asked me to go to terminal and enter some comands like [EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ...Downloads
however i cannot enter into terminal. when i pres 'c' for comand it takes me to 
grub>
there the : [EMAIL="ubuntu@ubuntu"]ubuntu@ubuntu[/EMAIL] command does not work
help please?
i am getting another copy burned as the instructions in the second link thanks

---

### Post by yellowmans on 2013-02-25
hello bashing om
on the third booting option i get 
(initramfs)
i enter the 
[EMAIL="ubuntu@ubuntu-desktop:~$"]ubuntu@ubuntu-desktop:~$[/EMAIL] cd Downloads
command from the link you sent me and says 
/bin/sh: ubuntutu@....: not found

---

### Post by zero2xiii on 2013-02-25
Hay,

> ubuntu@ubuntu-desktop:~$ is the console line that shows when you open up a terminal. You only need to type whatever is AFTER the ":~$" part.. For example:
> ubuntu@ubuntu-desktop:~$ cd /media/
Then you type in a terminal:
```
cd /media/
```

For further debuging please post the output of the following commands (in the code brackets, the # sign at the top of the thread reply tool) while in the busybox environment (your third option listed):
```
pwd
ls /media/
ls /dev/ | grep sd
```

an example output might be:
```
~/:~$ pwd
/home/zeroburn

```
```
~/:~$ ls /media/
apt  cdrom  cdrom0  external  floppy  floppy0  Media  usb

```
```
ls /dev/ | grep sd
sda
sda1
sda2
sda5
sdb
sdb1
sdb2
sdb3
sdc
sdc1
sdc5
sdc6
sdc7

```

Please note that the "~/:~$" in my system will be different on yours. My shell environment is heavily modified... 

Good luck :)

Reference for busybox:
[http://manpages.ubuntu.com/manpages/dapper/man1/busybox.1.html](http://manpages.ubuntu.com/manpages/dapper/man1/busybox.1.html)

---

### Post by zero2xiii on 2013-02-25
Hay,

Just thought of something.... 

Have to tried to simply exit busybox? Give a few seconds after the prompt shows up and then simply type "exit" and slam on enter... Might just be a time out issue... I regrettably assumed you have tried this already...

:)

---

### Post by grahammechanical on 2013-02-25
It would help if you describe what you mean by "it crashed." And what you did for "update." for something has gone serious wrong. There is stuff missing from the OS for you to get those messages.

What version of Ubuntu are you trying to load a live session from? If it is a 64bit version and your CPU is 32bit then it will not run. Do you get any messages when you try to load the live session?

My suggestion is to

1) download the 10.04 ISO image and burn it to disk and try loading the live session from that.

2) get any data that you want to save off the hard disk

3) install Ubuntu 10.04 as a fresh install. You have about 2 months of support left on 10.04. That should be time enough to find out if the machine will run Ubuntu 12.04 or may be you need to install Xubuntu or Lubuntu. You also need to find out if the CPU needs a non-PAE kernel.

[http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

Regards.

---

### Post by yellowmans on 2013-03-01
Hello zero2xiii
ok. I entered in the (initramfs) comand line
pwd
/

I entered ls /media
no such file or directory

I entered ls /dev I grep sd (were I is capital i, i didnt find the vertical line in my keyboard)
No such file or directory
/dev/:
Console pts tty2 tty4 tty6
Null       Tty1 tty3 tty5
(initramfs)

---

### Post by yellowmans on 2013-03-01
Hello grahammechanical
i believe it had ubuntu 10.11 but not sure
then ububtu asked to update latest version and uptdates
almost sure it was version 12.something
then it crashed. I was hoping for the old version to be in there somewhere
but i guess you are correct i will look for the 10.04 version
thank you

---

### Post by yellowmans on 2013-03-01
Zero2xiii
exit gives me
gave up waiting for root device...
-boot arg
-check rootdelay...
-check root...
Alert! /dev/disk...dropin to a shell

---

