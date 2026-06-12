---
title: "shut down and restart"
date: 2008-05-16
forum: General Help
---

### Post by goldstar1 on 2008-05-16
I have a problem with Hardy not restarting and/or quiting from the GUI.

There are some posts on this subject on laptops, mine is a desktop. but so far there seems to be no help on this issue.

In fact, none of the suspend, hibernate, shut down, restart work on my desktop from the GUI. Log out---well, I'm using an ATI driver and of course after 3 or so years, so far there's been no fix for this logout not working issue from any distro.(I'm never again purchasing ATI cards)

So... I'm open for suggestions...How do I fix this so I can restart and shut down my computer without first opening a console or using the GUI to start to shutdown/restart then hitting ctr+alt+backspace to finish the task?

Thank You for your patience from this Ubuntu newby.

---

### Post by macaholic on 2008-05-16
What version of the ATI drivers are you using?

---

### Post by goldstar1 on 2008-05-17
The lastest ati driver. It has always worked good, however; when 3d graphics are enabled, I cannot log out. The computer freezes. It has done this through many distros for a number of years. The 3d graphics that come with a ubuntu work ok but are slow on my 9600 Radeon 256mb card, so I use .the properiatary accelerated drivers.

---

### Post by russo.mic on 2008-05-17
> **goldstar1 said:**
> The lastest ati driver. It has always worked good, however; when 3d graphics are enabled, I cannot log out. The computer freezes. It has done this through many distros for a number of years. The 3d graphics that come with a ubuntu work ok but are slow on my 9600 Radeon 256mb card, so I use .the properiatary accelerated drivers.

2nd the motion.

Try this, just as a troubleshooting step,  go to a terminal and do a:

sudo killall atieventid

and see if it shuts down normally.  if it does, it's your 3d accel.

---

### Post by goldstar1 on 2008-05-17
No, still doesn't work.

Everything closes on the desktop,but it hangs on the wallpaper. by pressing ctl+alt+backspace, it will then continue to either shut down or restart depending on what button I pressed.

I can open a console and restart or shut down normally.

Think it might be the wallpaper?

---

