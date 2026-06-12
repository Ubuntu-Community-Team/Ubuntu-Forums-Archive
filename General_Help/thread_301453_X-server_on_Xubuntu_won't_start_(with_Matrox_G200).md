---
title: "X-server on Xubuntu won't start (with Matrox G200)"
date: 2006-11-17
forum: General Help
---

### Post by dede on 2006-11-17
Hi all,

i'm a new Xubuntu user.

I've try to install the xubuntu alternate version on a pc and all the installation goes ok.

When i had rebooted the pc first time, it's appear me the log in window, and after 10 seconds some messages with some of this lines:

(EE)MGA(0) :no valid modes found
(EE)screen(s) found, but none have a usable configuration


No screen found
---------------------

I've try to reinstall teh OS but without any results.

Always, when i switch on the pc, appear me the blue window with the xserver information.

Please, i try to use Xubuntu from two weeks....

I've visited various sites, but none have a solution....:( 

Thanks in advance to all!

---

### Post by gareththegeek on 2006-11-17
Can you get to a command prompt?
Does Ctrl+Alt+F1 get you there?

---

### Post by dede on 2006-11-17
yes, i can also run the os in safe mode with the prompt

---

### Post by gareththegeek on 2006-11-17
I'm a bit of a newbie myself, hopefully someone more knowledgeable (nudge) can help you more but..

what's in the xorg.conf and xorg.log?
pico /etc/X11/xorg.conf  <-- configuration of x-windows
pico /var/log/Xorg.0.log  <-- look for error messages in the log..


You could try running through 	
sudo dpkg-reconfigure xserver-xorg
which asks you some questions and lets you configure x

HTH
G!

---

### Post by dede on 2006-11-17
i've just try to make this command (dpkg-reconfigure xserver-xorg) in safe mode.

I've try to make some combinations without any results.

---

### Post by gareththegeek on 2006-11-17
There seems to be a lot of good info over at the matrox forums,
[http://forum.matrox.com]("http://forum.matrox.com")

for example this post shows how to configure a G200 with Edgy I think:
[http://forum.matrox.com/mga/viewtopic.php?t=22451&highlight=mga++valid+modes]("http://forum.matrox.com/mga/viewtopic.php?t=22451&highlight=mga++valid+modes")

HTH
G!

---

### Post by dede on 2006-11-28
i've try to follow the second example, but i don't know i can install the driver in text mode...i'm new and i don't know the commands...

---

### Post by gareththegeek on 2006-11-30
What Xubuntu version are you on?

Can you post the contents of
/etc/X11/xorg.conf
/var/log/Xorg.0.log

at all?

---

