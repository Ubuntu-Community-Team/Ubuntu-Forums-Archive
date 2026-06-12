---
title: "Make a script run on startup"
date: 2007-01-12
forum: General Help
---

### Post by Azakus on 2007-01-12
I have a Xubuntu 6.06 box I use as a fileserver and NAS that I run headless. I run Folding@Home on it by using a script I made to start it up and run without my intervention and I want to be able to have my fileserver run the script when it starts up. This way, if I need to reboot it for an update, it will start where it left off on the Folding@Home data. How can I do this?

---

### Post by dcstar on 2007-01-12
> **Azakus said:**
> I have a Xubuntu 6.06 box I use as a fileserver and NAS that I run headless. I run Folding@Home on it by using a script I made to start it up and run without my intervention and I want to be able to have my fileserver run the script when it starts up. This way, if I need to reboot it for an update, it will start where it left off on the Folding@Home data. How can I do this?

Have a look at your /etc/init.d directory, that is where startup scripts exist and they are linked to the various /etc/rc.d directories.

If you do a web search you should find numerous articles with detailed instructions to help you.

---

### Post by Azakus on 2007-01-12
I've followed a guide to put it in init.d and attach it to rc.d, but it didn't work
{EDIT}Oops, forgot to make it executable to all, nevermind.

---

