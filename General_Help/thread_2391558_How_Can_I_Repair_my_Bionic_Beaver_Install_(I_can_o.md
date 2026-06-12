---
title: "How Can I Repair my Bionic Beaver Install (I can only use Xubuntu)"
date: 2018-05-10
forum: General Help
---

### Post by cubdukat1968 on 2018-05-10
A few weeks ago, while I was still using 16.04 Xenial, I suffered a power loss during an update, and for a while I was unable to boot into Ubuntu. After following some instructions I found here on how to repair a broken update, I was able to get the system up and running again, and it seemed to be all right -  at least until I tried to upgrade to 18.04...

It took me three separate attempts to get it installed, and it involved uninstalling just about everything but Xubuntu in order to do it. EVentually, I reinstalled the other desktop environments (KDE and the original ubuntu-desktop), but now when I attempt to log into anything but Xubuntu, it acts like it's booting into the selected environment, then it brings me back to the LightDM login screen. Another symptom is that booting up is starting to take as long as another unnamed OS that I would dump in a heartbeat if I could...

I am really trying to avoid doing a clean install because it was a nightmare trying to get it on the laptop in the first place thanks to all the roadblocks a certain software monopoly has thrown into the works to prevent you from using Linux. Additionally, none of the USB sticks I have are recognized at boot. And more importantly, I have my system set up the way I like it..

I am currently typing this from my desktop, but what I need to know is how to generate the logs I would need to upload so that someone might help me diagnose the problem. The end result should be Gnome, KDE and XFCE co-existing (I also have openbox, Fluxbox and IceWM installed, but I'll deal with those when the rest of the system is stable again.)

Any help anyone could render would be most appreciated.

---

### Post by dino99 on 2018-05-10
Get the log from a tty console after trying to login as expected:>  journalctl -b > journal.txt

---

### Post by cubdukat1968 on 2018-05-11
Here goes...

Hopefully my attempts to log into GNOME and Plasma will show up...

[https://paste.ubuntu.com/p/ZGDTf8rdxZ/](https://paste.ubuntu.com/p/ZGDTf8rdxZ/)

---

