---
title: "Skype - &quot;problem with sound device&quot;"
date: 2006-11-03
forum: General Help
---

### Post by Fajer on 2006-11-03
Hi,
I had fully functional and working Sykpe on Dapper.
After upgrade to Edgy I had few problems with my soundcard, (SoundBlaster 5.1) but it works now properly.

Only one thing doesn't work still - Skype.](*,) 
When I want to call someone, ore someone is calling to me, I get the ringing tune in my speakers, and then I get the massage:
```
problem with sound device
```
I tried to run Skype from terminal. In the time, when this error massage is shown, I get on the terminal:
```
ALSA lib pcm_dmix.c:801:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
```

Any suggestions?
Pleas, help. Skype is for me my only phone :-?

---

### Post by TigerWolf on 2006-11-03
[http://ubuntuforums.org/showthread.php?t=205924&page=2](http://ubuntuforums.org/showthread.php?t=205924&page=2)

This might help.

---

### Post by revolver on 2006-11-04
This is big problem of open source community - all closed source programs are "almost" working on open source systems. This "almost" may spoil your Linux experience.

I use vmware with windows installed just for skype - normal sound and video are available on windows only.

---

### Post by Fajer on 2006-11-06
> **TigerWolf said:**
> [http://ubuntuforums.org/showthread.php?t=205924&page=2](http://ubuntuforums.org/showthread.php?t=205924&page=2)

This might help.
Thanks a lot :)
This topic helped me :)

I made:

```
 sudo mv /etc/asound.conf /etc/asound.conf.bak
 sudo /etc/init.d/alsa-utils restart
```

And It works :)
thanks!

---

### Post by jamaas on 2006-12-05
Thanks mate, worked for me too!  :-0
Jim
> **Fajer said:**
> Thanks a lot :)
This topic helped me :)

I made:

```
 sudo mv /etc/asound.conf /etc/asound.conf.bak
 sudo /etc/init.d/alsa-utils restart
```

And It works :)
thanks!

---

### Post by jnuneziglesias on 2006-12-19
> **jamaas said:**
> Thanks mate, worked for me too!  :-0
Jim
Works for me too! (though I didn't have an "asound.conf" file to move, the second command on its own worked!)

Thanks!!!

Juan.

---

