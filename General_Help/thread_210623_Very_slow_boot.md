---
title: "Very slow boot"
date: 2006-07-07
forum: General Help
---

### Post by punjabimunda on 2006-07-07
I have Ubuntu 6 with Windows XP Professional.

The problem is, Ubuntu takes around 10 minutes to load. It gets stuck on the second boot up: Mount root file systems.

Rest of the booting takes in a few seconds, but the second step takes around 10 minutes.

I have a Pentium 4 1.7 GHz with 256 MB RAM. The harddisk is a new one, so no problem with that.

Any help will be greatly appreciated but please don't use too geeky terms. I am just a kid and a newbie to Linux.

---

### Post by ajgreeny on 2006-07-07
I'm not quite sure what you mean by second boot up but if you mean the first boot after installing, then it may simply be updating through your network connection.  Try booting again, once Ubuntu is up and running, and if it seems to still take that long, it is worth doing the equivalent of scandisk in windows to check that your filesystem is OK.

Open the Gnome terminal in Gnome or Konsole in KDE and type:-
"sudo shutdown -r -F now"

This will restart your computer and it will do a filesystem check when it starts.  If it finds any problems it should repair them and then may tell you it has to restart again.  Let it do that and hopefully all will be OK.

I am assuming the machine has been doing this since you installed Ubuntu and hasn't just started playing up after an update or something you have done or changed.

---

### Post by punjabimunda on 2006-07-07
Thank you for your reply.

The first time I booted into Ubuntu after Install, it was ok. After that it messed up.

I will run the command and let you know. 

Thank you so much.

---

