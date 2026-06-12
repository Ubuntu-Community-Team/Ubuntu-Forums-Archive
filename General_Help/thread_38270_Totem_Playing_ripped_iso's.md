---
title: "Totem: Playing ripped iso's"
date: 2005-05-30
forum: General Help
---

### Post by flanker on 2005-05-30
Can Totem be configured to play an iso of a DVD? i.e open Totem, browse to the iso and open it to start playing.

I've tried mounting an iso but it only allows you to browse the cd and play one of the vob's rather than play the whole film.

sudo mount -t iso9660 -o loop,ro movie.iso /media/iso

If this cant be done how should I store my movies for playback on the pc?

cheers, Ian.

---

### Post by smoon on 2005-05-30
I don't think Totem is able to play DVD(/(S)VCD/whatever)-Images at all. MPlayer and vlc do work fine though.

Another way would be to rip your DVDs and encode them to Mpeg4 or something similar. This can be achieved with tools like [Thoggen](http://thoggen.net/), a very simple and easy to use Gnome-application (not the fastest at encoding because it's using gstreamer for that) or [dvd::rip](http://www.exit1.org/dvdrip/) which may be available through the marillat repository. [Here are some more](http://freshmeat.net/search/?q=dvd+rip&section=projects&Go.x=0&Go.y=0).

---

### Post by Marquis_de_Carabas on 2005-05-30
[QUOTE=flanker]Can Totem be configured to play an iso of a DVD? i.e open Totem, browse to the iso and open it to start playing.

I've tried mounting an iso but it only allows you to browse the cd and play one of the vob's rather than play the whole film.

sudo mount -t iso9660 -o loop,ro movie.iso /media/iso

If this cant be done how should I store my movies for playback on the pc?

cheers, Ian.[/QUOTE]

Came across the following code snippet [here](http://forum.doom9.org/showthread.php?s=&postid=628814):

```
# mkdir /mnt/dvd_image 
creates the mountpoint directory

# mount -o loop -t udf /path/to/image.iso /mnt/dvd_image 
mounts the ISO image /path/to/image.iso on the /mnt/dvd_image directory

$ mplayer dvd://1 -dvd-device /mnt/dvd_image 
Plays the mounted image with mplayer

$ vlc --dvd /mnt/dvd_image
Plays the mounted image with VLC
```

I'm not sure how one would do the same in Totem, I just use Mplayer myself, but hopefully that gives you somewhere to start. Or you could just install Mplayer.

---

### Post by flanker on 2005-05-31
I was a bit reluctant to install another movie player as everything seems to be going the gstreamer route but I tried VLC.

VLC played the iso without mounting it and the picture quality was so much smoother than totem.

Storing dvd's in iso form makes burning back to disc that much easier.

Has anyone one else noticed the picture quality difference?

thanks guys.

---

### Post by logan2004 on 2005-05-31
ya VLC is greaaaaat

---

### Post by mommebu on 2007-11-21
While in earlier versions of ubuntu totem-xine was able to play iso files it seems to fail now if you load the image from the menu, however from terminal it worked for me using:
totem-xine dvd://absolute/path/to/your/iso/file.iso &
This is without mounting the image.

Strange that the newer version lost the feature from the menu though...

---

