---
title: "Sudden disaster, please help- not a hard drive crash, gnom extension killed something"
date: 2017-09-08
forum: General Help
---

### Post by david503 on 2017-09-08
So, I installed a Gnome extension "Switcher".  The first time I tried it, it sort-of worked for a minute and then froze gnome.  Still had mouse activity, nothing else.

So I rebooted the machine- checked to make sure there was no drive activity first. She reboots, and then starts asking me the initial install questions- keyboard, timezone, create a username, etc etc. Before I even get a login prompt. Why?  (16.04). 

Weird thing is, the desktop background is still the same as mine. So it's not like completely re-installing ubuntu or something.  I don't know what the hell...

So I go through the keyboard stuff and it just hangs. So I reboot again and during the stream it stops/hangs at this: 

[ OK ] Started Stop unreadahead data collection 45s after completed startup.

(and, no, I didn't mistranscribe "Started Stop" that's actually what it says.)

I can go into recovery mode and drop to root, and I can see all the files, so it's not some spontaneously coincidental drive crash. 

I tried this:  

sudo mv /etc/init/ureadahead.conf /etc/init/ureadahead.conf.disable

Which I found here: [http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04](http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04)

I was able to do it (again, all the files are still there, the drive seems to be fine), but it didn't change anything when I rebooted.

Please advise, computer is down.  

sq

Update: Now I can get one step after, to:

 "[ OK ] Reached target Network."  

So it hangs there instead.  And when I go to power off, when I soft press the power button, it reacts and throws messages before shutdown.  I gotta emphasize- none of the message in the stream are anything but green "OK"'s.  It's just not doing anything after Reached target Network.

---

