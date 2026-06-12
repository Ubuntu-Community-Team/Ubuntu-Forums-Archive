---
title: "Installing more than one distro"
date: 2007-03-07
forum: General Help
---

### Post by finferflu on 2007-03-07
Hi all, I just wanted to give a look at ZenWalk Linux and eventually install it alongside Ubuntu, but I'm a bit confused. This is how my partitions work:

hda1 ---> /home partition
hda2  ---> swap
hda3 ---> / partition

So, my main concern is the /home partition: will it interfere with the /home folder I will have in ZenWalk? I would like to resize hda3 and install it there, but I wouldn't like it to interfere with my Ubuntu settings. 
Also, will I lose any data just resizing hda3?

This is the first time I try a double Linux partition, so I'm quite new to this...

Thanks a lot for your time!

---

### Post by Kateikyoushi on 2007-03-07
No most likely you will not loose anything by resizing partitions but a backup of important data is always advised before playing with the HDD.
Neither your home or / will be effected as long as you do not set the mount points as / or /home in the other distro, but actual settings depend on the distro's installer.
Do not forget that you can't have more than 4 primary partitions.

---

### Post by finferflu on 2007-03-07
So what should the mount point for the next partition be?

---

### Post by maxamillion on 2007-03-07
I think you could (don't quote me on this because I could be wrong) just re-use both the /home and /swap for zenwalk so that both installs share it .... but if you were to try that, definitely backup everything in /home.

.... just a thought.

---

### Post by finferflu on 2007-03-07
Well, the point is that I don't want Ubuntu and Zenwalk sharing the same /home partition, I'm a bit worried it would mess up all my current configuration... I'm ok for them to share the swap partition though...

---

### Post by Kateikyoushi on 2007-03-07
Well the new partitions should be /, swap should be shared and if the installer let's you set the current /home as /media/hda1 so you can reach it but nothing will be changed by the settings you make in zenwalk, this is not crucial you can add it to fstab manually later.

I wouldn't make a new /home if it just for a try could make one later or use the existing one.

---

### Post by finferflu on 2007-03-07
> **Kateikyoushi said:**
> 
Neither your home or / will be effected as long as you do not set the mount points as / or /home in the other distro, but actual settings depend on the distro's installer.
Do not forget that you can't have more than 4 primary partitions.

> **Kateikyoushi said:**
> Well the new partitions should be /, swap should be shared and if the installer let's you set the current /home as /media/hda1 so you can reach it but nothing will be changed by the settings you make in zenwalk, this is not crucial you can add it to fstab manually later.


Sorry I'm a bit confused by those two statements. You said that I didn't have to set the mount point of my new partition as /, but then you said to set it as /... I think I didn't get what you said...
Sorry...

---

### Post by Kateikyoushi on 2007-03-07
Sorry what I meant your existing (ubuntu) / and /home should not be set as / or /home in the new installation, ubuntu / is of no use, if you do not want to change anything on /home set it as /media/something so you can still access it but it won't function as a /home partition.

The new partition's (what you make in zenwalk) mount poin should be / I would not make a /home for the time of the test, if you decide you keep zenwalk and want one later there are guides in the forum how to move the /home to it's own partition.

---

### Post by finferflu on 2007-03-07
OK, now it's clear, thanks a lot!
I think I got the point where I was confused: I can still have a / mount point, since it's on another partition. Now it's much clearer.

Thank you!

---

### Post by Redeyes_Gambit on 2007-03-07
Not 100% sure, (someone please correct me if I'm wrong) but I believe that whatever new partitions you make should come physically AFTER your current Ubuntu partitions. In other words, if you put some other partition before your current Ubuntu partition it may change the drive lettering/numbering scheme, causing weirdness. I did something similar and wound up having to re-install Ubuntu.

Another thing of note is that I have heard sharing a swap partition may kill hibernation. Not a big issue for me personally since I don't hibernate, but I figured it was worth mentioning.

---

### Post by finferflu on 2007-03-08
Thanks for the useful hints, I'll keep them in mind!

---

### Post by finferflu on 2007-03-08
Now I've got another problem: I can't resize hda3 without deleting it first. I've tried with the ZenWalk partition program and with Qtparted on Knoppix. I need to delete it first... I just want to resize it, I don't want to lose any data...

Any hint?

Thanks

---

### Post by Kateikyoushi on 2007-03-08
How much of that partition is used ? I would recommend the gparted live disc for resize.

---

### Post by finferflu on 2007-03-08
27% 
Knoppix is actually a liveCD distro, is it different from the gparted live disc?

---

### Post by ygarl on 2007-03-08
Honestly mate: if you have the resources (i.e. power supply, ports, money), just get a cheap 6 or 8 gig HDD and slap it in. I think I picked one up from one of my local PC hole-in-the-wall stores (you know them... they look like a Tandy/Radio Shack left abandoned for about a month, then opened by the bait shop guy down the road again). It cost me £10/$18 USD... Pick up a 2-way IDE cable and voila!
2 HDDs...

---

### Post by finferflu on 2007-03-08
Not easily achievable on a laptop I think...

---

### Post by Kateikyoushi on 2007-03-08
Indeed that's a good idea, we also have them in hard off 40GB for 40usd did not check the smaller ones but for testing could find really cheap ones.

Gparted live cd has the newest stable gparted which might work if knoppix does not, unfortunately it isn't 100% either but at least a small download.

As I expected you are also on laptop...

---

### Post by finferflu on 2007-03-08
Stupid CD drive! I can burn discs, but then it doesn't recognise them! So I can't boot from the gparted live cd... there must be a way to resize without deleting a partition...

---

### Post by Kateikyoushi on 2007-03-08
There is somebody just tried it today on the forum and it failed on the machine resulting in a data loss, does not sound very promising especially your hda3 is /.

---

### Post by Redeyes_Gambit on 2007-03-08
I've had good experience with gparted. Never had any data loss resulting from its use. Did you burn the disk at max speed? Sometimes burning at max makes the disk unusable. Does the gparted .iso have an md5 sum available on the site? Lol, I can't remember if it does or does not. Did you check the disk? 

If push comes to shove you can actually boot off the Ubuntu live cd and install gparted through synaptic. There are issues related to Ubuntu auto-mounting, but that can be disabled somehow I'm sure.

---

### Post by finferflu on 2007-03-08
Thanks for the hints.
I actually burn my cds at 4x and I md5 sum them with k3b.. I know it's a problem with my stupid CD (DVD-R/RW - whatever) Drive. It works only with certain brands.. I've just bought a 10 pack of blank cds, and it doesn't work either... so much money in the drain........

---

### Post by Redeyes_Gambit on 2007-03-08
I feel your pain. I have a stupid Sony removable drive that wont even take SONY disks! Eventually we wound up replacing the drive.

---

### Post by Redeyes_Gambit on 2007-03-10
Oh, I just remembered something! 

I triple boot between Ubuntu, Fedora, and Vista. When I logged in as root in Fedora, then logged out without logging back in again as a normal user it messed with Ubuntu. My theory is that Fedora changed the ownership of the hard disk Ubuntu was on to root, and when Ubuntu booted it couldn't write my user preferneces to the disk! So, I recommend the following:

1. Keep the EXACT same user name/user ID number for log on in all Linux-based OSes you install. That way any file you own in one OS, you will own in the other.

2. When setting up your *second* Linux distro, don't create a mount point for the root directory of the *first* Linux distro. That way you don't encounter any permission issues. Try to keep the drives that both OSes "see" to a minimum.

---

### Post by finferflu on 2007-03-10
Thanks a lot! I think that's precious information.

Now, I have a question about you #2 point:
When installing the second distro, what should I set as mount point? I thought / was fine, since it's / on another partition which hasn't got anything to do with the first.. Am I correct? Maybe I missed your point...

---

### Post by Redeyes_Gambit on 2007-03-10
Lol, yea sorry, I suppose I could have phrased that better. Let me try again :) . 

"/" is fine for the **[COLOR="Teal"]ZenWalk[/COLOR]** root partition mount point. I think "/" HAS to be the mount point for the root directory. What I'm trying to say is that most installers give you options to mount other detected partitions during set up. So, when installing **[COLOR="#008080"]ZenWalk[/COLOR]**, don't assign a mount point to the root partition of **[COLOR="#a0522d"]Ubuntu[/COLOR]**. So, according to what you said earlier, your hard drive currently looks like this to **[COLOR="#a0522d"]Ubuntu[/COLOR]**:

DRIVE---Mount Point
hda1 ---> /home
hda2 ---> swap
hda3 ---> / (**[COLOR="Sienna"]Ubuntu's[/COLOR]** root partition)

Basically we want to make it where each Linux distro has [COLOR="Red"]NO MOUNT POINT[/COLOR] for the other's root partition. **[COLOR="#a0522d"]Ubuntu[/COLOR]** should not mount **[COLOR="#008080"]ZenWalk's[/COLOR]** root partition and **[COLOR="#008080"]ZenWalk[/COLOR]** should not mount **[COLOR="#a0522d"]Ubuntu's[/COLOR]** root partition. This way permissions on system files remain separate. So, ideally this is how each distro SHOULD "see" the hard drive:

**[COLOR="#a0522d"]Ubuntu[/COLOR]** :

DRIVE---Mount Point
hda1 ---> /home
hda2 ---> swap
hda3 ---> / (**[COLOR="#a0522d"]Ubuntu's [/COLOR]**root partition)
hda4 ---> ([COLOR="#ff0000"]NO MOUNT POINT![/COLOR]) (**[COLOR="#008080"]ZenWalk's[/COLOR]** root partition)

**[COLOR="#008080"]ZenWalk[/COLOR]**:

DRIVE---Mount Point
hda1 ---> /home
hda2 ---> swap
hda3 ---> ([COLOR="#ff0000"]NO MOUNT POINT![/COLOR]) (**[COLOR="#a0522d"]Ubuntu's [/COLOR]**root partition)
hda4 ---> / (**[COLOR="#008080"]ZenWalk's[/COLOR]** root partition)

A tad clearer now?

---

### Post by finferflu on 2007-03-10
Much clearer now! That's the kind of explanation I was looking for, thanks. 

Anyways, I managed to break my HD (with a punch.. no comment), so I'm reinstalling Ubuntu right now on my brand new HD. The problem with the graphical installer is that I cannot choose the no mount point solution, so I've chosen /media/hda4, and I hope it will be fine...

Thank you!

---

### Post by Redeyes_Gambit on 2007-03-10
> **finferflu said:**
> ...I managed to break my HD (with a punch.. no comment)...

ROFL!

> **finferflu said:**
> ...I cannot choose the no mount point solution...

No problem. Once you have installed Ubuntu just edit your /etc/fstab file and remove the entry for hda4.

---

### Post by finferflu on 2007-04-08
Ok, I am now back to this topic with a new question. I need to reinstall Sidux, but everytime I install it after Ubuntu, I get its grub installed, which leaves out some of the Ubuntu boot options. I mainly need to use Ubuntu with the older kernel 2.6.17-10 which is the only one that supports my Wacom tablet so far. 
So, is it possible to either keep the Ubuntu grub, or to get the Ubuntu boot options back in some way?

Thank you!

---

