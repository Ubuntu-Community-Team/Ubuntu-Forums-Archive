---
title: "XMMS lock-up's, can't shut down?"
date: 2005-06-03
forum: General Help
---

### Post by Caffeine on 2005-06-03
Alright, I'm still new to Ubuntu, so sorry beforehand if my information may be a bit lacking or extremely n00bish.

I listen to a lot of internet radio, and my friend who is quite experienced with Linux hooked me up with XMMS and StreamTuner to find the stations.  So, I started up StreamTuner, found a station, and tried to tune in;  XMMS started up, said it was connecting, then locked up stiffer than a corpse.  The only way I could get it off of my desktop was to log off.  So I tried to log off, and it locked that up, and I was forced into a hard reset.

After reset, I tried using XMMS for some MP3's, and it locked up just the same.

The only adjustments I have done to my system since putting in Ubuntu were the ones listed on UbuntuGuide, and one here to add sound to flash files.

Any help would be greatly appreciated.  Please be patient, I haven't used Linux since they sent it to you on 3 1/2" diskettes, and I'm having to re-teach myself these days.

---

### Post by _MiniMe_ on 2005-06-03
Sorry that I can't help you, but I have to write cause I got exactly the same problem. I didn't try it with internet-radio, but it always freezes when I try to start an MP3-File. There is no problem with listening to mp3s using rythmbox and totem-player. only with XMMs it doesn't work...

btw: I always could kill it with "killall xmms"...

---

### Post by jmboris on 2005-06-05
i think that the problem is that you have to select  in xmms preferences **esound** as output plugin....

hope it helps

---

### Post by mike998 on 2005-06-05
[QUOTE=jmboris]i think that the problem is that you have to select  in xmms preferences **esound** as output plugin....

hope it helps[/QUOTE]

And as bad as it sounds, keep the force quit applet somewhere on your taskbar... Just in case of rogue applications.

---

### Post by _MiniMe_ on 2005-06-29
[QUOTE=jmboris]i think that the problem is that you have to select  in xmms preferences **esound** as output plugin....

hope it helps[/QUOTE]

It helped. Thx!

I think the other way to get xmms to work is to disable the ESD. But I haven't tried it...

---

### Post by virgule on 2005-06-29
XMMS only play with OSS driver for me.
PowerMac 'screamer'.. standard beige G3 build-in 'sound card'

---

### Post by thoffland on 2005-06-29
[QUOTE=virgule]XMMS only play with OSS driver for me.
PowerMac 'screamer'.. standard beige G3 build-in 'sound card'[/QUOTE]


Same with me, I still havent found a fix for that and I still cannot hear system sounds. I keep searching around for a fix, but I havent found anything yet after trying 3 different HOWTO's.

---

