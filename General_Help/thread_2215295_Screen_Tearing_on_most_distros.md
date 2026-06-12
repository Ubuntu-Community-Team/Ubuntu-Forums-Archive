---
title: "Screen Tearing on most distros"
date: 2014-04-05
forum: General Help
---

### Post by ampage2 on 2014-04-05
Hi, I have a rather old laptop that I want to just use as an NAS. I've installed about 13 different distributions. I've tried Debian-based, Ubuntu-based, and even Fedora-based, though all share a common issue on my laptop. They will all boot fine, but later have the issue of screen tearing on the desktop. The only distros without the problem have been Puppy and DSL (besides native support with Windows XP). Anyone know a fix for this? Here is an example I just snapped:

[ATTACH=CONFIG]251766[/ATTACH]

---

### Post by ajgreeny on 2014-04-06
If you only want to use it as a NAS does that really matter?

What is the hardware, particularly the graphic card?  Let's see the output in terminal of command **lspci | grep -i vga**

---

### Post by mörgæs on 2014-04-06
Hi, welcome to the fora.
I can't see which distro you are running now. If you have lshw please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

