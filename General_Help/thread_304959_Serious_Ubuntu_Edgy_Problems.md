---
title: "Serious Ubuntu Edgy Problems"
date: 2006-11-22
forum: General Help
---

### Post by tgone on 2006-11-22
Hello,

I'm new to Ubuntu and Linux so please excuse my ignorance...

Last night I installed Python 2.5 and then attempted to remove the Python 2.4 package. 

I ran this command: sudo apt-get remove python-2.4

But I must have done something very wrong. After I executed the command, I minimized the shell window and about a minute later I noticed that apt was removing every package on my system! I stopped the process right after Evolution had been removed. Many important packages were removed before I noticed, including Gnome's panel.

Now when I boot my computer I see the shell prompt (Gnome won't load).

Is there anyway to repair the lost packages without a complete reinstall? Is there a way to fix Gnome so I can login and backup my files?

Any advice is appreciated.

---

### Post by o_fortuna on 2006-11-22
> **tgone said:**
> Hello,

I'm new to Ubuntu and Linux so please excuse my ignorance...

Last night I installed Python 2.5 and then attempted to remove the Python 2.4 package. 

I ran this command: sudo apt-get remove python-2.4

But I must have done something very wrong. After I executed the command, I minimized the shell window and about a minute later I noticed that apt was removing every package on my system! I stopped the process right after Evolution had been removed. Many important packages were removed before I noticed, including Gnome's panel.

Now when I boot my computer I see the shell prompt (Gnome won't load).

Is there anyway to repair the lost packages without a complete reinstall? Is there a way to fix Gnome so I can login and backup my files?

Any advice is appreciated.
It's actually not as bad as it might seem.
You're at a terminal, so try to type this:
```
sudo apt-get install ubuntu-desktop
```
This should reinstall important things, including GNOME. Happy hunting ;)

Oh yes, and it's a good idea not to remove stuff like Python that have tons of dependencies (most Ubuntu packages that use Python were built with 2.4 in mind, so they "depend" on it). Of course, the apt command should have told you that it was about to remove all those files. Anyway, it's understandable to make the mistake, but luckily it's easily recoverable.

... Ah, and as far as backing up your files, that can be done with a command line -- it's just a bit difficult. Try to find a terminal tutorial somewhere -- you can use commands like "cd /home/yourname/Documents" and then "cp *.odt /media/usb/Documents/" to copy all "odt" files from your Documents folder to a USB device at /media/usb.

---

### Post by tgone on 2006-11-22
Thanks. Your advice worked as planned. I didn't think it would be this easy.

Too bad apt didn't give me a warning. But now I know!

---

### Post by tgone on 2006-11-22
Now I have Python 2.4 and 2.5 installed. If my system depends on 2.4, how can I use 2.5 as the default? For example, when I want to launch the command line interpreter.

---

