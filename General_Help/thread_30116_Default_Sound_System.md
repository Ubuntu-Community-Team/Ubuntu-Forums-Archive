---
title: "Default Sound System"
date: 2005-04-27
forum: General Help
---

### Post by Kimm on 2005-04-27
I was woundering if there is any way of changing the default sound system from ESD to Alsa or OSS? now I have to kill esd for most apps to work... but when I kill esd gaim notification sounds dont work and there is no sound from flash movies.

Can anyone help?

---

### Post by bored2k on 2005-04-27
Run gstreamer-properties [from a terminal window] .
[[IMG]http://img195.echo.cx/img195/3140/screenshotmultimediasystemssel.th.png[/IMG]](http://img195.echo.cx/my.php?image=screenshotmultimediasystemssel.png)

---

### Post by eric71 on 2005-04-27
Just had the same problem because I've disabled esd to more conveniently use Audacity and Skype.  I found the answer in this thread:

[http://ubuntuforums.org/showthread.php?t=21205](http://ubuntuforums.org/showthread.php?t=21205)

Now I've got sounds in Gaim despite not running esd.  You might want to enable software mixing with Alsa to get sounds from multiple apps at once.  There's good instructions in multiple threads about creating an etc/asound.conf file to do this.  Just search for "multiple sounds" or something like that.

---

