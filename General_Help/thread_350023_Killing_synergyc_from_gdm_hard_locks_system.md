---
title: "Killing synergyc from gdm hard locks system"
date: 2007-01-31
forum: General Help
---

### Post by nezroy on 2007-01-31
I have an interesting Synergy problem that I have been bashing my head against for a while now, and have run out of things to try at the moment.

I have a standard Edgy setup (ubuntu-desktop) that runs great. I have also installed the synergy package so I can share my mouse and keyboard from Windows. Synergy connects fine and everything works great, for the most part.

The issue I am having occurs when I try to setup synergyc to launch automatically for gdm. The launching part works ok (I can type in user/password, etc.), but when it gets to the line in /etc/gdm/PreSession/Default that tries to kill the running synergyc (running as root) so that the user's synergyc can start, it hard locks the host. I have to hit the power button to get it back. The same thing happens if I don't explicitly try to kill synergyc in one of the gdm scripts, since it manages to try and kill it anyway.

The really odd part of all this is that if I manually login to the host (either SSH or through another vterm) and kill synergyc (while gdm is running), it works fine! Synergy goes away fine and doesn't cause any problems at all. If I then login to gdm via my local keyboard (hooked up for testing), everything is happy. So something specifically about killing synergyc from within gdm's script handling process is causing the issue.

The only other unusual thing about my setup is that I am running a Xen kernel (2.6.17-6-generic-xen0), so this is all happening on dom0. Not sure if that's having any impact or not, but frankly the behavior is weird enough at this point that I have no clue what's up.

For what it's worth, I'm using the i810 driver in X (also tried with vesa, with and without framebuffer, all with the same outcome) on an intel d865perl mobo. Any ideas? I'm out of things I can think to try. I've used killall and pkill with various signals (including -9), tried forking the call (&), as well as different video drivers, all with the same result: killing synergyc from within gdm's scripts hard locks the box.

---

### Post by ograbah on 2007-04-08
I would suggest checking out the following thread, if you haven't already found your answer.

[http://ubuntuforums.org/showthread.php?t=48196](http://ubuntuforums.org/showthread.php?t=48196)

That thread walked me through the setup process and it worked.

Hope it works,
Jesse

---

