---
title: "[SOLVED] I want to kill updatedb"
date: 2008-03-27
forum: General Help
---

### Post by natirips on 2008-03-27
How do I completely disable updatedb, and more important, will it affect my system if I do so?

It's VERY annoying, it behaves like some spyware, starts scanning the disk like crazy and eats-up the CPU, thus increasing the computer's temperature, it's almost like a virus...:-|

---

### Post by LeoSolaris on 2008-03-27
> **natirips said:**
> How do I completely disable updatedb, and more important, will it affect my system if I do so?

It's VERY annoying, it behaves like some spyware, starts scanning the disk like crazy and eats-up the CPU, thus increasing the computer's temperature, it's almost like a virus...:-|


Question...   what version of Ubuntu are you running? I have Gutsy desktop, and I have not found a process named updatedb, and I have added quite a few things to my system. I have an update-notifier that I can remove through Menu->System->Preference->Sessions It's on the first tab, Startup programs... But I get the feeling this is not what your hunting for. (If it is... cool, it shouldn't do anything to the system to disable it, as I have turned it off and on occasionally for various reasons.)

---

### Post by natirips on 2008-03-27
> **LeoSolaris said:**
> Question...   what version of Ubuntu are you running? I have Gutsy desktop, and I have not found a process named updatedb, and I have added quite a few things to my system. I have an update-notifier that I can remove through Menu->System->Preference->Sessions It's on the first tab, Startup programs... But I get the feeling this is not what your hunting for. (If it is... cool, it shouldn't do anything to the system to disable it, as I have turned it off and on occasionally for various reasons.)
It's Ubuntu 7.10 Gutsy Gibbon. That updatedb is ran by cron, and is supposed to update some file table for "locate" command, which is supposed to run faster than "find" or something blah blah blah... the thing is that I NEVER use that "locate" command manualy, but I'm not sure if the system uses it...

Updatebd is "supposed" to be a normal part of almost any linux, yet I see no purpose for it to exist, it only allows to search for files faster, but there IS the file system usually on your computer (on my computer it is an ext3 - you'd never have guessed)

---

### Post by MartinJ on 2008-03-27
The locate command is great!  KDE's locate:/ protocol is built on top of it, which is used in file browsers and open/save windows.  Personally, I think the increased CPU usage when updatedb is running is a small price to pay for some very useful functionality.

More info for the curious on KDE APPs here:
[http://www.kde-apps.org/content/show.php?content=17201](http://www.kde-apps.org/content/show.php?content=17201)

---

### Post by nick_h on 2008-03-27
It is also used in Places->Search for Files.

You can disable the update by renaming /etc/cron.daily/slocate to something with a "." in it.

Then you can always enable it again if needed, or run it manually.

---

### Post by natirips on 2008-03-27
> **MartinJ said:**
> The locate command is great!  KDE's locate:/ protocol is built on top of it, which is used in file browsers and open/save windows.  Personally, I think the increased CPU usage when updatedb is running is a small price to pay for some very useful functionality.

More info for the curious on KDE APPs here:
[http://www.kde-apps.org/content/show.php?content=17201](http://www.kde-apps.org/content/show.php?content=17201)

No, it's not! It takes over 20 minutes and I can't do a thing on my laptop during those times, everything's blocky, just opening the console takes about a minute, and typing those three letters "top" takes an age... btw, I use Gnome XD with "KDE on demand" or something, which I use rarely for stuff like Kolf or Kate (sometimes it's better that gedit).

---

### Post by natirips on 2008-03-27
> **nick_h said:**
> It is also used in Places->Search for Files.

You can disable the update by renaming /etc/cron.daily/slocate to something with a "." in it.

Then you can always enable it again if needed, or run it manually.

I never search for files though... I know exactly where my personal files are :). And thanks for advice.

---

### Post by nick_h on 2008-03-27
> **natirips said:**
> I never search for files though... I know exactly where my personal files are :). And thanks for advice.
You can still use *find* if you need to search for something - it doesn't use an index.

---

