---
title: "Getting sound to work for Cedega/Point2Play"
date: 2005-04-07
forum: General Help
---

### Post by humps_buatbu on 2005-04-07
Hi everybody,

I just wanted to know what I need to do to allow Point2Play/Cedega to access the sound card. Right now when I run the test program it tells me:

Unable to complete sound test:
aplay: main:507: audio open error: Device or resource busy

I haven't tried running any games to see if sound would work regardless, because I'm pretty sure if Point2Play can't do it then neither can Cedega. It works automatically on Mandrakelinux but I hated that distro......

Anyways, any advice would be much appreciated.

---

### Post by Nis on 2005-04-07
[QUOTE=humps_buatbu]Hi everybody,

I just wanted to know what I need to do to allow Point2Play/Cedega to access the sound card. Right now when I run the test program it tells me:

Unable to complete sound test:
aplay: main:507: audio open error: Device or resource busy

I haven't tried running any games to see if sound would work regardless, because I'm pretty sure if Point2Play can't do it then neither can Cedega. It works automatically on Mandrakelinux but I hated that distro......

Anyways, any advice would be much appreciated.[/QUOTE]
 Try killing esd before starting P2P:
```

killall esd

```

---

### Post by humps_buatbu on 2005-04-07
Yeah, that worked all right!  Sound in all it's glory for both OSS and ALSA.  Now how do I set it so that esd doesn't always have control of the sound card?  Is there something I have to edit?

---

### Post by Nis on 2005-04-07
[QUOTE=humps_buatbu]Yeah, that worked all right!  Sound in all it's glory for both OSS and ALSA.  Now how do I set it so that esd doesn't always have control of the sound card?  Is there something I have to edit?[/QUOTE]
 If your soundcard does hardware mixing you can turn off esd in 'System/Preferences/Sound'.  Untick 'Enable sound server startup' and esd won't startup.  This will stop any system sounds from happening though, like the startup and logout sounds as well as some GNOME game sounds.  If your soundcard doesn't do hardware mixing stopping esd from running all the time isn't a very good idea.  You need it to have a song playing and hear any other sounds you might want, such as from GAIM.  If esd is not running these sounds will backup into a  queue so when your music stops you'll hear a series of old sounds from applications.  You could always try a wrapper script around Point2Play such as below:
```

#!/bin/sh
killall esd
Point2Play
/usr/bin/esd --nobeeps

```
Just save the above as something like myPoint2Play, make it executable, and try running.  Not sure if it will work but it might give you a springboard.

---

### Post by shupacanucks on 2005-04-14
in the Multimedia systems selector change the output to alsa...and disable the sound server...Cedega and mp3s will work but no system sound.

---

### Post by pirast on 2005-04-15
Is it possible to have system sound and games with sound?

In warty it worked  :mad: 

Martin

---

### Post by artinla on 2005-04-15
As a sidenote, I was having the same trouble with nvidia onboard sound.  Nothing that I did except to turn off esd would help.  I switched to a SBLive! and esd works fine with all my games.  (I don't have to turn it off or disable it).   My system sounds are working as well as all my games except MOH is a little strange.  

P2P and Cedega are great, and HL2 is really better than I expected under GNU/Linux.

Art

---

### Post by pirast on 2005-04-16
[QUOTE=artinla]As a sidenote, I was having the same trouble with nvidia onboard sound.  Nothing that I did except to turn off esd would help.  I switched to a SBLive! and esd works fine with all my games.  (I don't have to turn it off or disable it).   My system sounds are working as well as all my games except MOH is a little strange.  

P2P and Cedega are great, and HL2 is really better than I expected under GNU/Linux.

Art[/QUOTE]
 What about changing the sound system to OSS or ALSA?

Would this help and how to do it?

Martin
PS: I have a nvidia soundcard too. But I really don't want to change my soundcard because I think the sound is OK.

---

### Post by artinla on 2005-04-16
I tried both, but like I said.. Nothing worked except to change to the sblive.  An audigy  or audigy2 also works just fine.

Sorry I don't have a fix for you.

Art

---

### Post by pirast on 2005-04-16
Hi,
the weird thing is that I changed my sound system in warty to esd and I was able to play games with cedega and hear system sounds...

Now I upgraded to hoary and it doesn't work.

Martin

---

### Post by pirast on 2005-08-06
I bought an Audigy 2 ZS. 

After this I found out that 

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

helps too  :grin: 

Martin

---

