---
title: "Few Feisty MythTV Setup Questions"
date: 2007-08-03
forum: General Help
---

### Post by fkzdiceman on 2007-08-03
Hey All,

I have a MythTV backend/fronted system up and running, but I have a few questions.  First my specs:

P4 2 GHz
1GB RAM
80GB HD for OS
500GB HD for MythTV
Hauppauge PVR 150 with remote for capture
NVIDIA GForce 4 4600 for video output (S-Video)


1.  Display is very dark.  TV and DVDs look dark.  If it is a night scene you can't see anything!  Is there a setting to brighten things up a bit?

2. MythVideo works for some MPEGs and WMVs that I have, but it won't play my AVI files.  The AVIs are from a Canon Powershot.  I have tried the internal player, mplayer and xine but nothing has worked yet.

3. Video playback looks OK, but not great.  I used to have a DVR from my cable company and it looked just as good as watching cable.  With MythTV, live TV and recorded programs do not look that great.  Is this just the way MythTV is, or are there some tweaks I am missing?  Is it my hardware?  Should I install the proprietary drivers?

4. I have a Dell Wireless 1450 Wireless USB Adapter, but I can't get it to work.  It is recognized by Ubuntu, as what it is, but I don't think it is loading any drivers.  It won't get an IP address.  Any idea if the adapter is supported?  Should I just install NDIS Wrapper?

Well, those are all the questions I can think of at the moment.  I appreciate any and all help.  This is my first foray into Ubuntu, but I like it so far!

     dice

---

### Post by tgm4883 on 2007-08-03
> **fkzdiceman said:**
> Hey All,

I have a MythTV backend/fronted system up and running, but I have a few questions.  First my specs:

P4 2 GHz
1GB RAM
80GB HD for OS
500GB HD for MythTV
Hauppauge PVR 150 with remote for capture
NVIDIA GForce 4 4600 for video output (S-Video)


1.  Display is very dark.  TV and DVDs look dark.  If it is a night scene you can't see anything!  Is there a setting to brighten things up a bit?

2. MythVideo works for some MPEGs and WMVs that I have, but it won't play my AVI files.  The AVIs are from a Canon Powershot.  I have tried the internal player, mplayer and xine but nothing has worked yet.

3. Video playback looks OK, but not great.  I used to have a DVR from my cable company and it looked just as good as watching cable.  With MythTV, live TV and recorded programs do not look that great.  Is this just the way MythTV is, or are there some tweaks I am missing?  Is it my hardware?  Should I install the proprietary drivers?

4. I have a Dell Wireless 1450 Wireless USB Adapter, but I can't get it to work.  It is recognized by Ubuntu, as what it is, but I don't think it is loading any drivers.  It won't get an IP address.  Any idea if the adapter is supported?  Should I just install NDIS Wrapper?

Well, those are all the questions I can think of at the moment.  I appreciate any and all help.  This is my first foray into Ubuntu, but I like it so far!

     dice

1.  How are you getting it to your TV?  Direct or though a VCR or whatnot?  Look for contrast settings on your TV.

2.  Have you tried VLC?  I believe you can set that as a player for those files

3.  Your probably set up incorrectly.  The default PVR-150 settings arent high enough IMO.  You can set that up in your recording profiles under settings in the front end.

4.  IDK

---

### Post by fkzdiceman on 2007-08-03
WOW!  Thanks for replying so quickly!


> 
1. How are you getting it to your TV? Direct or though a VCR or whatnot? Look for contrast settings on your TV.

2. Have you tried VLC? I believe you can set that as a player for those files

3. Your probably set up incorrectly. The default PVR-150 settings arent high enough IMO. You can set that up in your recording profiles under settings in the front end.

4. IDK


1. Direct coax cable.  Didn't even think about adjusting the brightness on the TV...DUH!

2. Don't know what it is but I'll look into it.

3. I'll look into that.  What about drivers for my output card?  Any idea about that?

4. I think that is going to be the painful part.  Anyone know a good wireless card for Ubuntu?

     dice

---

### Post by fkzdiceman on 2007-08-09
OK... I have an update.  

I started over from scratch since I needed a different gui to configure the usb wireless adapter.  Now I have everything set up and working.  Wireless, Remote, all the files types work.  Life was good....until I connected it to my TV.  Everything is fine and dandy until the MythTV splash screen is supposed to load.  All I get is a black screen.  I can SSH into the box and I see that mythfrontend is running but nothing is showing on the screen.  Please Help:confused::confused:


Thanks as always,

     -dice

---

### Post by napsilan on 2007-08-09
did you install the proprietary nvidia driver?  I have a feisty mythtv box as well and I needed the proprietary ATI driver to get TV-out to work for my x800xl.

---

### Post by fkzdiceman on 2007-08-09
I haven't installed proprietary drivers yet.  I forgot to mention that I do get output through S-Video.  I can hit ctrl-alt-F1 and log into the console.  Could it still be a driver problem?  I guess it wouldn't hurt to install the proprietary drivers anyway.

Thanks,

     -dice

---

### Post by fkzdiceman on 2007-08-10
thanks for the tip....that did the trick!  unfortunately when I rebooted MythTV frontend loaded, but the remote didn't work :(  come to find out the kernel had been updated since I compiled lirc.  recompiling fixed that up, so now I finally have everything working on my myth box!:guitar:

---

