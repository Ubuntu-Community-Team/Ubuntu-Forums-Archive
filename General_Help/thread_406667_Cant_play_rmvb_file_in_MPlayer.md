---
title: "Cant play rmvb file in MPlayer"
date: 2007-04-11
forum: General Help
---

### Post by Petester on 2007-04-11
I believe i downloaded Real Codec already and when i go to codecs & demuxer in the preferences, I selected the real codec.

But when I tried to open a rmvb file, it shows:

Error opening/Initializing the selected video_out (-vo) device


I have nVidia drivers installed via Envy..


any ideas? Thanks

---

### Post by hanzomon4 on 2007-05-04
Install totem-xine and then follow these instructions> **NeoChaosX said:**
> I'm having this problem, too. It started happening in Feisty; in Edgy, Real files played audio just fine in Kaffeine as well. It was exactly like one problem I had a year ago when I couldn't get WMVs to play sound despite having w32codecs installed; it turns out I had to tweak ~/.xine/catalog.cache to get it to play sound. Maybe playing with that file again will get it working, but I'm not so sure.

chggr: I'd prefer not to use VLC for a number of reasons, one of which there are some format it actually doesn't support (I have a few videos encoded in Indeo v4, which it doesn't support). So fixing xine to get this working would be preferable.

ETA: Found a solution. Open up ~/.xine/catalog.cache in a text editor and find this section:
```
[/usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so]
size=11300
mtime=1171041406
type=131
api=15
id=realadec
version=10104
supported_types=52494336 52559872 52756480 
decoder_priority=5
```
Bump up the 'decoder_priority' value to 10. That should get audio with Real files working.

First scratchy sound in SDL games, now this. And Canonical smoothed out all my audio problems with Edgy...

---

### Post by Egils on 2007-05-29
I don't know if this is still of interest Petester, but I sometimes got this message with Mplayer and it turned out that the problem was simply the choice of video driver within Mplayer. To change the driver you open Preferences, click on the Video tab and select a different (and hopefully compatible) driver from the "Available drivers" list. I don't know what the differences are between the different options but I have the nvidia display drivers installed as well and "gl2" ended up working fine for me.

---

### Post by mydrac on 2007-06-04
> **hanzomon4 said:**
> Install totem-xine and then follow these instructions

what other thing i can do because don't work to me.
 ](*,) :(

---

### Post by Casla on 2007-11-04
I found this tutorial real helpful and easy to follow.

[http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/#comment-77471](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/#comment-77471)

Hope it works for you too.

---

### Post by dingorunner on 2007-11-21
[http://www.simplehelp.net/2007/07/27...#comment-77471](http://www.simplehelp.net/2007/07/27...#comment-77471)
Follow those instructions changing the codec library (/usr/lib/win32) to /usr/lib/codecs.

This issue usually comes up after you update Mplayer, the new version has another codec library by default. and make sure you are working with essential-20071007.

---

### Post by quantboy on 2007-11-23
Following this Ubuntu's instructions on installing RealPlayer also works:[URL="https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods"]
https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods[/URL]

---

### Post by dingorunner on 2007-11-23
But is that a full version of Real Player?
I installed a free version of Real Player and It wasn't full featured, it didn't even have brightness control. 
I'd rather change some directories and fix MPlayer rather than installing Real Player if it is a  poor version of it.
What do you think?

---

### Post by Bablefish on 2007-11-23
Yes there is a full version of Real Player and you can get it through this command line

sudo apt-get install realplayer

I am not really a big fan of Mplayer I tried it once and frankly wasn't impressed, what I really found out was this only Real Player can play all Real Player files.

---

