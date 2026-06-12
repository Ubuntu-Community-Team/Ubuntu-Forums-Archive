---
title: "X does not recognize my monitor, most of the time."
date: 2007-07-13
forum: General Help
---

### Post by Patrick Urs on 2007-07-13
Note: This doesn't always happen. But most of the time it does.


When I turn on my computer, after the entire 'ubuntu loading screen', it just shows the following blinking symbol:

_


That means:

I cannot type. I cannot enter a visual desktop. I cannot enter gdm.


So, I booted with a mandriva one cd. It gave me the following error message: x cannot detect a monitor on your system.


Basically, what can I do to fix it?

---

### Post by Atomic Dog on 2007-07-13
I had some monitor issues and was able to fix it by adding

```
        Option          "DDC"      "false"
```
to the monitor section of my xorg.conf file.  You could try it.  Worse thing that can happen is you have to remove it.
DDC is a plug and pray monitor detection.  It caused me some issues as it was not detecting my monitor properly for some reason.

---

### Post by Patrick Urs on 2007-07-13
Forgive my absolute incompetence, but how can I edit the x.org file without being able to get into x in the first place?


And, btw, Thank You!

---

### Post by simoncifer on 2007-07-13
> **Patrick Urs said:**
> Forgive my absolute incompetence, but how can I edit the x.org file without being able to get into x in the first place?


And, btw, Thank You!

Well, if you are familiar with the command line, you can edit that file via tty2 or something.  Namely, after the computer boot up and at GDM, you can press [CTRL]+[ALT]+[F2] to get a command prompt (I think it's those combination, I could be wrong).

Then you can login and edit /etc/xorg.conf using a console version of text editor, like nano or vi.

---

### Post by Patrick Urs on 2007-07-13
uh, gee, thanks?

I can't get to gdm, though!

---

### Post by avik on 2007-07-14
Try pressing Alt-Alt-F1 regardless of whether or not you get to gdm.  Then log in and use:

```
sudo nano /etc/X11/xorg.conf
```

to edit the file.

You installed Ubuntu, so I'm guessing you can use the Ubuntu Live CD (with or without the GUI).  Just mount your hard drive and edit the file from the Live CD.

---

### Post by Patrick Urs on 2007-07-18
yay! It works now! Thank You!

:razz:

---

