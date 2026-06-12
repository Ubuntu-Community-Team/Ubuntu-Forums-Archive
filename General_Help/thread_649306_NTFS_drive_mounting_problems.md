---
title: "NTFS drive mounting problems"
date: 2007-12-24
forum: General Help
---

### Post by FnordLoader on 2007-12-24
I've been using Ubuntu for about 2 months now, slowly making the shift from windows to Linux and now I'm almost finished. I've successfully moved most of my needed windows files over to an external NTFS drive with no problem mounting the external USB drive (80g WD800). 
I also have an NTFS 40g internal drive I use for extra important storage, and up until recently have had no problems mounting it with full access.
Fast forward to this morning when Azureus hard-locked everything and I did a hard reboot. I can no longer access the drive in Ubuntu OR Windows XP. QTparted crashes any time I attempt to select the drive (Gparted won't finish loading at all), and it doesn't show up in the explorer. 
In Xp, the drive shows up as H:/ drive, but cannot be opened, and if I try, I receive an error telling me the drive is "corrupted and/or has a hardware failure" (or something close to that)
Am I royally screwed, or is there a solution?

---

### Post by rabid9797 on 2007-12-24
first off, i would get a hardrive testing utility to see if the hardrive is physically damaged(unrecoverable becuase of corruption), i'd use something like hiren's boot cd to check this: [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

then, if everything checks out with that, see if you can use one of the recovery tools on that cd to fix corrupted sectors(if that really is the problem).

---

### Post by FnordLoader on 2007-12-24
Thanks! I'll try it Asap.

---

### Post by davenport651 on 2007-12-24
> **FnordLoader said:**
> I've been using Ubuntu for about 2 months now, slowly making the shift from windows to Linux and now I'm almost finished. I've successfully moved most of my needed windows files over to an external NTFS drive with no problem mounting the external USB drive (80g WD800). 
I also have an NTFS 40g internal drive I use for extra important storage, and up until recently have had no problems mounting it with full access.
Fast forward to this morning when Azureus hard-locked everything and I did a hard reboot. I can no longer access the drive in Ubuntu OR Windows XP. QTparted crashes any time I attempt to select the drive (Gparted won't finish loading at all), and it doesn't show up in the explorer. 
In Xp, the drive shows up as H:/ drive, but cannot be opened, and if I try, I receive an error telling me the drive is "corrupted and/or has a hardware failure" (or something close to that)
Am I royally screwed, or is there a solution?

I have this same problem this morning as well!  I just installed Azureus a few days ago and haven't touched my Linux box since.  Today, I boot up and attempt to view my NTFS drives in Nautilus.  I don't get an error or anything pointing directly to Azureus, but when I try to view the contents of the NTFS drive my screen goes black and the only way out is a hard reset.  I'm new to linux (user for only a few months) and this is the first time I've been afraid of losing data.

EDIT:  I'm trying to burn the CD that was linked, but can't find the link on that page to actually download the CD.  I swear, I've used a computer before, its just getting late and I must not be able to see the underline.

---

### Post by FnordLoader on 2007-12-30
Davenport651:
I couldn't find the link either. I downloaded it from thepiratebay.org
Although if your torrent client isn't working then that might not be an option. 

I've yet to find any errors using the CD. Could it be a mounting problem?

---

### Post by davenport651 on 2007-12-30
> **FnordLoader said:**
> Davenport651:
I couldn't find the link either. I downloaded it from thepiratebay.org
Although if your torrent client isn't working then that might not be an option. 

I've yet to find any errors using the CD. Could it be a mounting problem?

I eventually found a download link by doing a google search.  I ran all kinds of hard disk and partition recovery software from that CD, but everything would either crash with a "read error" or it would say that the hard disk was only 130 GB (the disk is actually 250 GB).  Weird thing is, when I connected this hard drive to my other computer it reads just perfectly.  I am backing up all of my data, then I'm going to plug it back into my Ubuntu machine.

If you have another physical machine, try connecting it to that.  Or maybe just place the drive on a different IDE or SATA channel.

FnordLoader, we'll get this figured out by the start of the new year.

EDIT:  My girlfriend was nice enough to inform me that I posted this on New Years Eve...  I guess it'll be a little after the new year begins.

---

### Post by davenport651 on 2008-01-13
Well, my problem appears to be a hardware issue.  My SATA hard disk mounts fine on another computer.  I've had all kinds of bulging and blown capacitors on this motherboard, maybe I was too quick to blame Linux.  This was a secondary machine so I may just pull out the drive and scrap the parts that are left.

---

### Post by daverich on 2008-01-14
i would suspect the power supply.

Kind regards

Dave Rich

---

