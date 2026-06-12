---
title: "multimedia handicapped sound,graphics"
date: 2008-05-14
forum: General Help
---

### Post by sync_85 on 2008-05-14
hello i hvae just installed ubuntu 8.04
it wokred and looked absolutely fine after install.
my main intention was to configure mythtv.then i realized my graphics card all-in-wonder 9000 is not well supported.so i tried to install the ati driver and work around it.but finally all i have now is a screwed up screen with blur display.i have managed to uninstall the drivers from synaptic but still the display is quite horrible.
finally i have given up the idea of mythtv.but now i hav no idea how to get my display back :( :(
i also have a strange issue with sound.
i have one of those intel integrated sound card( soundmax digital audio in Windows and  
Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
	Subsystem: Compaq Computer Corporation Evo D500

as in ubuntu.

as u can see my computer is a Compaq small factor Evo D500 it has an internal speaker
the problem with the sound is,it plays on the internal speaker but it will not play on any headphone or speakers,which is so frustrating.
i really really want to use ubuntu 8.04 as my usual desktop rather than as a secondary to XP.
but all these is not getting me anywhere.
i'm not worried about tv anymore but if anyone can advise me what possibilly i can do with mainly sound and hopefully display would be really great.
thanks a lot

---

### Post by pedro_orange on 2008-05-14
> **sync_85 said:**
> hello i hvae just installed ubuntu 8.04
it wokred and looked absolutely fine after install.


Theres the simple answer.

---

### Post by sync_85 on 2008-05-14
it did cross my mind to reinstall the whole thing..but the sound was an issue from the begining...

---

### Post by pointone on 2008-05-14
Running:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

...should regenerate your xorg.conf file and fix the display issues. As far as sound, try going to **System > Preferences > Sound** and under **Default Mixer Tracks**, try changing the **Device** setting.

---

### Post by sync_85 on 2008-05-16
thank you very much
my graphics is better now....atleast i can play movies.
but the sound is really funny.i tried installing OSS driver whics brought sound on speakers but sounds that comes out is really funny.its sort of hight pitch on fast track.like george clooney sounds like a teenage singer of some boyband.
will try to get a fix,in the mea time any suggestion is welcome.

---

