---
title: "Trouble installing transcode"
date: 2005-04-10
forum: General Help
---

### Post by gflores on 2005-04-10
I can't seem to install transcode. I've uncommented the lines and I've added marillat and backports and rarewares. I think it was initially installed by the Automate Script, but I was having problems with it. I tried to install DVD:Rip but it said it needed transcode and that it would not install it. 
So, I decided to uninstall transcode and then reinstall it again. It uninstalled fine. Now when I try to install transcode, it says, 
that it depends on libdvdread2 and libvorbis0 (>=1.0rc3-1) but it is not installable. I checked in my installed software, and I have libdvdread3 and libvorbis installed. Any idea what's wrong?

---

### Post by Nis on 2005-04-10
Mixing in repositories compiled for different releases (namely Debian Sid) usually causes trouble.  I would guess that your versions of libdvdread2 and libvorbis0 are conflicting with what transcode wants.  You can try selecting "Force version" from the package menu in Synaptic for libdvdread2 and libvorbis0 to see if you can get them to the version transcode requires.  Next time I would suggest not using marillat at all since most of the stuff there can replace things in Hoary that it shouldn't unless you do proper pinning in /etc/apt/preferences.

---

### Post by gflores on 2005-04-11
I see, I'm going to try to fiddle around with it later.

I also found this, which seems to be my problem.
[http://www.linuxquestions.org/questions/history/296324](http://www.linuxquestions.org/questions/history/296324)

---

