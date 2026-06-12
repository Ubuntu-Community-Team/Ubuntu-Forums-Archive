---
title: "[SOLVED] Grip not working with Plextor drive"
date: 2006-12-12
forum: General Help
---

### Post by jkroto on 2006-12-12
I’m trying to use Grip to rip cd’s but for some reason it does not want to work.  I can’t even get it to play cd’s.  I’m guessing it has something to do with the drive and recognition of the device but I can’t figure it out.   Other programs such as k3b work for burning and I can play dvd’s with xine.  Anyone have any ideas?  

The relevant parts are:
Edgy 64-bit
Grip from the repo’s
Plextor PX-755SA 16x SATA Internal DVD Burner

Note: I understand that k3b could be used to rip as well but I’m trying to stay with grip on my new Edgy install.

current fstab
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a6ee0d6e-93a4-41c2-9550-bfd8531f6853 /               ext3
defaults,erro$
# /dev/sda3
UUID=0e82479c-a335-40e3-a977-be2d737fd9c9 /home           ext3
defaults     $
# /dev/sda5
UUID=2589a7e3-6ead-4325-94b8-06bbd42139f2 none            swap    sw
$
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


---

### Post by logos34 on 2006-12-14
Grip is one of those older applications which requires an audio cable from the cdrom to the soundcard for cd playback.  (Most others can output digitally through the IDE cable).  

If you can see the track timer playing and you have a cable but still no sound, check that the 'CD' sliders in gnome volume or alsa aren't muted/turned down when you use grip.  Also, toggle the tiny speaker icon button in grip -- the slider should be all the way to the right.

What are your settings in config>rip>ripper and >options?  What's listed as 'Rip file format'?
Looks like your sata plextor is showing up as /dev/scd0 (reads sata as scsi device).  What shows up in 'CD' tab?  Paste a screenshot of you can.

---

### Post by jkroto on 2006-12-14
> **logos34 said:**
> Grip is one of those older applications which requires an audio cable from the cdrom to the sound card for cd playback.  (Most others can output digitally through the IDE cable). 

If this is an absolute then I guess it won't work from me since all the new SATA drives don't come with that extra cable/connection.  However, if it's only the sound I wouldn't mind if I can't hear it, as long as I can rip it.  I can listen with... 'Listen'  my player of choice at the moment.

>  What shows up in 'CD' tab?  Paste a screenshot of you can.

Never posted a screenshot but here goes.
I have config>>CD  and Rip (shown) both set to /dev/scd0.

Also, I can get the drive to recognized the CD.  But when I hit play it just cycles through the tracks, staying on each for only a second and then moving on to the next, and it just keeps looping like that without playing anything.
I did get grip to play a CD, without sound, by using an external USB drive.
Thanks for the help.

---

### Post by logos34 on 2006-12-14
Your ripper tab looks right.

You say grip playback (sans sound) works with a usb drive. Can you rip too? 

If so, my hunch is that grip won't work properly with an optical drive using serial ata protocol even though it recognizes the drive block device (as generic scsi device '/dev/scd0') -- again, it's an older program and probably hasn't been updated to take into account sata dvd/cd which even now is relatively uncommon (probably because there's no performance gain in having one when we have yet to reach bandwidth saturation in eide).  

Assuming for the moment this is not the case and it is a settings issue: You mean by 'recognized the cd' that grip is fetching track titles on your sata plextor? If so, click on the '123' button at bottom.  A bar will pop up.  Toggle the right button to '-|' Single-play mode and the button on left to 'N' Normal play mode. Go to config>rip and uncheck everything except 'poll disc drive for new disc.'  See if you can play a song all the way through. In config>rip>options uncheck everything except 'beep after rip.' On the rip tab 'rip partial track' should be unchecked.  Try to rip a track using grip's built-in cdparanoia. Then try cdda2wav or your local cdparanoia (if applicable). 

If no go, then it may be a sata issue.

---

### Post by jkroto on 2006-12-18
> **logos34 said:**
> Your ripper tab looks right.
You say grip playback (sans sound) works with a usb drive. Can you rip too? 


logos34,
thanks for the info.
What I found is that when I use the external USB drive it will play CD's in grip but no sound through the system (no cd cable) but if I plug headphones directly into the external dive I can hear it.  this makes sense considering that the sound doesn't pass through the usb cable.  I did not try to rip with the external drive, but my guess is that it would work.

I tried all of your ideas but grip will not play CD's with the SATA drive, _however_, I did change the paranoia setting from grip paranoia and to my surprise it will rip CD's.  So, even though I can't hear them I can rip them (passing data with SATA is ok, just not sound!?).  Also, by recognize the CD I mean that it goes out and gets the proper track info for the CD.

Thanks again for all your help.  Guess things won't change until the sata drives become more popular.  For now I can just rip with Grip and listen with something else.

---

