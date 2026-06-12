---
title: "manual fsck?"
date: 2008-06-23
forum: General Help
---

### Post by thehereaway on 2008-06-23
I just started up my computer and its asking me to manually perform a fsck (?) and says something or another is mounted in read-only mode.

Im rubbish with computers so i've no idea whats happening or how to fix it :confused:

thanks

---

### Post by nick_h on 2008-06-23
To run fsck manually type:
```
sudo fsck <filesystem>
```

To read the manual page type:
```
man fsck
```

The filesystem must be unmounted first.  If it is the root filesystem then run the check from a Live CD.

---

### Post by thehereaway on 2008-06-23
> **nick_h said:**
> To run fsck manually type:
```
sudo fsck <filesystem>
```

To read the manual page type:
```
man fsck
```

The filesystem must be unmounted first.  If it is the root filesystem then run the check from a Live CD.

I cant use my live cd, because everytime i do it asks for a password :confused:

I didnt understand the first two steps, im logged into the root because it asked for a root password before i could continue.

---

### Post by aquavitae on 2008-06-23
You'll need to boot off your live cd. I don't know why its asking for a password - I've never seen that before.  Where exactly does it ask for the password?

Once you get on, open a terminal (under the applications menu) and type ```
sudo fdisk -l
```
This will show a list of all the partitions on your system (e.g. /dev/sda1, /dev/sda2, etc). If you have a normal setup (i.e. one hard drive, only ubuntu) it should show just two.  If you're not sure exactly what its showing, just post it here and we can tell you. Once you've seen your partitions, type ```
sudo fsck <device>
``` for each partition listed and not formatted as swap. In the normal system it will probably be just ```
sudo fsck /dev/sda1
```. That should sort out the problem.

---

### Post by thehereaway on 2008-06-23
> **aquavitae said:**
> You'll need to boot off your live cd. I don't know why its asking for a password - I've never seen that before.  Where exactly does it ask for the password?

Once you get on, open a terminal (under the applications menu) and type ```
sudo fdisk -l
```
This will show a list of all the partitions on your system (e.g. /dev/sda1, /dev/sda2, etc). If you have a normal setup (i.e. one hard drive, only ubuntu) it should show just two.  If you're not sure exactly what its showing, just post it here and we can tell you. Once you've seen your partitions, type ```
sudo fsck <device>
``` for each partition listed and not formatted as swap. In the normal system it will probably be just ```
sudo fsck /dev/sda1
```. That should sort out the problem.


it asks for a password after i have chosen the first option on the live cd and it has all loaded. it did it before and i remember one night it randomly worked and thats how i installed Ubuntu. It happens with like 6 live cds i have because i thought i had'nt copied the files onto the disc properly.

Its now asking for a password again, is there anyway i can do it without the live cd?

---

### Post by aquavitae on 2008-06-23
You need to boot of a separate drive to run fsck. There are ways to get around it but they are quite complicated, and it will probably be easier to get your password problem sorted out.  Can you post a screenshot of it asking for the password? Have you tried clicking ok without entering a password? The live cd doesn't have any passwords built in so I really don't knwo where its getting them from.

---

### Post by nick_h on 2008-06-23
> is there anyway i can do it without the live cd?
Another way to do it is to create a file called forcefsck in the root directory.
```
sudo touch /forcefsck
```
The next time you reboot it will run an fsck on the root device.

---

### Post by aquavitae on 2008-06-23
Didn't know about that. It will save a lot of time!

---

### Post by thehereaway on 2008-06-23
> **aquavitae said:**
> You need to boot of a separate drive to run fsck. There are ways to get around it but they are quite complicated, and it will probably be easier to get your password problem sorted out.  Can you post a screenshot of it asking for the password? Have you tried clicking ok without entering a password? The live cd doesn't have any passwords built in so I really don't knwo where its getting them from.

ok i chose 'start ubuntu in safe graphics mode' off the live cd to see if that would work, and it did so im going to try the steps you listed before. hopefully there are no consiquences from chosing safe graphics mode :confused:

EDIT: sorry if im not communicating my points very well, its been a bad day. i'm currently doing the fsck on my /dev/sda1 and then /dev/sda2 . did you say not to do a fsck on any devices listed as 'swap' ? cause i have a third one but it says 'swap'

i tried the second partition and it didnt do it and said 'could this be a zero-length partition?'

should i just try see if it works now that i have done the /dev/sda1 ?

---

### Post by aquavitae on 2008-06-23
It doesn't harm it to do fsck on a swap drive but its not really necessary. There's not problem with using safe graphics mode.

---

### Post by thehereaway on 2008-06-23
it worked, thanks alot guys

---

