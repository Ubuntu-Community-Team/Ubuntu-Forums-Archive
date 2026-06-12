---
title: "Help - Unity broken"
date: 2013-12-22
forum: General Help
---

### Post by hhall on 2013-12-22
Hi. I appear to have a major problem. I was on the latest long term release, and just now, on restarting, the Unity launcher appears to have broken.

I cannot see the top or side bars, and only have access to files on my desktop. 

I can access the terminal on Ctrl, Alt F1, but it prompts me for a login and a password. I know my password, but am mystified as to the login it wants. I don't think it's ever asked me for that. 

Is there any way I can get Unity to function again? I really do need help...

---

### Post by deadflowr on 2013-12-22
can you run ctrl+alt+T in the blank/bare desktop?
It should open a terminal.

If so, look at this
[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

or if you have compizconfig-settings-manager installed, try launching it with
```
ccsm
```
and then look to see if the unity shell plugin is enabled.

But I'd go with the instructions on the link first.

---

### Post by hhall on 2013-12-23
I am afraid Ctrl/Alt/T doesn't do anything. Still no idea how to get my pc to work...

---

### Post by Iowan on 2013-12-23
> **hhall said:**
> I can access the terminal on Ctrl, Alt F1, but it prompts me for a login and a password. I know my password, but am mystified as to the login it wants. I don't think it's ever asked me for that.  That would be your username, followed by your password.

---

### Post by grahammechanical on 2013-12-23
There is also something else that you can try when at a desktop without the top panel and the Launcher. Right click the desktop and select Change Desktop Background. That should open System Settings and from there you can try changing video drivers using Additional Drivers.

When using Ctrl+Alt+F1 or F2, etc., we get to a Linux command line outside of the desktop. This is why we need to log in. There are two useful commands

```
sudo shutdown -r now
```
```
sudo shutdown -h now
```

The first command restarts and the second halts - shutsdown the operating system. It is a bit more gentle than hitting the power button because we do not have a power/cog indicator on the top panel.

Regards.

---

### Post by hhall on 2013-12-23
Hi again.

Thanks for the advice, everyone, I did manage to get into terminal at last and I reset Unity and it kind of works, but not quite:

The left and top panel are back, but look different than before, with some items missing and some blacked out. Same for the desktop itself, where most items, be they folders, files or images, now show in the same way, a blank white panel with the file name. Like this:

(See attachment below)

I don't think anything has disappeared, but things are not working properly. I was going to copy everything relevant to an external drive and think about a fresh install, but I have the impression that some files are not being copied, I tried to do the same thing from a live usb stik, but it does not permit me access to many of my files. 

Considering that the overall system appears to still work, is there something I can do to repair my installation?

Thanks,

HH

---

### Post by hhall on 2013-12-23
OK, so far everything I try to do works, except copying some files, The Unity system is, however, totelly messed up. It shows some items it never did before on the side bar, and fails to show most that it used to, including some that are actually there and can be used, but simply do not show up visually. Most importantly, "Home Folder" works but remains invisible. Everywhere I go, there are things that work, but don't show up visually. Is there anything I can do about this?

HH

---

### Post by deadflowr on 2013-12-23
Since you've reset unity, have you done a clean reboot, yet?
It might clean up and reset the launcher.
Of course, it could also reset the borkage.

But in my own experience, whenever I bust up unity and compiz and reset them, things never seem right until I do a restart.
Then things look as normal as they were before my fits of whatever I did to cause the problems.

But big +1 to copying and backing up your files.
You should do that anyway.

---

### Post by hhall on 2013-12-24
Dear deadflwr. 

It appears to be the case that you were right.

Thank you and Happy Holidays!

HH

---

