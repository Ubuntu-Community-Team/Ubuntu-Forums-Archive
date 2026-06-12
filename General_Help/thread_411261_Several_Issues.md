---
title: "Several Issues"
date: 2007-04-16
forum: General Help
---

### Post by jimbo99 on 2007-04-16
Hi, thanks for taking the time to read this message.  I have several issues that I want to address in this post.

I'm a pretty long term user of Ubuntu and I have quite a bit of computer experience under my belt.  I run a small business and I do not have the time to pick through the intracies of the OS any longer so I do what I can and then resort to asking questions.

Over the past week I've had several people in the store wanting Linux (Ubuntu) or just wanting general help with Linux.  I'm glad to offer that time to them for free.  It is pleasant to see people understanding what Microsoft is doing with their DRM (and ultimate lock in--with tendencies toward using their current monopoly to gain another in DRM and CRM--not to mention they are very displeased about how Microsoft is spying on them and their computers).

I personally switched to Linux because it is very nice.  I have used it over the past 10 years on and off but this is my first total committment on my main computer to it.  I'm very pleased with how well it has served me, except maybe in the area of commercial gaming.  The standard apps have come a long way and I'm extremely happy with them, except for some issues that have recently cropped up as of late.  Here's a rundown.  See if you can find my solution.  It certainly will help me help others in the long run.

Gaim has caused me a lot of grief.  I recently began to chat with my sister in MN and she wanted to send me some photos so I told her to fire up her IM and begin transferring.  Throughout the transfer process (quite often) the transfers would just stop with a message saying that it was canceled.  Since neither of us had canceled it I decided  to move my sister over to Gaim 2.0 beta 6 under windows (Ubuntu installed Gaim 2.0 beta 3).  I figured if we had the same client we'd have the best experience.  She managed to download (being a newbie to the intricacies of computers) and installed it.  She then set up her accounts and we were off.  This time a greater problem cropped its head up.  As we transferred files often my client would just quit or crash.  We muddled through this for a while.  I decided then to stop the transfers and take some time to download and install the Beta 6 of version 2.0 of Gaim for Linux.  This gave us better results but still periodically I get crashes during transfers.  Though the crashes aren't as often they still exist.  But not only that since we are using standard protocols such as AIM, Yahoo, MSN, etc we should be able to transfer from various clients.  Anyone know if the Gaim people are really taking this product seriously?  Anyone have ideas on how to resolve the crashes?

Earlier today I was looking at my menu system and noticed some duplicate entries and after running alacarte I noticed that some of the menus were not visible.  I tried to enable some and disable others but NO changes were permitted.  Anyone have any ideas on why I can't turn on or off menu entries?

The third issue has to do with the "open with" feature of gnome.  I was attempting to open some .pdf files and when I double clicked on them some el cheapo document viewer program launched.  I then looked at trying to change it so that all .pdf files are opened by default using Acrobat Reader.  I had no luck.  I right clicked on a .PDF document and chose properties.  When I did this a list of applications were available for me to select to "open with" with a radio button indicating the one that was being used.  The only problem was that I couldn't change it to a new default.

I launched the nautilus using gksu and was able to alter this but apparently it only made the change effective for the root user.  This was also the case for the alacarte menu editor.  It took me loading alacarte with gksu before I was able to make the changes but they were only applicable to the root account--or they didn't stick after I closed the editor.

I also have various issues with my camera being recognized and with my camera's flash card being read.  Sometimes it does and sometimes it doesn't.

As these are every day issues it would be most appropriate to have someone in the Ubuntu development take some serious looks at how they implemented this stuff.  I'm sure I'm not the only one with these problems.

Oh, forgot to add that after updating to Gaim 2.0 Beta 6 the IRC plugin is missing.  Anyone know where I can get a working plugin for IRC for Gaim 2.0 beta 6?

Any help would be greatly appreciated.  If you need clarification on some of these just ask.

---

### Post by jimbo99 on 2007-04-17
These aren't insurmountable problems so I'm going to bump it back up.

Any ideas?

---

### Post by Brucevdk on 2007-04-18
I'll try and assist you with the Gaim/Pidgin problem, hopefully others will be able to offer more insight into the others. Since Gaim is known as Pidgin nowadays, I'll refer to it as Pidgin for the remainder of this post.

> **jimbo99 said:**
> 
[...] Throughout the transfer process (quite often) the transfers would just stop with a message saying that it was canceled.  Since neither of us had canceled it I decided  to move my sister over to Gaim 2.0 beta 6 under windows (Ubuntu installed Gaim 2.0 beta 3). [...] This time a greater problem cropped its head up.  As we transferred files often my client would just quit or crash.  We muddled through this for a while.  I decided then to stop the transfers and take some time to download and install the Beta 6 of version 2.0 of Gaim for Linux.  This gave us better results but still periodically I get crashes during transfers.  Though the crashes aren't as often they still exist.  [...] Anyone know if the Gaim people are really taking this product seriously?  Anyone have ideas on how to resolve the crashes?


First off, Pidgin developers take their work very seriously. Any bug report that involves an application crash is given the highest priority. However, if the problem is not immediately reproducible they need a lot more information concerning the crash (perhaps it is something specific to your machine that makes it crash). I searched the tracker and couldn't find any recent bug reports which involved crashing while transferring files (see all bug reports with the keyword crash in them at [sourceforge.net]("http://sourceforge.net/search/index.php?group_id=235&words=%28%2Bcrash+%2Btransfer%29+AND+ml_name%3A%28gaim-bugs+gaim-gtk-bugs%29&type_of_search=mlists&pmode=0&words=%28%2Bcrash%29+AND+ml_name%3A%28gaim-bugs+gaim-gtk-bugs%29&Search=Search") and [developer.pidgin.im]("http://developer.pidgin.im/search?q=crash&noquickjump=1&ticket=on")).

To get this information you'll have to use a debugger (GDB), [please  read this document from the Pidgin website]("http://www.pidgin.im/gdb.php"). As described in the linked document at the Ubuntu Wiki, you'll have to follow these steps:

```

gdb /usr/bin/gaim 2>&1 | tee gdb-gaim.txt
(gdb) handle SIG33 pass nostop noprint
(gdb) set pagination 0
(gdb) run

```

After it crashes, execute the following commands:

```

(gdb) backtrace
(gdb) info registers
(gdb) thread apply all backtrace
(gdb) quit

```

Though you could attach the file generated (gdb-gaim.txt) to your post I'm not sure if I could be of much assistance. You should probably create a bug report at the Pidgin website, [read the following document for a how to]("http://developer.pidgin.im/wiki/TipsForBugReports").

> **jimbo99 said:**
> 
Oh, forgot to add that after updating to Gaim 2.0 Beta 6 the IRC plugin is missing.  Anyone know where I can get a working plugin for IRC for Gaim 2.0 beta 6?


What plugin are we talking about here? [IRC Helper]("http://plugins.guifications.org/trac/wiki/irchelper") perhaps?

---

