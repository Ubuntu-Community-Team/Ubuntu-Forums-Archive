---
title: "installed ubuntu but cant find winxp anymore"
date: 2008-01-22
forum: General Help
---

### Post by robertoto on 2008-01-22
Hi I installed ubuntu on my compaq presario. i pressed install after a live cd boot up, then just about pressed all the default options. I was pretty sure that i would get a partitioned disk, but now I'm not sure. menu.lst, does not show winxp as a boot option. i only have ubuntu at the boot up. what can I do to check of my winxp files all all still there and boot it up??

---

### Post by JRanch on 2008-01-22
It is possible you overwrote your windows partition.  One of the steps during the install is to tell Ubuntu how to partition the drive for installation.  The options are something like these:

Use entire drive
Use all free space
Create custom partitions

If you selected the first and only have one drive, then windows is gone.

You can try checking what your partitions look like using gparted.  Open a terminal

sudo apt-get install gparted
sudo gparted

This will give you a visual representation of the partitions on your drives; and also allow you to edit them, so be careful with it.

---

### Post by robertoto on 2008-01-22
thanks for the reply!

here is what I get:

roberto@roberto-laptop:~$ sudo apt-get install gparted 
[sudo] password for roberto: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package gparted is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
E: Package gparted has no installation candidate 
roberto@roberto-laptop:~$ sudo gparted 
sudo: gparted: command not found 
roberto@roberto-laptop:~$

---

### Post by sekinto on 2008-01-22
Could you give me the result of typing "sudo fdisk -l /dev/sda" in terminal? You might have to change sda to hda, I don't know.

---

### Post by robertoto on 2008-01-22
great, I opened terminal and my pc froze... 
anyway, thats another problem.

response is:

bash: /dev/sda: No such file or directory

---

### Post by sekinto on 2008-01-22
Did you try hda?

---

### Post by robertoto on 2008-01-22
with /hda it says permission denied, then password and
unable to open

---

### Post by sekinto on 2008-01-22
Did you type in exactly this:
sudo fdisk -l /dev/sda

Then when it asks for your password you have to type in your password and press enter (you won't get any visual feedback for password characters like asterisks).

---

### Post by robertoto on 2008-01-22
ok I am a beginner! I wasnt typing that right

here it is:

roberto@roberto-laptop:~$ sudo fdisk -l/dev/sda 
fdisk: invalid option -- / 

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by sekinto on 2008-01-22
There should be a space between the -l and /dev/hda

---

### Post by robertoto on 2008-01-22
ok well

hda1 says linux
hda2 says extended
hda5 says linux swap/solaris

i'm guessing that means no ntfs or fat...

thanks

---

### Post by sekinto on 2008-01-22
Hmm. I wonder what file system is contained in the extended partition. I don't know how to check this out though terminal. Try downloading gparted "sudo apt-get install gparted" and then starting it "sudo gparted".

---

### Post by robertoto on 2008-01-22
one of my problems is that the pc with the problem (not this one) boots up in ubuntu but doesn't seem to recognize the built-in wiki, so I can install anything...

---

### Post by sekinto on 2008-01-22
Do you have all your software sources checked? Make sure you have them all checked and open synaptic package manager and try searching for it;

---

### Post by robertoto on 2008-01-22
I'm trying to work that out. I downloaded gparted packets on a usb stick. but i dont know how to have synapics recognize that. and i just dont know what else to do.

---

### Post by sekinto on 2008-01-22
Well if you download the .deb package you can do "dpkg -i (location of file on stick drive)".

---

