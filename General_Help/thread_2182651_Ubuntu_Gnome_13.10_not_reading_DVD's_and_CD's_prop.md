---
title: "Ubuntu Gnome 13.10 not reading DVD's and CD's properly"
date: 2013-10-21
forum: General Help
---

### Post by jhilp on 2013-10-21
I installed Ubuntu Gnome 13.10 on my computer yesterday, and everything seems to be working fine so far, except that it isn't reading video or audio CD's and DVD's.  At first, I inserted a DVD video, and it played normally for maybe 30-45 seconds before coming up with a "internal read error" or something like that.  I was using the Totem player when the problem occurred, so I tried installing the VLC media player.  It wouldn't read the disc at all, so I uninstalled the player.  Now, the Totem player won't even begin playing the DVD.  The player sometimes doesn't even open up when I insert the DVD, and other times it will but says it can't read it.  I've tried several different DVD's and CD's with similar results.  The computer is recognizing the optical drive, because when I open "Files",  it shows the drive and the disc, but can't play it.  Previously, I ran Ubuntu 13.04 with the Gnome desktop installed from the software center, and I had no issues.  Any help is appreciated!

---

### Post by scouser73 on 2013-10-22
1 - Open Terminal

2 - Copy & Paste Command

```
sudo apt-get install ubuntu-restricted-extras
```

3 - Press Enter

4 - Enter Your Password

5 - Press Enter

Ubuntu Restricted Extras will now be installed, giving you the opportunity to watch DVD's.

---

### Post by jhilp on 2013-10-22
Thanks for the help, but that didn't work.  I installed the Ubuntu restricted extras and rebooted, but have the same problem.  Any other ideas?

---

### Post by QIII on 2013-10-22
One more step...

You need to install libdvdcss by running a script in one of the directories created when you installed restricted-extras:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by jhilp on 2013-10-22
Already did that too.

---

### Post by philipp-sadleder on 2013-12-05
There is a bug that describes the issue:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1245097](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1245097)

---

