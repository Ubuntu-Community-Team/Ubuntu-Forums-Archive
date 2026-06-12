---
title: "Mplayer plugin in Firefox won't display WMV"
date: 2006-11-15
forum: General Help
---

### Post by mring on 2006-11-15
I have installed the Mplayer plugin for Firefox, but when I open a site like CNN and look at a Windows Media file it shows the plugin and the text "playing mms://wmscnn.stream.aol....." but no video. I know there is some dumb thing I forgot to do, but I am pretty new to Ubuntu

---

### Post by jd65pl on 2006-11-15
Do you have the codec for wmv? did you get this functionality by using automatix?

---

### Post by mring on 2006-11-15
I used the synaptic package manager. I presumed (wrongly?) that it would have everything. Where would the codec files be located?

---

### Post by jd65pl on 2006-11-15
What did you install from synaptic exactly? If you need this functionality soon you should try using automatix.

See this link on installation of automatix: [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by jd65pl on 2006-11-15
To get just the w32codec. try:

```
sudo aptitude update
sudo aptitude install w32codecs
```

---

### Post by mring on 2006-11-15
Tried: sudo aptitude update
That worked
Tried: sudo aptitude install w32codecs
I got the message: No candidate version found for w32 codecs

Went on to automatrix, installed that installed the mplayer for firefox and codecs. Now when I open video in cnn I get error message: Cannot find codec matching selected -vo and video format. Then I get an error: Couldn't resolve name for....

When opening QT I get the second error, but it goes ahead and plays the clip.

Also, does it have to open a new player window to play?

---

### Post by phxcxh on 2006-11-15
I had a similar issue. Video's on dallascowboys.com wouldn't play; sound only. So I tried my old WinXP partition, same problem, only audio. Then upgraded windows media player to version 10 in XP-got video! guess I'll look into installing the player onto my Edgy partition.

---

### Post by mring on 2006-11-15
Okay downloaded and figured out a way to install newest mplayer codecs but I still get: "Couldn't resolve name for AF_INET6:...." Also, still opens a new window instead of playing in existing window. Is this the way it is supposed to be?

---

### Post by fragos on 2006-11-15
universe and multiverse repositories must be enabled.  IMHO the first place to look to install packages is Synaptic.  Synaptic is GUI and easy to use.  The Ubuntu recommended repositories are always best.  Not all deb packages work correctly with Ubuntu.

---

### Post by pissedoffdude on 2006-11-15
Do you have the codecs?  If not follow this link to install the proper codecs [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

