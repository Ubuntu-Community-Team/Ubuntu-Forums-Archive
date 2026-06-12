---
title: "Please enter runlevel:"
date: 2006-12-07
forum: General Help
---

### Post by Maelgwyn on 2006-12-07
I've hit a brick wall with my computer :(

I'm running Xubuntu 6.06 and when I turned the pc on this morning, it loaded up fine, but then gave me a blank terminal screen and asked for a runlevel!

I've tried everything from 1-6, but it just tells me that there are no processes left in this runlevel... So, I thought I'd be clever, boot into 'safe/restore' mode from GRUB, and backup everything up & just re-install. Heh, that failed too! I get 
```
root@none:
```, which isn't very helpful.... If I try to edit anything, I get told that I'm in a read-only environment!! ](*,)](*,)

Now normally at this point I'd just chuck it in and re-install, but I've got stuff in my home folder that I just don't want to lose! I can't burn any rescue CD's 'cause I've only got one drive and need that for the Live CD for Ubuntu, but I do have a 128Mb USB thumbdrive....

Can somebody please give me some advice for how to get my stuff off /home and transferred to my external HDD? Once that's done I can re-install... :)

OR, if somebody knows how to fix the run-level issue, that'd be just as great!

Thanks

---

### Post by Maelgwyn on 2006-12-07
OK - just to prove I'm not totally useless, I checked out my error message on google.com/linux and found an old thread about someone with the same error, and tried to enter failsafe 2 and dsl 2 at the prompt. Neither worked, so I tried failsafe2 [without the space] and got the same error message :(

Also, I've tried looking through / whilst logged in via the Live CD, but I'm not sure where to look to find my /home folder... :(

Please help!

---

### Post by averagejoe84 on 2006-12-07
Try to use a knoppix CD if you don't have knoppix CD you might be able to mount the drive with th Ubuntu live cd .. I'm not sure.. and mount you hard drive that should give you access to your home dir then you can move it off to a flash drive.

---

### Post by bodhi.zazen on 2006-12-07
First, take a look at the partition with the live CD.

Depending on the size of /home and your HD perhaps you can resize your partition, create a new one, and move your data into it preserving it from a re-install....

If that fails, try [austrumi](http://sourceforge.net/projects/austrumi/)

austrumi is a 50 mb Live CD and will boot to ram, then eject freeing up you CD for burning.

---

### Post by bodhi.zazen on 2006-12-07
> **Maelgwyn said:**
> OK - just to prove I'm not totally useless, I checked out my error message on google.com/linux and found an old thread about someone with the same error, and tried to enter failsafe 2 and dsl 2 at the prompt. Neither worked, so I tried failsafe2 [without the space] and got the same error message :(

Also, I've tried looking through / whilst logged in via the Live CD, but I'm not sure where to look to find my /home folder... :(

Please help!

LOL :lol:

You will need to mount your HD.

boot to the live CD

In a terminal type```
sudo fdisk -l
``` to list your partitions.

Now ```
sudo mkdir /mnt/hd
```

mount your partiton:```
mount /dev/hdxy /mnt/hd
```
Where hdxy is your xubuntu partition (? hda1 )

Now your old home directory is in:> /mnt/hd/home/user_name

---

### Post by Maelgwyn on 2006-12-07
> **bodhi.zazen said:**
> LOL :lol:

You will need to mount your HD.

boot to the live CD

In a terminal type```
sudo fdisk -l
``` to list your partitions.

Now ```
sudo mkdir /mnt/hd
```mount your partiton:```
mount /dev/hdxy /mnt/hd
```Where hdxy is your xubuntu partition (? hda1 )

Now your old home directory is in:



You're an absolute blessing. I could kiss you but I don't think you swing that way :lol:

I'm now copying everything over via command line to the external HDD - when I get home from work I'll re-install Linux :D

Thanks!!!

There was no point in me downloading Knoppix 'cause this computer doesn't have a cd-writer... *sigh* I'll have a new pc by February, so then I'll have all the fancy stuff ;)

---

### Post by bodhi.zazen on 2006-12-07
glad it worked out for you.  When you re-install consider a separate partition for your data.

Oh, and when you get home, open a terminal and type:```
I will back up my data
```100 times :twisted:

---

