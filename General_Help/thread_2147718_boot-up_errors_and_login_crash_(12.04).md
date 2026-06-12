---
title: "boot-up errors and login crash (12.04)"
date: 2013-05-22
forum: General Help
---

### Post by PKfireball on 2013-05-22
Hello everybody, first time poster, and first time ubuntu user. If i posted this in the wrong spot, please forgive me. im a noob.

I recently downloaded ubuntu 12.04 and installed it. Upon the first inital bootup, there appeared a few small graphical glitches. small horizontal lines that looked a bit like this: ._ except not out of ascii characters. The lines are of a random color, usually red, blue, green, or purple. Once i reach the desktop, i see these lines all over the screen, appearing in a vertical pattern. Ubuntu will last about 5-10 seconds like this, and then proceed to crash. I tried uninstalling my graphics drivers, but to no avail, it did nothing. the lines remained. I am weirded out, because i had an old fedora distro on an old computer, and nothing like this ever happened. Help would be awesome, thanks.

Specs:
CPU: Intel i3-3.3ghz
RAM: 4gb
GPU: AMD Radeon HD 6570

---

### Post by HiImTye on 2013-05-22
try using nomodeset then installing the proprietary drivers
(at the grub menu) hit 'e' on ubuntu, go to after 'quiet splash' and add nomodeset then hit f10

---

### Post by PKfireball on 2013-05-22
This brings me into a low graphics mode that gives me some settings that I cant really change. I continued and got to a command line, and cant really do anything from there. What should I do from here? Also, thanks for replying to my first post.

---

### Post by HiImTye on 2013-05-23
from there you want to install your proprietary drivers, I believe they're in the list of repositories

---

### Post by PKfireball on 2013-05-23
I actually did some google searches and was able to do that. thanks for the help!

---

### Post by HiImTye on 2013-05-23
no worries, please mark as solved (edit first post then change prefix to [SOLVED]) so that others may benefit from it :D

---

