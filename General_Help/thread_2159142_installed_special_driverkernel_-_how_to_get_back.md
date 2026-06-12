---
title: "installed special driver/kernel - how to get back"
date: 2013-07-02
forum: General Help
---

### Post by hako1 on 2013-07-02
Running 13.04 (32bit), I found the graphic performance not very good. Especially the launcher (Unity) is quite slow, and vlc cannot play movies without stuttering on my old RS480.
So, I looked around, and found a method to use ATI drivers [http://*********************.com/2012/09/28/to-do-list-after-installing-ubuntu-13-04-aka-raring-ringtail-operating-system/](http://*********************.com/2012/09/28/to-do-list-after-installing-ubuntu-13-04-aka-raring-ringtail-operating-system/)
Details:[INDENT]   Alternative ATI Legacy Video Driver PPA installation for (for < 5000   series cards):

      sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
      sudo add-apt-repository ppa:makson96/fglrx
      sudo apt-get update
      sudo apt-get upgrade
      sudo apt-get install linux-headers-generic fglrx-legacy
      sudo aticonfig --initial
      And then reboot.
 [/INDENT]
There were a couple of warnings at "sudo apt-get install linux-headers-generic fglrx-legacy" with update-alternatives.
  At the last step I got "aticonfig: No supported adapters detected".
Unity does not start anymore, but I can login to Gnome.

I un-installed the driver with sudo ppa-purge ppa:makson96/fglrx

Unity still does not start, the hp printer indicator quits at start-up (no system tray detected), and I can still only use the Gnome desktop.
 How can I get back to a working system with Unity?

---

### Post by hako1 on 2013-07-03
nobody can hint me to a solution? Do I need to re-install 13.04?  Or, because it is such a major issue, better 12.04?

---

### Post by Mark Phelps on 2013-07-03
Had you asked BEFORE you did this, some of us would have told you it was a BAD idea and advised against doing it -- for exactly the kinds of problems you are encountering.

Ubuntu 12.04.1 is the LAST Ubuntu version that will cleanly install the AMD restricted drivers for your PC.  You can use the card in 13.04, just NOT with the AMD restricted drivers.

Unless you really NEED the AMD restricted drivers for heavy duty gaming or GPU temp control, the best course of action would be to reinstall with Ubuntu 12.04.1.  You can get that version from the following link:  [http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

---

### Post by hako1 on 2013-07-03
Thank you, but it leaves me to ask 2 questions:

1. If I don't care for slow Unity and stuttering vlc, do I have to re-install 13.04? Or, is there an easier way by installing some packages that got purged?

2. If I install 12.04.1, do I have to install the special drivers afterwards? Or are they automatically installed?

Btw., 12.10 ran with non-optimal video performance on this PC, especially Unity, but it was still possible to watch videos.

---

### Post by hako1 on 2013-07-10
I found a solution [here]("http://askubuntu.com/questions/204428/unity-missing-cant-see-top-or-side-panels"):

1. Ran from a Gnome desktop terminal
   sudo apt-get purge fglrx lightdm && sudo apt-get install lightdm ubuntu-desktop
2. Enabled Unity via ccsm, and rebootet.
3. After login to Ubuntu desktop, running ccsm again to do the settings did the trick.

Now, acc to sytem settings, I have the driver "Gallium 0.4 on ATI RS480".
Unity is working again. Slow - but working.
:D

---

