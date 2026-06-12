---
title: "Lost power during install - what do I do?"
date: 2006-07-22
forum: General Help
---

### Post by spamjim on 2006-07-22
I'm installing on a dual boot XP/ubuntu (5.10) PIII laptop.  The installer got as far as setting up the base and boot loader and then told me to eject the CD-ROM.  After a reboot it started installing packages.  Then I stupidly kicked the power supply and the laptop went black.

When I restarted it, Ubuntu gave a warning that the installation of packages was incomplete and that I could review or adjust this.  It only gave an 'ok' button.  I hit enter and the computer did some more things and then went to a prompt. 

I now get a prompt for user/password and it works for both root and the normal user accounts - but after login, all I get is the shell/prompt.  I can cd to other directories but there is no desktop/GUI.

What do I do now?  Should I uninstall (and how?)?  Can I resume installation somehow?  Am I missing a very simply command to start the desktop?  The install CD does not seem to be found now that GRUB is running as the boot manager.

Help!

(thanks)

---

### Post by Sef on 2006-07-22
try this: (It will upgrade you to Dapper.)

sudo apt-get update

sudo aptitude install ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade

Hopefully that will get your GUI up and running.

---

### Post by spamjim on 2006-07-22
Thanks - it seems to be churning away now on setup.

---

