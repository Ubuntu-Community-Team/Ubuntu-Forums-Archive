---
title: "first try with linux - messed my pc up"
date: 2008-03-23
forum: General Help
---

### Post by wob_b on 2008-03-23
Hi,
i thought id dabble in some linux and  i installed ubuntu on my acer desktop, while keeping the Vista already on it.
but seem to have hit a few problems:

Firstly, when restarting the computer, after setting the exact model of the screen in the configurations, when i select to run linux as the OS, the screen (the actual monitor) tells me it "cannot read input".

Secondly, i tried to fix this by trying some other screens and try to see if i could recover the old settings - not that i know anything about linux to be honest. However, this meant i had to turn the computer off without shutting down, many times (this might be the cause of my second problem). now every time i try and run Vista, i get the "blue screen of death". What can i do? as i cant access either OS. 

id really quite like to keep all the setting and things in vista, especially the files.

Could i remove ubuntu without actually going into it? or is there a method of doing it in a text based formate which would still work with my screens? and would this solve the problem with vista?

---

### Post by tgalati4 on 2008-03-23
Boot to a rescue terminal.  Then run the following:

>sudo dpkg-reconfigure -phigh xserver-xorg

(Sudo is not really needed since a rescue shell runs as root, but it's helpful to remember that you can use this as a user as well.)

---

### Post by elchico04 on 2008-03-23
you could just delete/format the partition that ubuntu is on.

---

### Post by Tyke91 on 2008-03-23
System specifications please.

Please tell me you have all your files backed up, this would make it alot less painful, barring that, can you boot to the live CD and create backups from there? (when you get the desktop, grab some sort of removable device, CD, DVD, Flash drive... and copy/paste all of your important windows files to it)


once you're done doing that, restart and take the live cd out. can you boot into a recovery console? (restart and choose recovery from GRUB) 

if you can't get into recovery mode, I would suggest a reinstall, possibly with a new cd (maybe the alternate one?) 

If you can get into recovery mode I'm sure the other people here will have further instructions. It sounds like your display isn't being recognized by the OS. It could be a video card issue as well, but those tend to give black screens of death. 

anyway, can't help you any more without specifications


EDIT: bah, doubleninja'd

---

