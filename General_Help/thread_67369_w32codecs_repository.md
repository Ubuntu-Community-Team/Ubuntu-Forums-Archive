---
title: "w32codecs repository?"
date: 2005-09-20
forum: General Help
---

### Post by Richard Rowlands on 2005-09-20
Hi there,

Can somebody tell me the repository details / sources.list entries for the repository containing w32codecs.  I've searched the forums and each entry I have found and tried has failed when I start the package manager!

Thanks in advance, Richard.

---

### Post by SilentCacophony on 2005-09-20
Hello. As you may know, since those are non-free formats, they are not installed by default.

Usually, there is an unofficial starter guide to help with these things, but it seems to be down for the moment, so I'll point you to the wiki.

[Restricted Formats](https://wiki.ubuntu.com/RestrictedFormats) - here it outlines how to get the w32codecs and such.

[Software Management](https://wiki.ubuntu.com/SoftwareManagement) - here it outlines general software management.

Hope this helps!

---

### Post by bryan986 on 2005-09-21
its not in hoary-extras or hoary-backports

---

### Post by aysiu on 2005-09-21
I believe the w32codecs were just recently taken out for legal reasons (can someone confirm or deny this?).

Maybe [this](http://www1.apt-get.org/search.php?query=w32codecs&submit=&arch%5B%5D=i386&arch%5B%5D=all) will help? Generally you want to use Ubuntu repositories, but you may want to add this just for that one package.

---

### Post by Richard Rowlands on 2005-09-21
Hi folks,

Thanks for the help.  I've not had chance to try the link aysiu sent yet, but the URLs SilentCacophony posted have allowed me to enable mp3 playback despite missing the w32codecs.  Would be nice to have the w32codecs but I'm happy to have progressed a little further so thanks.

Best regards, Richard.

---

### Post by fordfan753 on 2005-09-22
[QUOTE=Richard Rowlands]Hi there,

Can somebody tell me the repository details / sources.list entries for the repository containing w32codecs.  I've searched the forums and each entry I have found and tried has failed when I start the package manager!

Thanks in advance, Richard.[/QUOTE]

You're looking for the Marillat Debian repositories.

debian.video.free.fr/ 

All the information about the repositories is on that site. Alternatively you can download the .deb from the repository manually (pool directory) and install it through dpkg. You may have to dpkg-reconfigure your movie players, eg dpkg-reconfigure totem

---

### Post by fordfan753 on 2005-09-22
[QUOTE=Richard Rowlands]Hi folks,

Thanks for the help.  I've not had chance to try the link aysiu sent yet, but the URLs SilentCacophony posted have allowed me to enable mp3 playback despite missing the w32codecs.  Would be nice to have the w32codecs but I'm happy to have progressed a little further so thanks.

Best regards, Richard.[/QUOTE]

mp3 playback is usually done through libmad0-dev and gstreamer0.8-dev, just make sure both of those are installed and mp3s *will* work fine on any player.

---

### Post by fordfan753 on 2005-09-22
[QUOTE=Richard Rowlands]Hi folks,

Thanks for the help.  I've not had chance to try the link aysiu sent yet, but the URLs SilentCacophony posted have allowed me to enable mp3 playback despite missing the w32codecs.  Would be nice to have the w32codecs but I'm happy to have progressed a little further so thanks.

Best regards, Richard.[/QUOTE]

mp3 playback is usually done through libmad0-dev and gstreamer-mad0.8-dev, just make sure both of those are installed and mp3s *will* work fine on any player.

---

### Post by Neodymion on 2007-09-25
> **fordfan753 said:**
> You're looking for the Marillat Debian repositories.

debian.video.free.fr/ 

All the information about the repositories is on that site. Alternatively you can download the .deb from the repository manually (pool directory) and install it through dpkg. You may have to dpkg-reconfigure your movie players, eg dpkg-reconfigure totem

I installed gstreamer-mad. I had to do dpkg-reconfigure too, then it worked fine.

---

### Post by danbh on 2007-09-25
medibuntu.sos-sts.com

take care

---

