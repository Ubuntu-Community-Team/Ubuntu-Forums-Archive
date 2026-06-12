---
title: "Cannot mount regioned DVDs, others work fine."
date: 2008-05-06
forum: General Help
---

### Post by fbuchele on 2008-05-06
Exactly like the title says, I can't seem to mount regioned DVDs on my computer. The problem I think lies in recognizing the udf filesystem, however. 

I recently went to china and bought some regionless dvds there, they only contain two episodes so it is possible that they are of filesystem iso9660 since they are small. All of my regionless dvds mount manually, they don't automount, but I don't mind. Regardless, I can't mount my region 1 dvds, I used to a while ago, but then I started using a different computer to watch movies. I have tried manual and automounting, and changed iso9660,udf to auto in etc/fstab. I fear the problem might be in mounting udf filesystems.

Manual mounting yeilds, after a minute and a bit of cd drive activity,
```
fox@fox-laptop:/media$ sudo mount -t udf /dev/scd0 /media/cdrom0
mount: No medium found
```

/etc/fstab reads 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6ebbcdbe-2aaa-463f-bf0f-6af189f0200b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b4be4f05-3834-4808-8064-cb8aae9ba68b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto	user,noauto	0	0
#foxedit: added following lines, changed some spacing on the above line and changed noauto to auto changed type from
# udf,iso9660 to auto, added exec below
/dev/sdb1 	/media/usb 	auto	user,auto,exec	0 	0
/dev/sdb2 	/media/usbpart	auto	user,auto,exec 	0 	0

```

Any other cds mount normally, is09660's as well.

dmesg | tail yeilds

```
[  830.044303] ISOFS: changing to secondary root
[ 2480.451324] UDF-fs: No partition found (1)
[ 2480.527333] ISOFS: Unable to identify CD-ROM format.
[ 2482.855091] cdrom: This disc doesn't have any tracks I recognize!
[ 2520.835879] UDF-fs: No partition found (1)
[ 2520.913026] ISOFS: Unable to identify CD-ROM format.
[ 2571.907633] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO

