---
title: "help mounting drives"
date: 2008-06-25
forum: General Help
---

### Post by spyderxombie on 2008-06-25
im running ubuntu live disk right now...how do i mount my drives so i can retrieve all of my old files??

---

### Post by fibster on 2008-06-25
What are you trying to do, recover? Also what drive do you mean, I do this a lot for rescue operations.

---

### Post by spyderxombie on 2008-06-25
> **fibster said:**
> What are you trying to do, recover? Also what drive do you mean, I do this a lot for rescue operations.

my windows just crashed so im switching to ubuntu and simply want to retrieve my old music videos ect... any help would be seriously appreciated.

---

### Post by breadbin on 2008-06-25
start off open a terminal and do 

```
sudo fdisk -l
```

that will show you the partitions on your hard disk. you should show us the output from that command and take it from there.

---

### Post by spyderxombie on 2008-06-25
> **spyderxombie said:**
> my windows just crashed so im switching to ubuntu and simply want to retrieve my old music videos ect... any help would be seriously appreciated.

my hard drives i have 2

---

### Post by spyderxombie on 2008-06-25
> **breadbin said:**
> start off open a terminal and do 

```
sudo fdisk -l
```

that will show you the partitions on your hard disk. you should show us the output from that command and take it from there.

i tried that command and nothing happened

---

### Post by VMC on 2008-06-25
> **spyderxombie said:**
> i tried that command and nothing happened

What do you mean nothing happened? You mean you got an error message or the drives in question didn't show up? something had to happen. Did you execute that command from a live cd or installed ubuntu?

Are these ex-Windows drives going to be usb drives installed in an enclosure or installed in your ubuntu system?

---

### Post by breadbin on 2008-06-26
start at the beginning. can you run windows anymore? your files are probably sitting on your hard disk but depends what you want to do with them. with the livecd you can view them, copy them to somewhere else etc but its only a temporary situation. are you planning to install windows again or ubuntu? you an have both. if you have 2 hard disks you can have windows on one and ubuntu on another or as i do ubuntu and windows on one and my files on another. 

which version of the livecd are you using? is it the right one for your machine? under applications->accessories menu pick "terminal" and a window should pop up. when you type 

```
sudo fdisk -l
```

in there what happens? it should display something

---

### Post by spyderxombie on 2008-06-27
> **breadbin said:**
> start at the beginning. can you run windows anymore? your files are probably sitting on your hard disk but depends what you want to do with them. with the livecd you can view them, copy them to somewhere else etc but its only a temporary situation. are you planning to install windows again or ubuntu? you an have both. if you have 2 hard disks you can have windows on one and ubuntu on another or as i do ubuntu and windows on one and my files on another. 

which version of the livecd are you using? is it the right one for your machine? under applications->accessories menu pick "terminal" and a window should pop up. when you type 

```
sudo fdisk -l
```

in there what happens? it should display something

this is what i got:
spyder@McNasty:~$ sudo fdisk -l
[sudo] password for spyder: 

Disk /dev/sda: 46.1 GB, 46103371776 bytes
255 heads, 63 sectors/track, 5605 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01f901f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5370    43134493+  83  Linux
/dev/sda2            5371        5605     1887637+   5  Extended
/dev/sda5            5371        5605     1887606   82  Linux swap / Solaris
spyder@McNasty:~$

---

### Post by breadbin on 2008-06-29
I think i'm probably out of my depth here but you have already installed ubuntu is that right? i got the impression you were just trying out the livecd. do you have the other hard disk connected now? 

what usually happens is that ubuntu (and most other linux distros) check to see if there is a windows partition and mount it automatically. unless its damaged in some way. you seem to only have 46Gb there. the swap partition is an extended one but thats fairly normal. i can't see any windows partitions there at all.

sorry i can't help you any further:( i was hoping that somthing like this would turn up in the fdisk output.


/dev/sda5 5371 5605 1887606 07 NTFS

then you could just mount it with

sudo mount -t ntfs /dev/sda5 /mnt/ntfs

but as it is I cant see your windows partition there unless its on the other drive. it is connected?

---

### Post by vanadium on 2008-06-29
Indeed, what kind of a drive is your second hard drive? It does not show up in the output of "sudo fdisk -l", which means it is not connected to the system.

---

