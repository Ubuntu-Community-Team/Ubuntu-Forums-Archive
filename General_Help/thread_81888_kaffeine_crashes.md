---
title: "kaffeine crashes"
date: 2005-10-25
forum: General Help
---

### Post by tonysathre on 2005-10-25
any time i try to play a movie in kaffeine it crashes, any ideas what could be causing this, or a fix for it ..... thanks

---

### Post by Staesys on 2005-10-25
What engine are you using? Personally, I've had better luck using the xine engine instead of gstreamer.

---

### Post by tonysathre on 2005-10-25
gstreamer

i also tried playing some movies in xine and that also crashed

---

### Post by daller on 2005-10-26
What audio and video drivers are you using? (In xine-parametres)

---

### Post by RoByLy on 2006-02-04
I think the problem is with ffmpeg if you have the win32 codecs try uninstalling ffmpeg and try again. It worked for me now kaffeine works perfectly.But mplayer requires ffmpeg right? Too bad I gues...


//later...no it still doesn't work correctly..I actualy uninstalled all of gstreamer and than ffmpeg and it worked great for a while but after I reinstalled gstreamer and even though ffmpeg isn't there kaffeine crashes again.It must be a conflict somewhere between the xine engine and gstreamer or one of it's plugins or another codec it's driving me nutsi..:( ll try testing it again I am a big kaffeine fan
Following the codecs guide from the ubuntu guide installs something that breaks kaffeine

---

### Post by RoByLy on 2006-02-04
Me again.Reinstaled all the codecs changed audio options to alsa in xine parameters in kaffeine.Works without problems so far.Looks promising :P

---

### Post by tonysathre on 2006-03-03
["openwrt hardware list"]("http://wiki.openwrt.org/TableOfHardware#head-f38de925d05399c37be284625228fb82d75cc8ef")

---

