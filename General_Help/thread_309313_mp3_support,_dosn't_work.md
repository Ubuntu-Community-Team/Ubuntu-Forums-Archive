---
title: "mp3 support, dosn't work?"
date: 2006-11-29
forum: General Help
---

### Post by Hoborg on 2006-11-29
Yo guys ;)

I downloaded Juk so i could play my mp3 files, problem is that Juk dosn't play them! They are listed in the collection list, but when i want to play then nothing pappens. there are no problems regarding ogg files. 
Do i need to download some kind of mp3 plug in for the system or what?:confused:

---

### Post by newlinux on 2006-11-29
You need to download the right codecs. try the following:
```

sudo aptitude update
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll 
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
sudo aptitude install gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
sudo aptitude install libxine-extracodecs
wget http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
rm w32codecs_20060611-1plf1_i386.deb
```

Make sure you have the universe and multiverse repos enabled

---

### Post by xfred on 2006-12-29
I'm also experiencing problems with juk.  It seems has a nice look and feel, and seems to have the features I'm looking for, but for some reason it doesn't play.  I've installed all of the codecs you list (actually they were already installed when I checked) to no avail.

(I've tried other players - quod libet works, but appears not to have a random play option which I think is a must (well not that I could figure out, anyhow).  rhythmbox just plain dies when I try to import my 4000 or so mp3s.  totem is on the blink for no apparent reason, and I'm at my wits end ](*,) ).

---

### Post by Perfect Storm on 2006-12-29
Try this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by xfred on 2006-12-29
OK, thought I'd posted a solution here... but seems to have vanished.  Anyhow, it now works! :D

Solution was to install libarts1-mpeglib and libakode2-mpeg as per the kubuntu faq ([http://www.kubuntu.org/faq.php)](http://www.kubuntu.org/faq.php)).  Maybe this should be included in the ubuntu (not kubuntu) restricted formats section?

---

