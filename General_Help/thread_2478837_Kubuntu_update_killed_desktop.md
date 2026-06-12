---
title: "Kubuntu update killed desktop"
date: 2022-09-06
forum: General Help
---

### Post by TechnoJunky on 2022-09-06
I have 4 Ubuntu computers, 1 server and 1 desktop on 20.04 and 2 desktops on 22.04.  The 1 desktop on 20.04 was off and that's the computer I'm using to post this thread.  I use Ansible to run apt-get updates to all 4 of these computers and keep them up to date all the time.  This morning I saw there was an update and told Ansible to update the computers.  During the update my computer crashed and rebooted.  After reboot I was at the command prompt asking for user name, not in the GUI.  I rebooted and same thing.  I logged in and tried running 'sudo init 5' but that just gave me a weird error 'mtd device must be supplied'.  I tried rebooting and selecting a previous kernel, but same result.  I tried the other 22.04 desktop and it had the same issue.  I can't log into the desktop of the server but can SSH to it and it seems fine, no reboot/crash.  I don't want to have to reinstall Linux on these computers if I don't have to, especially if this is going to happen again as soon as I update.  Any ideas?

---

### Post by TechnoJunky on 2022-09-06
Forgot to mention, these are Kubuntu computers

---

### Post by miguel001 on 2022-09-06
Can't you login from command prompt and undo the last updates installed? I'm not sure what the command for this is on Kubuntu. It might not have anything officially also in which case you may have to do some work. Its nice when there's an official means in a distro. Very handy at times like that.

At the very worst there is also a way to gain access to command prompt of an installed OS from installer usb which you might get confused on if you search but the info is available. No matter what you should be able to fix it without a clean install.

But, I'm not walking you through anything. Clean install if you can't do it.

Something like: [https://askubuntu.com/questions/34888/is-there-any-way-to-roll-back-the-most-recent-upgrade](https://askubuntu.com/questions/34888/is-there-any-way-to-roll-back-the-most-recent-upgrade) or [https://salsa.debian.org/PatH/apt-revert](https://salsa.debian.org/PatH/apt-revert)

---

### Post by oldfred on 2022-09-06
My 22.04 Kubuntu install just did a major update and I also lost gui.
Booted to recovery mode in grub, to add netword & get to terminal
Tried reinstall of sddm, but that only gave me mouse at gui.
I ended up with a total reinstall of kde.

This seemed to work but was a lot or apps. Better than full reinstall.
sudo apt reinstall kde-full

Finding now a few settings have reverted to defaults.

Adding Kubuntu to your title.

---

### Post by QIII on 2022-09-06
Same here.  Since I had a separate /home partition, I just reinstalled using the "with updates" option.  I have a list of the apps I have installed at any given time, so I was back up and running within 20 minutes.

Huge bug from the folks at KDE, for sure.  That, or the Kubuntu repos were not ready.

---

### Post by TechnoJunky on 2022-09-07
On one of the computers, my laptop, I just went and reinstalled Linux.  I tried doing the uninstall updates and reinstall removed but it didn't work.  Like QIII I have a separate partition for /home and I have a script I run after new installs to reinstall all my apps, so not a big deal.  I ran apt-get upgrade afterwards and everything is fine now.  I took oldfred's suggestion on the other computer and ran apt-get install kde-full and that worked.  So my wife's computer is back as well.  The login screen looks really weird but it's working and everything is basically back to normal.  Thanks everyone.

---

### Post by pslat-8 on 2023-02-17
> **QIII said:**
> Same here.  Since I had a separate /home partition, I just reinstalled using the "with updates" option.  I have a list of the apps I have installed at any given time, so I was back up and running within 20 minutes.

Huge bug from the folks at KDE, for sure.  That, or the Kubuntu repos were not ready.
Would you mind clarifying your comment re 'with updates' option please? Did you add this to a command line or was it an option while installing? I've tried three times to upgrade from 20-.04 and end up with an unuseable system as the login screen is a$$ways. If you used the command shell please share your commnand thanks.
Have been a fan of kubunu for a very long time but if I can't upgrade easily I'm looking at switching to another distro.

---

