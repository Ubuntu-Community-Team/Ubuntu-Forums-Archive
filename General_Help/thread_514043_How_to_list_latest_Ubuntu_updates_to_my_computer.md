---
title: "How to list latest Ubuntu updates to my computer"
date: 2007-07-31
forum: General Help
---

### Post by weedwacker on 2007-07-31
How can I get a list of latest updates to my computer.  I just gave the OK for Update Manager to install the latest updates and after a reboot I noticed that my BIOS screen had white dots regularly spaced like a grid covering the screen.  Then my Ubuntu loading screen which is normally black with the Ubuntu logo and progress bar is covered with a beaded look (many colored dots) that looks textured like a tapestry or needlework.  In addition my mouse pointer on the screen now has a couple of lines of dots just below the pointer.  Most irritating.

I want to uninstall the updated because I think this is what caused to screen problem.

How do I list these latest updates so that I can uninstall?

Any help would be appreciated.  Oh, I have a Radeon ATI card.  No problems before the install.

---

### Post by mcduck on 2007-07-31
If you get artifacts on screen even in BIOS, before Ubuntu is loaded, it really can't be because of the updates.

Sounds more like a hardware problem, perhaps your graphics card is overheating?. Check that al fans in your case are clean and working..

---

### Post by IcemanV9 on 2007-07-31
There are two (2) logs in /var/log that you can check.

     1) dpkg.log
     2) aptitude

---

### Post by weedwacker on 2007-07-31
Thanks to both of you for your quick responses.  Aptitude was something new for me.  Want to study that some more.  Don't really know what I am looking at in the logs, so... will save for later.

Have not installed or uninstalled  anything yet, but did take a look into the possibility of heat and the graphics card.

Fans are all spinning nicely.  Vacuumed out the whole case and vacuumed all the intake grills.  Did see some dustball (?) bouncing around on top of my graphics card when I removed the case cover.  That's the reason for vacuuming the interior of the case.

Restarted the computer and all seems fine for now.  Will continue to monitor.

Oh, the graphics card was generating heat.  Hmmm? I thought it had a fan, but didn't see it.  Will investigate if that model card does or does not have one.  It's a Powercolor XF98-C3l Radeon 9800PRO 128 MB DDR AGP 4X/8X video card.

Thanks again for the tips. :)

---

### Post by weedwacker on 2007-08-05
It was the fan on the graphics card!  Frozen up completely.  Could make it move a bit with some finger pressure.

Replaced fan with a Zalman VF700 CU VGA Cooler fan and all is well again! :popcorn:

---

