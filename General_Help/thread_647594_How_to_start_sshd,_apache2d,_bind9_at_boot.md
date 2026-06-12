---
title: "How to start sshd, apache2d, bind9 at boot"
date: 2007-12-22
forum: General Help
---

### Post by gs48 on 2007-12-22
Sorry if this has been answered elsewhere, but after looking didn't find quite enough info to solve it.

Installed ssh server, apache2, and bind9  packages on Ubuntu 7.10 workstation build.  Both do not respond to remote connections after reboot, but DO respond after first local log on.  Saw startup scripts in the /etc/rc6.d and /etc/rc3.d directories, so thought they would both be available after boot.

Can someone please explain how to get them to respond after boot without local logon first?

Thank you!

---

### Post by p_quarles on 2007-12-22
How did you install these packages? If you got them from the repositories, they should have installed startup scripts in /etc/init.d, and will start without your needing to do anything. If you compiled them yourself, it's a different story.

---

### Post by gs48 on 2007-12-22
thx for the response.  Installed all packages from repositories, i.e. sudo apt-get install apache2

after some simple troubleshooting steps that I overlooked (ping!), I can see that the wireless network interface does not come up after reboot, until first local logon.  Is there a session setting or something that will bring up the interface at boot, before logon?

Thank you

---

### Post by p_quarles on 2007-12-22
Wireless can be a bit more complicated. Basically, you'll need to use iwconfig to connect to the access point on startup. Most likely, you'll need to write a script for it, including the essid and any keys that you use. It's not something I've done before, so beyond pointing you to the man page, I can't give you a lot of advice on this one.

---

### Post by gs48 on 2007-12-22
k, thx for the assist.  Will have look at the man pages

---

