---
title: "Advanced partitioning. Getting as many mount points off the IDE and on to SATA"
date: 2008-06-11
forum: General Help
---

### Post by garethsimpsonuk on 2008-06-11
Basically I've tried and tried to boot ubuntu from my SATA drive on a board that doesn't support it using a PCI SATA controller and it's not happening, not right now anyway.

I'm gonna just go ahead and install on the IDE drive but I'd like to make the best of my situation by putting all the system mount points on to the SATA i.e. /var - so my home website is on the fast drive and /tmp etc.

The thing is I don't know what sizes and what FS to use. This is how I set up now:

IDE

/root - 8GB
/media/storage - 72GB

SATA

/home - 201GB
/swap - 2GB

Just to clarify I'd like to install all of the different mount points on to the SATA except /root as that has to be on the IDE to boot. The thing is I don't know what size to make them all.

I'd really like to get the install going and have it finished tonight so it would really help me out if someone could give me some advice.

Cheers

---

### Post by garethsimpsonuk on 2008-06-11
n e 1?

---

### Post by xebian on 2008-06-11
> **garethsimpsonuk said:**
> Basically I've tried and tried to boot ubuntu from my SATA drive on a board that doesn't support it using a PCI SATA controller and it's not happening, not right now anyway.

I'm gonna just go ahead and install on the IDE drive but I'd like to make the best of my situation by putting all the system mount points on to the SATA i.e. /var - so my home website is on the fast drive and /tmp etc.

The thing is I don't know what sizes and what FS to use. This is how I set up now:

IDE

/root - 8GB
/media/storage - 72GB

SATA

/home - 201GB
/swap - 2GB

Just to clarify I'd like to install all of the different mount points on to the SATA except /root as that has to be on the IDE to boot. The thing is I don't know what size to make them all.

I'd really like to get the install going and have it finished tonight so it would really help me out if someone could give me some advice.

Cheers



I'm not an expert on this, but I have 10gigs partition for all and I barely use 3gig.

I'm not sure about the rest, but I'm certain /home can be safely mounted on a diff part.  /usr and possibly /var & /or /tmp.  

Sizes may vary on what you intend to do.  I would say /tmp could get high if you do a lot of video stuff.

BUt for me, I have 10gigs for /root, 20gigs for /home.  

AS for fs type, the ext3 is quite good, though would say reiser is better.

---

### Post by garethsimpsonuk on 2008-06-11
thanx 4 the answer this is what I've done: 
( after thinking really hard about it all and finding out you can only have 4 partitions per disk bar the use of logical )

IDE
/ - 5 GB
/media/storage - 75GB

SATA
/home 193.9GB
/usr - 3GB
/swap - 2GB
/var - 5GB

I did have tmp on the SATA but it was 1 too many so it's with the root. 
Do you think tmp is more important than /usr? I learned that /usr is for my own installed apps so I thought this would be torrentflux, mythtv etc and assumed they would be important. when you say /tmp gets big, how big? as you can see, root and tmp have 5GB between them is this ok?
I have tried to set them up so the disk head wont have to move as much i.e. home, usr and swap are all together at the front.

I just need a bit of constructive criticism b4 it's not too late as I have a habit of reinstalling after a week if I think I can do it better!

---

### Post by garethsimpsonuk on 2008-06-11
anyone?

---

### Post by xebian on 2008-06-11
> **garethsimpsonuk said:**
> thanx 4 the answer this is what I've done: 
( after thinking really hard about it all and finding out you can only have 4 partitions per disk bar the use of logical )

IDE
/ - 5 GB
/media/storage - 75GB

SATA
/home 193.9GB
/usr - 3GB
/swap - 2GB
/var - 5GB

I did have tmp on the SATA but it was 1 too many so it's with the root. 
Do you think tmp is more important than /usr? I learned that /usr is for my own installed apps so I thought this would be torrentflux, mythtv etc and assumed they would be important. when you say /tmp gets big, how big? as you can see, root and tmp have 5GB between them is this ok?
I have tried to set them up so the disk head wont have to move as much i.e. home, usr and swap are all together at the front.

I just need a bit of constructive criticism b4 it's not too late as I have a habit of reinstalling after a week if I think I can do it better!

I guess you should be ok.  Some apps has temp files.   Say video encoding.  It could grow big- a decent movie could be as big as 8gig.

The 4 max is a DOS thing.  BUt you could make the 4th partition as logical and take the whole free space.  Then you could then repartition them as logically smaller ones.  Here is how I did mine,

```
root@kebian4:~# fdisk -l /dev/sda

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002d09d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        2432     9767520   83  Linux
/dev/sda3            2433        3648     9767520   83  Linux
/dev/sda4            3649       38913   283266112+   5  Extended
/dev/sda5            3649        4864     9767488+  83  Linux
/dev/sda6            4865        6080     9767488+  83  Linux
/dev/sda7            6081        8512    19535008+  83  Linux
/dev/sda8            8513       10944    19535008+  83  Linux
/dev/sda9           10945       13376    19535008+  83  Linux
/dev/sda10          13377       25534    97659103+  83  Linux
/dev/sda11          25535       38300   102542863+  83  Linux
/dev/sda12          38301       38913     4923891   82  Linux swap / Solaris

```

---

### Post by garethsimpsonuk on 2008-06-12
thanx 4 that m8. well my hard drive is now making a clicking noise but smartmontools isn't picking up errors. 
it sounds like it's on it's way out but it can't be as it's quite new. I also recieved a couple of errors. 
I'm wondering if it has anything to do with my partitions so I'm reinstalling with the guided setup just to see if it still clicks. It may be the heads havin to work real hard due to my part setup. 
It's probably dying and I'm just in denial!

edit: yea I kno of using logical partitions but I refrained from using them. I don't know why but I don't like the idea and prefer to stick to how the computer wants it and if that means 4 on each then so be it

edit: it seems to have stopped clicking now. what could this mean? maybe i should try just 3 partitions on the SATA

---

