---
title: "Yikes! &quot;GDM: Xserver not found... what do i do?"
date: 2007-01-14
forum: General Help
---

### Post by konungursvia on 2007-01-14
I've been running dapper on my Dell for a week straight without shutting down, and it was becoming a little funky (USB ports stopped working for instance) so I decided to reboot it. 

Now, it says GDM server not found, then a bunch of /usr/bin/Xgl :0 and stuff, and it says I have to install the Xserver or corect GDM configuration and restart. MY beloved Ubuntu won't start any more (or Gnome won't).

Trouble is, I don't know how to do either of those things. Can I copy the files from the CD?

Please help!

---

### Post by konungursvia on 2007-01-14
> **konungursvia said:**
> I've been running dapper on my Dell for a week straight without shutting down, and it was becoming a little funky (USB ports stopped working for instance) so I decided to reboot it. 

Now, it says GDM server not found, then a bunch of /usr/bin/Xgl :0 and stuff, and it says I have to install the Xserver or corect GDM configuration and restart. MY beloved Ubuntu won't start any more (or Gnome won't).

Trouble is, I don't know how to do either of those things. Can I copy the files from the CD?

Please help!

Sorry to be a pain, but I can't figure out what to do. How do I navigate to the actual cd drive in terminal mode? is that the solution, to copy files from there?

Thanks in advance.

---

### Post by acorey on 2007-01-17
I had a similar problem after trying to install beryl (unsuccessfully).

My workaround was to start in safe mode by hitting escape key during GRUB.

Typing startx as /root' which started gnome for me as root.

Run "synaptic", from terminal. (there was no menu button for it as root)

Install "wdm" (wings display manager). Install Wizard asks for default display manager. I selected wdm.

Reboot. cntrl-alt-backspace then "exit" at root.

Upon reboot all was well with new display manager.

Good Luck!

---

### Post by Patrick-Ruff on 2007-01-17
I don't think he tried to install beryl.

here's waht I think you should do: 

CTRL + ALT + F1

or get to the terminal prompt somehow (not the GUI one.)

copy all your personal files to a thumb drive (if accessable) if you don't have one then you're going to have to find a way to burn a cd straight up from the terminal (yes it's possible.)

if you run into any delema's with this, you should ask in this thread.

---

### Post by bodhi.zazen on 2007-01-17
Hmm ...

sounds like you may have an imminent hardware failure :(

Her is a link on how to burn from the CLI (if you need it)

[http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

---