```

Any other information I will happily provide.

---

### Post by fbuchele on 2008-05-07
Bump

I've been working on this for a month or two, and I can't figure it out. libcss is installed, and ive played regioned dvds before, just can't mount themnow. Any settings i might have messed with that would cause this?

---

### Post by fbuchele on 2008-05-07
edit: oops double post

---

### Post by fbuchele on 2008-05-07
Ok so new update: The problem (at least one of them) appears to be in the partitions. Gparted told me after I insert an unregioned movie that it couldn't detect the file type, it appeared in Gparted as an unformatted disk and appeared on my desktop as a blank dvd.
I inserted a regioned tv show and it didn't appear on gparted or on my desktop. Again, manual mounting on both does nothing.

Can anyone help?

---

### Post by dasunst3r on 2008-05-07
If you want to play those DVDs, you will need a package called libdvdcss.  Try looking here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by fbuchele on 2008-05-07
If you read above instead of just the title, you would see i mentioned that above in different ways... i've installed the entire libdvdcss package and everything, as a matter of fact a few months ago i could mount AND play dvds.

However, if you had redirected the misguided but appreciated helpfulness and read above, the problem is not with PLAYING regioned dvds, it's with MOUNTING them.

---

### Post by fbuchele on 2008-05-09
BUMP

No matter, I'm not going to let this thread die. Surely theres someone out there with more than my cursory knowledge of linux and ubuntu...

---

### Post by fbuchele on 2008-05-10
BUMP
Bump
bump

Hmm it looks like no one is helping. Well, for all those who don't visit this page, allow me to plug my blog! While you don't respond, please check out my blog, [www.foxoutofthebox.blogspot.com](www.foxoutofthebox.blogspot.com).  Thanks!

---

### Post by mc4man on 2008-05-10
> Exactly like the title says, I can't seem to mount regioned DVDs on my computer. The problem I think lies in _recognizing_ the udf file system, however.
usually it would be helpful to mention what ver. of ubuntu your using though in this case probably doesn't matter. If a file system isn't _detected_ then the media can't be mounted by any means. In most cases it's not a defect of the os in recognizing the file system, more likely a defect of the drive,or rarely the media itself. (in regards to udf 1.02)
You could try - booting to a slightly earlier kernel, a fresh install of the os, clean or replace the drive. Or ...
You could browse thru this thread, try some of the things suggested. While it took 6 wks. to exhaust the possibilities  the solution is in post #79
[http://ge.ubuntuforums.com/showthread.php?t=645470](http://ge.ubuntuforums.com/showthread.php?t=645470)

---

### Post by fbuchele on 2008-05-13
Ok sorry, I'm using a few different Hardy Kernels, I boot to different ones every once and a while, so I don't think the earlier kernel is the solution. 

And thanks for the link to the other page. The problem on there was that the guy couldn't read DVDs. However, I tried his solutions and they didn't work. The problem is not with mounting DVDs, the problem is mounting *regioned* DVDs. Unregioned DVDs mount just fine. These are not video CDs or other media related CDs, I can assure you they are 100% unregioned DVD goodness.

---

### Post by sevensevens on 2008-05-14
I'm having this problem as well.  I managed to get totem to say "you need to install libdvdcss" by replacing totem-gstreamer with totem-xine.

---

### Post by fbuchele on 2008-05-15
No, unfortunately, you are **not** having this same problem. Your problem is caused by not installing the codecs required to read the DVDs. However, I assume if you are getting that error message that you can mount the DVDs, just not play them. Meaning, they appear on the desktop, and you can browse in the DVD, but can't play the DVD. For that solution, there have been many posts on the solution, one even in this post. 

Yet again, I can mount reigionless DVDs, just not Regionless ones. Meaning, I put the regioned dvds, region 1, into my drive and it works for a sec, and does... nothing. Doesn't show up on the desktop, or in the computer. It isn't there. A regionless DVD is put in, works for a sec and... mounts correctly. Appears on the desktop and in the computer.

---

### Post by chrisccoulson on 2008-05-15
I don't know if it would cause your problem or not, but have you tried regionset to set the region code for your player?

---

### Post by ellgor on 2008-05-15
Hi, 

I have had similar problems, some DVDs will play while others wont even register, same for some CDs and suchlike (even using VLC).

Anyway, I have found a little workaround (works for me, on Gutsy 7.10) which goes like this this.

You will need K3B, something similar might work but I haven't tried it, start K3b in the very first column it should mention your dvd drive with the legend   No medium present, insert the disc you want to play and wait until all activity is finished and the title of the disc is shown, or not, if no title has been made, when the disc has registered click on device and select load from the drop down menu, the dvd drawer will open and close and hopefully the customary-- A new medium has been detected--  window will appear, if it doesn't repeat this action until it does, once the medium window has opened,select-- open in a new window-- and carry on as normal from there, ejecting is just the reverse of what you just have done, hope this works for you.

Regards, Ellgor

---

### Post by fbuchele on 2008-05-16
Hey guys, thanks for the suggestions:

@chrisccoulson: I tried regionset with a regioned dvd in the drive and it outputs:
```
fox@fox-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
fox@fox-laptop:~$
fox@fox-laptop:~$ sudo regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
fox@fox-laptop:~$

```

@ellgor: This sounds like a temporary workaround I used to do with ogle, when i would tell the drive to read the disk right after i put it in, before it could tell me it couldn't read it. I'm downloading k3b right now, and I will test your fix and report on what happens.

Thanks again!

Edit: I tried your solution ellgor, and its not seeming to work, though my drive is making different noises than before...

---

### Post by mc4man on 2008-05-16
@ fbuchele 
the disks that you can play do you know if they are burned media? usually you can tell from the color, appearance on the media side.

---

### Post by fbuchele on 2008-05-17
Good question... I just looked and they don't appear to be burned media. The regionless dvds are part of a season set of House, M.D. Holding the regioned dvd on the shiny side next to the unregioned, i can't tell any difference in terms of coloring or anything else. As a matter of fact, on the unregioned DVD laser etched into the inner ring is the DVD logo with the little DVD picture, some chinese writing and then the words 'DISC 5' as in disk 5 of the 6 disk series. 

I think I can safely say that it isn't a burned DVD and it is of professional quality. Good question though.

---

### Post by mc4man on 2008-05-17
I once had a 'similar' issue with a dvd drive but it was quite some time ago and was mainly specific to plextor drives.(about the time feisty changed from hdx to sdx) You haven't mentioned your drive model.
What i'd love to know is in post 4 you mention that while using gparted you could 'see' your dvd drive, how did you do that?
In the vein of it doesn't hurt to try see if this has any effect
[http://ubuntuforums.org/showthread.php?t=767449&page=8](http://ubuntuforums.org/showthread.php?t=767449&page=8)  post 80  -all_generic_ide module

---

