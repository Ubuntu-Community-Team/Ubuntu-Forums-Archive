---
title: "Firefox Crashes When Printing"
date: 2005-07-29
forum: General Help
---

### Post by SuperMike on 2005-07-29
In the default Hoary Hedgehog, I was fine and I could print just fine with an HP Jet Direct kind of connection. But then I updated it when the little red upgrade icon came on. Now when I try to print, Firefox just crashes.

This makes me very  :sad:

---

### Post by amohanty on 2005-07-30
I had quite a few problems with the ff upgrade about a week back so I downgraded it back. Try that.

AM

---

### Post by Malkin on 2005-08-03
I'm having the same trouble on one of my Ubuntu machines.  The user doesn't know quite when it started, but it was probably sometime after one of the updates.  It happens in both Firefox and Thunderbird.  When one tries to print, as soon as the print dialogue screen opens, it crashes the entire program.  I've tried downgrading to Firefox 1.0.3-1.0.5 with no luck.

Also, I can no longer print from OOo.  Trying to print doesn't crash OOo- just nothing ever prints out.  No errors or anything.  Status says data file sent successfully.

Printing a test page from the printer setup under properties works just fine.

The printer is a LaserJet 4200n over a wireless network. CUPS with a static IP.

---

### Post by plm99 on 2005-08-10
I'm having the exact same problem with an HP2610xi printer. Is everyone with this problem using the HP printer driver? I have the latest HP driver. The test page prints perfectly.

---

### Post by Malkin on 2005-08-11
Yes, using the HP driver.  Perhaps I'll experiment with some other drivers.  I'll let you know if I find anything that works.

Anybody out there have any other ideas?

---

### Post by Malkin on 2005-08-11
Well, I tried replacing the HP with an Epson Stylus connected through USB, and I still get the crash.

Grrrrrrrrrrrrrr!

I'm about ready to reinstall the OS.  I feel like I'm on Windows.

---

### Post by Toddy on 2005-08-12
See this thread for using gtklp to print from apps like firefox:

[http://www.ubuntuforums.org/showthread.php?t=24850&highlight=gtklp](http://www.ubuntuforums.org/showthread.php?t=24850&highlight=gtklp)

---

### Post by eagle101 on 2005-08-13
I was having this problem also.  It appears to be related to Glider and a couple other themes.  I changed to Clearlooks and printing works great in Firefox 1.0.6.

Check out

[This Forum answer](http://ubuntuforums.org/showthread.php?t=23845&highlight=firefox+crash+printing)

---

### Post by plm99 on 2005-08-13
[QUOTE=eagle101]I was having this problem also.  It appears to be related to Glider and a couple other themes.  I changed to Clearlooks and printing works great in Firefox 1.0.6.

Check out

[This Forum answer](http://ubuntuforums.org/showthread.php?t=23845&highlight=firefox+crash+printing)[/QUOTE]

I treid the gtklp trick, no success.

I am not using any theme, (just the default) so my problem is not theme related.

Printer HP Photosmart 2610xi
Driver: hplip 0.94, network connected
Verified working applications:
  Openoffice
  Evolution
  gThumb
  etc.

Firewall up or down does not matter either

This seems to be strictly a Firefox issue.

Any other ideas?

---

### Post by plm99 on 2005-08-13
I take it back about the Theme thing.

I was looking at my Firefox Theme.

I changed my Gnome theme to "simple" and the printer just 'magically' started to work.

Very strange indeed!

Why would the desktop theme be tied to the printer in one application but not another?

---

### Post by eagle101 on 2005-08-13
Glad to hear you're printing successfully now.  I have no idea why a theme would cause a crash in a single application only. 

I'm sure a bug has already been submitted, there have been a lot of users with this particular problem.

Dave

---

### Post by plm99 on 2005-08-13
MORE wierdness:

When I was having the problem, I discovered I had the 'Glider' Gnome theme (same as Eagle101) so I changed to 'simple' it started working (my prior post) now I switched back to 'Glider' and it seems perfectly happy to print.

Changing the desktop theme seems to be the real fix. There must be some configuration parameters that get cleaned up in the process.

---

### Post by hoople on 2005-08-15
hi all,

i'm a newbie so will do my best to get it right.

having the same issues with ff & tb. the gtklp trick worked for a while then reverted. i'm using hoary & 1.0.6 of the moz pair.

the printer is hp photosmart 7660. don't know what driver, it'll be the default.

will play with the themes tonight and post the results.

otherwise luvvin' this linux stuff

---

### Post by StonePiano on 2005-09-19
[QUOTE=eagle101]I was having this problem also.  It appears to be related to Glider and a couple other themes.  I changed to Clearlooks and printing works great in Firefox 1.0.6.

Check out

[This Forum answer](http://ubuntuforums.org/showthread.php?t=23845&highlight=firefox+crash+printing)[/QUOTE]

Thank you.  Both Firefox and Thunderbird did a crash and vanish trick every time I tried to print.  I clicked System > Preferences > Theme... changed to simple.  Problem fixed.

StonePiano

---

