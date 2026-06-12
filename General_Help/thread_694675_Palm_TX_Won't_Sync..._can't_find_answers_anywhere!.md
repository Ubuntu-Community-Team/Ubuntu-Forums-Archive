---
title: "Palm TX Won't Sync... can't find answers anywhere!"
date: 2008-02-12
forum: General Help
---

### Post by iThinkergoiMac on 2008-02-12
So I have a Palm TX and I can't get it to sync wirelessly or via the USB cable. I've looked at different threads on here and found no one with my specific error.

I'm running Gutsy (7.10) and trying to sync with the gpilot applet. My understanding is that I just need to add the applet to the menu bar and set up the Palm. It gets the user and ID from the Palm just fine, but when I try to sync with the cable I get an error: "Unknown PDA - no PDA matches ID -1038301850 Use gnomecc to configure gnome-pilot"

So I tried adding the exception of the wirelesscorlib (or something like that, I can't remember off the top of my head) to the backup-config file and doing it wirelessly. I actually tried the wireless before doing that as well... and using the wireless and USB after that too. I still get the exact same error.

My life is on my Palm, but right now I can only use it in Windows. Does anybody have any ideas? I'm pretty much lost here. Thanks!

---

### Post by Whiffle on 2008-02-12
[http://lists.ximian.com/pipermail/evolution/2002-February/017014.html](http://lists.ximian.com/pipermail/evolution/2002-February/017014.html)

There are some instructions toward the bottom that might be of some help.

> 
yeah thats the same problem of having 2 of them running...if you start
one manually and then run the control center, it will start of one its
own.  The control center has it use the gnome session stuff to prevent
it happening again or something.
usually I do this:
killall -9 gpilotd
gnomecc
#setup everything
ps auxw|grep gpilotd
#make sure only 1 is running

after that it stays working.

you might want to try removing these directories and starting again.
.gnome/gnome-pilot.d/
.gnome_private/gnome-pilot.d/



---

### Post by iThinkergoiMac on 2008-02-12
> **Whiffle said:**
> [http://lists.ximian.com/pipermail/evolution/2002-February/017014.html](http://lists.ximian.com/pipermail/evolution/2002-February/017014.html)

There are some instructions toward the bottom that might be of some help.

Well... I tried following the instructions... but when I tried to run gnomecc it said it couldn't find it. And Synaptic doesn't seem to find it either... what gives?

---

### Post by iThinkergoiMac on 2008-02-16
*bump*

Any ideas?

---

