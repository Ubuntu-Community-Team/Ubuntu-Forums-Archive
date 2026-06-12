---
title: "i've moved root directory to /home"
date: 2007-04-14
forum: General Help
---

### Post by JackiePaper on 2007-04-14
I moved root directory to home-directory and shut the os down, obviously i can't start kubuntu anymore. How can I move those root files back?

---

### Post by aidanr on 2007-04-14
1) boot the live cd 
2) mount the partition(s)
3) move the folder back
4) reboot
5) cross fingers

---

### Post by JackiePaper on 2007-04-14
> **aidanr said:**
> 1) boot the live cd 
2) mount the partition(s)
3) move the folder back
4) reboot
5) cross fingers

I'm newbie with linux. Could you explain how can I mount that partition?

---

### Post by SishGupta on 2007-04-14
> **JackiePaper said:**
> I'm newbie with linux. Could you explain how can I mount that partition?

Just read steps one and two of this:

[http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)


How did you get root in your home anyway? that must have been one brutal mv

---

### Post by aidanr on 2007-04-14
i'll assume your root partion is hda (*sudo fdisk -l* will list the partitions), then open a terminal and type

sudo mkdir /tmp/hda
sudo mount /dev/hda /tmp/hda
sudo nautilus /tmp/hda

---

### Post by JackiePaper on 2007-04-14
> **SishGupta said:**
> 
How did you get root in your home anyway? that must have been one brutal mv

I was as root. I tried to move some stuff from the directory I was at the moment to the home directory. I typed: "mv /* /home". I forgot the comma before the "/".

---

### Post by JackiePaper on 2007-04-14
> **aidanr said:**
> i'll assume your root partion is hda (*sudo fdisk -l* will list the partitions), then open a terminal and type

sudo mkdir /tmp/hda
sudo mount /dev/hda /tmp/hda
sudo nautilus /tmp/hda

/dev/hda3 is my linux partition according to "fdisk -l" listing.

Two first line succeeded. I typed: 
"sudo mkdir /tmp/hda3"
"sudo mount /dev/hda3 /tmp/hda3"

After I typed "sudo nautilus /tmp/hda3" it said "sudo: nautilus: command not found".

What should I do?

---

### Post by aidanr on 2007-04-14
my bad, i forgot you are running kubuntu, so it should be

sudo konqueror /tmp/hda3

---

### Post by JackiePaper on 2007-04-14
> **aidanr said:**
> my bad, i forgot you are running kubuntu, so it should be

sudo konqueror /tmp/hda3

I typed "sudo konqueror /tmp/hda3", however there were some errors. I gave up and I decided to re-install kubuntu.

However, thank you for helping me.

---

