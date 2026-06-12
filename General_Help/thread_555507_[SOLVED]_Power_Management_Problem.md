---
title: "[SOLVED] Power Management Problem"
date: 2007-09-20
forum: General Help
---

### Post by mel_phil@flashmail.com on 2007-09-20
Hi,

Please excuse my ignorance. I am currently running Fiesty Fawn 7.04 edition. The problem is I wish to set  up the power management like (And I don't mean to offend anybody in the Linux Community) windows "Always On" setting with no monitor & hard disk  turnoff/hibernation. My monitor turns off after 20 mins and I do not want this, the hard disk is always on (good). 

I have tried apt-get install acpid to get the latest edition, have run commands from a prompt to manually set it up, configured through the gui (Gnome & KDE) & have turned off power management stuff in the bios. I even tried 2 different monitors (one crt & 1 lcd) It happens if use either KDE or Gnome desktops. I believe it is something I am doing & not the machine as it happens when I install it on my Dell Poweredge 2400 & HP Netserver as well. The power management functions are there & say what I want them to say but it just don't work for me.

Please help & many thanks in advance for your patience

PS

---

### Post by cabinboy on 2007-09-20
In GNOME, go to System -> Preferences -> Power Management.  There should be a line saying "Put display to sleep when inactive for:".  Pull the slider to the right-hand end, until the text below says "Never".  Close.

This worked for me.  I made my laptop run on battery and the monitor never turned off during the 30-minute test.  It usually turns off after 15 minutes of idle.

---

### Post by mel_phil@flashmail.com on 2007-09-20
Hi,

Many thanks for taking the time to help me. I have already tried that with no success. I still think it is something I am doing not the hardware & OS

Many thanks

Phil

---

### Post by DaveRM on 2007-09-20
Phil,

I had a similar problem when in a XGL session.

See:
[http://ubuntuforums.org/showthread.php?t=341107&highlight=screensaver]("http://ubuntuforums.org/showthread.php?t=341107&highlight=screensaver")

Good Luck.

---

