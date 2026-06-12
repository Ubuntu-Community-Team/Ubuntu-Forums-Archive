---
title: "[SOLVED] Error messages following gksudo gedit and print"
date: 2007-12-18
forum: General Help
---

### Post by bw44 on 2007-12-18
If I $gksudo gedit and then edit a file and print it, I get a whole string of messages in the terminal window.  Here is a sample: ```
Model not found, discarding config

(gedit:6336): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterSelect': filter 'GnomePrintFilterSelect' is unknown

(gedit:6336): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:6336): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:6336): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterClip [ GnomePrintFilterMultipage ]': filter 'GnomePrintFilterClip' is unknown

(gedit:6336): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gedit:6336): libgnomeprintui-CRITICAL **: gnome_print_layout_selector_load_filter: assertion `GNOME_IS_PRINT_FILTER (f)' failed
```

I always worry when I see messages with CRITICAL in them.

Any suggestions as to why these messages are appearing and what to do about them (if anything)?

 I should add that the print job works, and for all I know the same messages may be present but invisible when I launch gedit from the desktop.

Thanks.

---

### Post by bw44 on 2007-12-19
bump

---

### Post by p_quarles on 2007-12-19
If the print job is working, and Gnome doesn't crash, then I'd say the message is a false alarm. 

If you want to get to the bottom of it, though, I'd begin by comparing this output to the terminal output of other programs when they attempt to print. First, gedit as your user. Then, another Gnome app which you can use to print something (like AbiWord or GIMP), then a non-Gnome app (Firefox or OpenOffice.org Writer). 

Basically, if you only get this error with gksudo gedit, then it's a probably with running Gedit as root. If you get it with Gedit as your user, and nowhere else, it's a problem with Gedit. If you get it in all Gnome apps, then it's a problem with Gnome. If you get it with all applications, it could be a number of things: dbus, Xorg, the printer driver, GDM, etc. 

Doing that might at least help narrow it down.

---

### Post by bw44 on 2007-12-19
> **p_quarles said:**
> If the print job is working, and Gnome doesn't crash, then I'd say the message is a false alarm. 

If you want to get to the bottom of it, though, I'd begin by comparing this output to the terminal output of other programs when they attempt to print. First, gedit as your user. Then, another Gnome app which you can use to print something (like AbiWord or GIMP), then a non-Gnome app (Firefox or OpenOffice.org Writer). 

Basically, if you only get this error with gksudo gedit, then it's a probably with running Gedit as root. If you get it with Gedit as your user, and nowhere else, it's a problem with Gedit. If you get it in all Gnome apps, then it's a problem with Gnome. If you get it with all applications, it could be a number of things: dbus, Xorg, the printer driver, GDM, etc. 

Doing that might at least help narrow it down.

Thanks a lot for this suggestion. (It's pretty basic problem resolution stuff, but I needed to be reminded!

I'll report back if/when I run it to earth.

Cheers.

---

### Post by bw44 on 2007-12-21
The problem only occurs with gedit, and I only see it when I run from the command line, whether with gksudo or without it.  OpenOffice ($ooffice -writer filename) can print without getting the errors.

I posted a report to Launchpad ([https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/20357](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/20357)) where I saw a bug report that showed the same error messages.  That report said the WARNING messages could be ignored, but I'd like to know why there are any error messages and if the CRITICAL ones can be ignored too!

Anyone have more thoughts on this?

---

### Post by p_quarles on 2007-12-21
My main thought is that the critical error message is a false alarm. Like I said before, if it prints okay and does not cause your hard drive to burst into flames, it can't really be all that critical. Of course, if you begin to notice other problems after getting this error (e.g., memory leaks, system sluggishness, missing icons in programs), then maybe there is a problem. 

There are a bunch of  these kinds of false alarms in any system. For instance, you've probably noticed that the gksudo program itself will frequently spit back an error message. Another example: ever since upgrading to 64-bit Ubuntu, my GRUB screen is immediately followed by a critical "Out of memory" message. This lasts for about a second and a a half, and then everything boots up normally (and very quickly), and I have no other issues with the installation. 

My read of the situation is that these are low-priority bugs, because a) they don't impact the actual working of the system, and b) they are the result of fairly low-level system operation, and fixing them would mean wading through massive amounts of code that is likely very cluttered. In this case, it's Gnome libraries that are the source of the problem, and I'm guessing those libraries contain enough patchwork to make them very difficult to analyze quickly.

Finally, Linux is just a bit more verbose by default than the major proprietary operating systems. I'm willing to bet that the verbose output in any recent version of Windows or OS X would yield a similar number of false alarms, it's just that the average user will never see it. One example of such an error, though, is Windows' "Error: No Error" message. ;)

---

### Post by bw44 on 2007-12-21
> **p_quarles said:**
> My main thought is that the critical error message is a false alarm. Like I said before, if it prints okay and does not cause your hard drive to burst into flames, it can't really be all that critical. Of course, if you begin to notice other problems after getting this error (e.g., memory leaks, system sluggishness, missing icons in programs), then maybe there is a problem. 

<snip> (please read original in p_quarles's post

My read of the situation is that these are low-priority bugs, because a) they don't impact the actual working of the system, and b) they are the result of fairly low-level system operation, and fixing them would mean wading through massive amounts of code that is likely very cluttered. In this case, it's Gnome libraries that are the source of the problem, and I'm guessing those libraries contain enough patchwork to make them very difficult to analyze quickly.

<snip>All of your thoughts are wise (I just snipped some to keep this post shorter).

I'm a relative noob to Linux but I'm already beginning to realize what you say is true. If things work, don't sweat it!  Coming from the Windows world, I've learned that when you actually see  a message that says "critical" then it often is (yes, MS hides a lot of the same stuff that you can see go by in Linux).

Resolved: don't report problems that aren't really problems; save posts for either something that just doesn't work, or something I can't figure out how to do.

Thanks.  (Will mark this thread SOLVED)

---

### Post by p_quarles on 2007-12-21
> **bw44 said:**
> Resolved: don't report problems that aren't really problems; save posts for either something that just doesn't work, or something I can't figure out how to do.
Just for the record, I certainly didn't mean to imply that you shouldn't have reported the bug on Launchpad -- even if it's a low-priority bug, it's still a bug, and it's helpful for the developers to know about it.

---

### Post by bw44 on 2007-12-21
> **p_quarles said:**
> Just for the record, I certainly didn't mean to imply that you shouldn't have reported the bug on Launchpad -- even if it's a low-priority bug, it's still a bug, and it's helpful for the developers to know about it. I wasn't even  thinking of my Launchpad report --  just about the number of posts on the Ubuntu forms.  I'm not sure now whether I would have reported it on Launchpad or not, based on your observations.  But I guess you're right-- it doesn't hurt to let developers know that things should be looked at; they might be related to a more serious problem.)

Cheers.

---

