---
title: "Having gnome and bspwm running concurrently"
date: 2019-05-15
forum: General Help
---

### Post by djedefre on 2019-05-15
I just installed ubuntu 18.04 and wanted to try out bspwm window manager.
I followed [this]("https://github.com/windelicato/dotfiles/wiki/bspwm-for-dummies") tutorial doing the "with display manager" path.
At the end of this, it tells you to restart your current display manager. 
I executed "sudo service gdm restart" and then everything just starts flickering between the normal desktop and the "gnome text log". 
(I don't know how you properly call it. I mean the command line where most lines start with [OK])
Moreover, the OS doesn't react to any mouse/keyboard input.

After that, I restarted logged into my account on gnome switched to tty3 and tried to start bspwm through "startx". 
However here I just get a black window and nothing happens. It also doesn't react to the keybindings set in sxhkd (Though I know that sxhkd works as it reacts to the keybinds in gnome).

Lastly, I restarted once again and then on the login screen found the small cog where one can select between bspwm, Ubuntu, and Ubuntu with Wayland. 
I selected bspwm logged in and it worked.

Though now I was wondering if it is possible to have bspwm running on e.g. tty2 and gnome on tty3 at the same time?
Therefore I tried selecting bspwm on the login screen, logging in, switching to tty3 and executing "sudo service gdm restart" there. 
However, this resulted in the same flickering as described above though now between "Linux text console" and the "gnome text log" and turned bspwm into a black screen.

Can someone help and/or explain why and what the problems are?

---

### Post by deadflowr on 2019-05-15
Duplicate thread. 
See original thread here:
[https://ubuntuforums.org/showthread.php?t=2418936]("https://ubuntuforums.org/showthread.php?t=2418936")

Feel free to bump the original thread if no response within 12 to 24 hours or longer.
(BUMP = Bring up my post which will bring the thread up to the top of the post listings)


This thread is closed

---

