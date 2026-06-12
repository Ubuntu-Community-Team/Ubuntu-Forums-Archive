---
title: "data recovery help please (fat32 partition nuked?)"
date: 2006-11-01
forum: General Help
---

### Post by Stochastic on 2006-11-01
Hi, so ever since the edgy apt-get dist-upgrade I've been trying to get a working system back on my harddrive (debian etch is the only disc I have that seems to work and I don't want to step back into the dark ages).  In the process of attempting a couple different install methods it looks like my partitions got screwed up.  I used to have a fat32 46gig (approx) hda4 partition (that I was not attempting to resize or move or edit), which houses the bulk of my files so I was extra carful not to touch it, and a 1gig (approx) swap space at the end of my drive.  Now partition editor shows a nice big chunk of free space where my data used to be and I don't know where I went wrong.  What steps can I take to recover those partitions?  I'm on the brink of throwing my laptop off my balcony, please someone help.

---

### Post by jallain on 2006-11-01
Have you got more info? From your description of hda4 it sounds like you had all primary partitions. You are limited to four partitions total on a hard drive. But your mention of a swap partition at the end seems to imply something else. If you indeed have (had) more than four partitions, the only way to do this is to have created an extended partition and then partition that into logical partitions. The first logical partition, if I remember correctly, will always start with 5 ie: hda5. Not sure what your situation is.

---

### Post by podunk on 2006-11-01
You might give this a try, it worked for someone this weekend:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Stochastic on 2006-11-01
My swap space was listed as hda5, this was what my dapper (or maybe it was breezy) install did way back when.  I assume it was an extended partition.

I also have a primary os partition at the beginning of the disc (hda1 ext3) and a /home partition after that (hda2 ext3), but no others.  These partitions were not deleted or ruined.

---

### Post by sefs on 2006-11-01
Before you do anything else you should image that disk with norton ghost 2003 or something simlar that if you muck up messing with the partitions you can always reimage and try again. most probably your data is there.

If your major worry is recoving data from your fat32 I would then boot up with something like knoppix and image it again but this time with dd_rescue to an extenal usb drive.  Then download a demo version of r-studio on a windows system and I suspect that may be able to scan the image file for a FAT 32 partition.  If you have not done much writing to the disk since your discovery, you may get lucky.

---

### Post by Stochastic on 2006-11-02
> **podunk said:**
> You might give this a try, it worked for someone this weekend:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I booted into the dapper liveCD, downloaded this program and started running it but then the CD froze and I had to reboot.  Upon reboot it would no longer boot into the CD but instead would go straight to GRUB error 15 (I tried multiple differnt liveCDs/installCDs and same result).  I am able to enter the bios and everything seems fine there (CD boot is still ahead of harddrive boot and everything is as it always was.  My CD drive does make some nasty grinding-like sounds now when I boot up now - with or without a cd in the drive.  It does look like my computer is able to network boot and I do have a old desktop that I'm running as a web server so I'm thinking the best way to fix this would involve a network boot/mount of one kind or another but I'm unsure of how to go about doing this.

I don't have norton ghost to do any disc image and my old desktop doesn't have enough room to house all 80gig from my lappy anyway.

Does anyone have any suggestions as to how I can recover this computer? It's only 6months old, I really don't want to see it die on me and I've got tons of important data on that missing partition.

---

### Post by Polygon on 2006-11-02
i had a similiar problem, i accidently copied to a fat32 drive without having write permissions or something and it completly owned it, linux nor windows could even detect it

so... to tell you the truth i downloaded a crack for a program called "getdataback fat32" ([http://getdataback-for-fat.runtime-software.qarchive.org/](http://getdataback-for-fat.runtime-software.qarchive.org/)) for windows..... since of course the reason i love linux is that i dont have pay 72 freaking dollars for a program that i will use once....

anyway that program saved a good majority of my data, although not everything was recovered, or it was in pieces

and you WILL most likely need a seprate, farly large hard drive to save the recovered data too.... if you been eyeing a bigger hard drive now is the time to invest in one! (i just used my dads 500 gb portable hard drive)

but yeah, do do anything to the partiton before you make an image of it, as the more you write to it the less chance you have of getting your stuff back

im not sure of a disk imaging program for ubuntu but finding one and saving it to your hard drive somewhere is a first.

---

### Post by Stochastic on 2006-11-02
any idea how to do any of this through a network boot?  it's looking more and more like that's my only option right now.

---

### Post by Polygon on 2006-11-02
well if you make an image somehow using a linux/ubuntu program, you will most likely be able to just specify where to save it, which be whereever your little network drive is

same thing with that getdataback program, you can specify where to save the recovered data

---

### Post by Stochastic on 2006-11-02
I can't actually boot the computer I'm trying to fix right now.  The CD drive wont boot anymore for some reason and the hard drive give me GRUB Error 15.  It looks like I need to figure out how to do a network mount of the hard drive or maybe a network install on a partition and then attempt to recover my fat32 partition.  Any suggestions?  My server is running ubuntu dapp[er right now, that's the only other machine on the network so I assume it would be the host for all these activities.  I'm completely new to network installs, so any howtos would be great.

---

### Post by podunk on 2006-11-03
Why don't you just remove the drive and sling it in the other computer as a slave drive? Change a few jumpers and you'll be good to go, no need to install anything, it's just another mount point that way.  USB external drives are a lot cheaper than data that took years to write. Once you have it in a working computer you may well be able to recover your data.

Partimage will do a fat 32 disk.
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Of course - the more you screw with it the greater the chance of data loss. How important is the data? If it's cut your wrist stuff I would try spin rite or send it off to a professional recovery service.

If it was just live in shame forever I think I would put the drive in the other computer as a slave then make an image of the drive. Once I had the image safe I would then see if the CG software could recover it.

Hope it works out for you!

---

### Post by Stochastic on 2006-11-03
> **podunk said:**
> Why don't you just remove the drive and sling it in the other computer as a slave drive? Change a few jumpers and you'll be good to go, no need to install anything, it's just another mount point that way.  USB external drives are a lot cheaper than data that took years to write. Once you have it in a working computer you may well be able to recover your data.


Well because laptop hard drives don't fit into desktop computer ide chains and I don't have an adaptor. ](*,) <---this is me.

---

