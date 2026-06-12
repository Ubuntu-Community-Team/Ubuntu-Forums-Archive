---
title: "Restoring /etc/sudoers?"
date: 2008-04-21
forum: General Help
---

### Post by AdrianStrays on 2008-04-21
Alright. I was trying to setup firestarter so it automatically began at boot.  I followed the instructions on the FAQ page only to discover I couldn't save the sudoers file.  So, I saved it elsewhere, then moved/overwrote the original with the edited one. It still doesn't work, and I can't edit it through the terminal, as it says something to the effect of "it should be "0440" when it is "0644"

If someone could help me restore my original sudoers file to working order, as well as auto start Firestarter, I'd be grateful.

---

### Post by wormser on 2008-04-21
Try this:

```
sudo chmod 440 /etc/sudoers
```

If that does not work you will need to boot into recovery mode and run the command without sudo.  

Your firewall starts automatically.  Firestarter is just a tool to configure it.  So, there is no need to start it at boot.

---

### Post by AdrianStrays on 2008-04-21
None of the sudo commands work.  There is a file called sudoers.save, which I assume is a backup, however because I can't use the sudo command I can't alter it.  If I am correct in my hypothesis, how would I go about altering it without using the sudo command (the directory is locked, by the way) additionally, the "administrative window" won't pop up either.

As for your suggestion, I am not sure I can do that.  I edited grub so that there is no wait time in selecting which system to boot as.  Can I alter grub without using sudo?

---

### Post by koenn on 2008-04-21
try hitting [Escape] a couple of times by the end of the POST (when your PC is booting and bringing ip its hardware), i.e just before Grub is starting to run. You might get lucky

otherwise, you'll need a Live CD, mount your hard drive (eg to /media/sda1) and look for the grub menu  in /media/sda1/boot/grub/menu.lst
use a text editor to set the tim-out to a higher value, then save and reboot

---

### Post by AdrianStrays on 2008-04-22
> sudo chmod 440 /etc/sudoers

That did the trick, although I had to enter into Recovery Mode.

---

