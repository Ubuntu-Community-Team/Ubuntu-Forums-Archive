---
title: "root access at boot"
date: 2007-08-16
forum: General Help
---

### Post by Glanwy on 2007-08-16
I have installed Ubuntu 5.1 and cannot get X to run, I am happy learning command prompt stuff and generally pottering around getting the hang of using Linux at command  level.
However to install any graphic drivers  (which it appears I am missing) I neet to be "root" but when I installed Ubuntu it gave me no opportunity to set up a superuser account.

Am I being dim and have missed something, I do not want to use su all the time as I know I wont get installations right first  (or tenth) time.

Any thoughts ???

---

### Post by Lord Illidan on 2007-08-16
> **Glanwy said:**
> I have installed Ubuntu 5.1 and cannot get X to run, I am happy learning command prompt stuff and generally pottering around getting the hang of using Linux at command  level.
However to install any graphic drivers  (which it appears I am missing) I neet to be "root" but when I installed Ubuntu it gave me no opportunity to set up a superuser account.

Am I being dim and have missed something, I do not want to use su all the time as I know I wont get installations right first  (or tenth) time.

Any thoughts ???

First off, Ubuntu 5.1 is very old now, and unsupported. You'd be much better off using Ubuntu 7.04 for example.

Furthermore, what's your graphics card?

You can access root, by booting as failsafe, there is an option in the GRUB menu at bootup.

However, in Ubuntu, we tend to use sudo, more than root. Simply precede a command with sudo.

Such as ```
sudo nano /etc/X11/xorg.conf
``` to open the xorg.conf file with root permissions.

Enjoy!

---

### Post by Glanwy on 2007-08-16
Thanks will try that later.
I have tried the su (not sudo) command but still wants the root password, my graphics card is an Nvidia GL 6000 + which is not listed when X tries to open.
When i try to tinker with the Xorg.0.log file I am told that it is write protected by root.
I am quite enjoying getting the hang of command line syntax etc, however, the PC is not connected to the internet and I know I will have enormous fun & games when I start configuring NIC cards and IP addresses etc, hence why I would like to be root to do this how do you get Grub to load as root?

---

