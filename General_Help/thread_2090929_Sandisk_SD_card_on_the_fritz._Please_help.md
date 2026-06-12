---
title: "Sandisk SD card on the fritz. Please help"
date: 2012-12-03
forum: General Help
---

### Post by grubbles444 on 2012-12-03
Hello,

I recently purchased a video camera that will be arriving tomorrow and it needs an SD card due to it's lack of internal memory. I didn't think this would be a problem because I have a Sandisk 4gb sdhc that would work fine, Except....

For the past 7 months all this card has done is hold a copy of the ubuntu distro. I have lubuntu on my netbook, needless to say I had no reason to use the card. But about a month a go I purchased a desktop from a friend that had Vista on it. pretty awful stuff. So I attempted to put ubuntu on it. it didn't work. so I erased the files of the SD and used unetbootin to make a stick for various versions of ubuntu (none worked).

The last version I attempted to load onto the card failed. and the card is now unusable. if you access the card's memory in the file manage a window stating "input/output error" pops up repeatedly. 

I tried to use the disk utility to reformat it but I get an error stating that it failed because it is in use. 

I've attempted to unmount it using  the unmount command with the device name, as well as unmount command with the mounted directory name. it says it can't find it.

rubbles@Grubbles444:~$ sudo unmount /media/B6D8-152E
[sudo] password for grubbles: 
Sorry, try again.
[sudo] password for grubbles: 
sudo: unmount: command not found
grubbles@Grubbles444:~$ unmount /media/B6D8-152E
No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)
unmount: command not found
grubbles@Grubbles444:~$ unmount /dev/sdb
No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)
unmount: command not found
grubbles@Grubbles444:~$ sudo unmount /dev/sdb
sudo: unmount: command not found
grubbles@Grubbles444:~$ ^C
grubbles@Grubbles444:~$ 

Attempts to sshut the device down, erase the files, etc. result in an error message about not being able to find some nautalis thing because it doesn't exist.

Yes I'm one of those people that shouldn't use linux. Please help!

---

### Post by dcstar on 2012-12-04
> **grubbles444 said:**
> 
........
```
grubbles@Grubbles444:~$ unmount /dev/sdb
**No command 'unmount' found, did you mean:**
 Command '**umount**' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)
**unmount: command not found**
grubbles@Grubbles444:~$ sudo unmount /dev/sdb
sudo: unmount: command not found
grubbles@Grubbles444:~$ ^C
```


```
man umount
```

---

