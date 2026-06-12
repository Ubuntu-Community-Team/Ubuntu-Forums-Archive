---
title: "NOTHING works after upgrading to 6.10 :( Please help!"
date: 2006-10-28
forum: General Help
---

### Post by Starlight on 2006-10-28
Hello... today I upgraded my Ubuntu from 6.06 to 6.10 using the cdromupgrade program from the alternate install CD. The actual upgrade went quite well, so I didn't even expect to see what I saw after rebooting the computer. And I saw.... nothing. Literally. A blank screen, with a blinking cursor at the top left.  But the computer seemed like it was doing something, so I decided to wait. After staring at the blank computer screen for a while, I decided to press Alt-F1, because I thought that maybe it had switched me to a wrong console. Then, I saw... something. That something looked more or less like this:

```
usplash: No usable theme found for 1024x768
screen init failed
```

So, I was staring at the peculiar error message, while waiting for anything to happen. And it did. This time it was an error message from xorg, or something similar. I wrote down a fragment of it with the actual error, and here it is:

```
module ABI major version (0) doesn't match the server's version (1)
Failed to load module "fglrx" (module requirement mismatch, 0)
No drivers available
```

I checked lsmod, and the module fglrx appeared to be loaded. So it should have worked. Of course it didn't, so I decided to edit the /etc/X11/xorg.conf file, and change "fglrx" to "ati". Then, I rebooted.

The system startup was exactly the same as last time, a blank screen with a blinking cursor. But this time the graphical login screen loaded after a few minutes of waiting. With an error, of course. But it wasn't some serious error, it just said that it can't find some theme. (Why the heck did the upgrader delete my themes?!) But I could log in, so I logged in with the XGL session I normally use. After what had happened before, I actually didn't expect it to work, so I wasn't surprised that a few seconds later I was looking at the login screen again. This time I decided to run the regular GNOME session. Of course, it didn't work too. The only thing which appeared on my computer screen was a light brown background, and a mouse cursor over it. No panels, no wallpaper, no desktop... I could only Ctrl+Alt+Backspace out of it, so I did. And I tried to run the failsafe GNOME session. This time the desktop, wallpaper, and panels loaded, but immediately after they did, everything just stopped working. Clicking anywhere did nothing, maybe because for some reason it tried to load Beryl, even though it wasn't an XGL session. (is it possible to disable it somehow by editing some configuration files?). I Ctrl+Alt+Backspaced out of it, and the last option I had was the failsafe terminal session. Surprisingly, it worked, and it didn't crash when loading the terminal. But I couldn't really do anything there. I wanted to download the fglrx driver again, but I found out that my internet connection didn't work. When I ran network-admin, it didn't let me activate ra0. When I used the "iwlist ra0 scan" command, it said there are no results. 

So, I rebooted the computer and this time I picked the good old Windows XP so that I could post about it all here... does anyone have any hints how to fix all this? I'm going to download the Ubuntu CD and just install it again from scratch. Is it possible to do it without formatting the Linux partition, so that I don't lose my personal files from the home directory? Or maybe there's a way to make it work without reinstalling?

---

### Post by Starlight on 2006-10-28
bumping.... can anyone help me? I really need to use Ubuntu... I have all my emails, bookmarks, IMs, etc. on it....

---

### Post by PriceChild on 2006-10-28
Not sure about the rest.... but if you do reinstall, you can save your entire home folder to keep all your emails and bookmarks etc.

---

### Post by Starlight on 2006-10-28
Hi! Thanks :) Do you mean when I reinstall without formatting the partition? I was going to start a new topic about it... if I reinstall Ubuntu without formatting the partition, will it keep my home folder? Or do I have to copy everything to a Windows partition and then copy it back to Ubuntu after I install it again?

---

### Post by randlieb on 2006-10-28
i am interested in seeing how to reinstall without losing my home directory. i have edgy installed with home in one partition and root in another. i don't have a problem now but it would be nice to learn something new here. a response or link to a HOW TO would be great.

(my upgrade to edgy went flawlessly.)

---

### Post by pablogabriel on 2006-10-29
I haven't tried it but it seems that the Alternate CD you can download from ubuntu.com is the aproppiate for reinstalling ubuntu on an already installed system. 
I've upgraded from dapper to edgy and the system doesn't boot anymore. It hangs after /scripts/init-bottom (I see that message only in recovery mode) with any kernel.
Good luck!

---

### Post by erimar77 on 2006-10-29
Try renaming your 

```

sudo mv /etc/x11/xorg.conf /etc/X11/xorg.old

```

then run:
```

sudo dpkg-reconfigure xserver-xorg

```

that will recreate a new xorg.conf for you.. i usually accept most/all defaults the first time around to get things working right

isn't it kinda funny how "stable" windows can be sometimes.. lol

---

