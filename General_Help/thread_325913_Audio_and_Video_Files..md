---
title: "Audio and Video Files."
date: 2006-12-26
forum: General Help
---

### Post by chrispche on 2006-12-26
Ok I installed automatix on Ubuntu 6.06. I choose AUD DVD Codecs,
Multimedia Codecs, and multimedia editing which included Audacity.
Audacity doesn't run it says there was an error initializing the audio
i/o layer.

I can't play DivX avi files and Mp3s. While trying to it says I need
the correct codecs. I have installed them. Is there something I'm
missing?

Please help, I don't want to go back to windows.

Cheers.

---

### Post by bruenig on 2006-12-26
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

Good guide there.

---

### Post by chrispche on 2006-12-26
Thanks, I'll see what I can do. Otherwise, I'm happy with Ubuntu.

---

### Post by chrispche on 2006-12-26
Ok I typed in:sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

And got: Password:
Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
chrispche@chrispche-desktop:~$

So w32codecs is something else now?

---

### Post by bruenig on 2006-12-26
First, you need to take the \'s out.
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```

Go here [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories) and follow the instructions for adding those repos, then run the command again. Also, I would also install totem-xine.
```
sudo apt-get install totem-xine
```

---

