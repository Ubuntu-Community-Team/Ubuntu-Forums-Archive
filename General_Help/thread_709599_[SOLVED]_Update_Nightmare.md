---
title: "[SOLVED] Update Nightmare"
date: 2008-02-27
forum: General Help
---

### Post by tranquito on 2008-02-27
I have been running the Hardy Heron Beta for a few weeks now and despite a few minor bugs everything was going fine until yesterday. The update manager offered me a system upgrade and I accepted. When it finished, I restarted and it was a nightmare, my restricted drivers which include my graphics and wireless net card were replaced with generic drivers that wouldn't work properly. The Gnome desktop was exhibiting some eratic behaviours, clicking icons didn't work etc. Nautilus wouldn't work either.

Because of this I decided to backup my stuff and install Gutsy instead. I somehow managed to send my home folder to the trash and when i tried to get it out again there wasn't enough disk space then nautilus freaked out and trash wouldn't open anymore.

I booted from the Gutsy LiveCD and sure enough that home is gone.

My main question is this:
Where in the filesystem to trash files live? I need that home folder back. EVERYTHING is in there.

---

### Post by Therion on 2008-02-27
Going by memory but isn't it found at  ~/username/.Trash/ ??  

Ctrl+H to view hidden files, of course...

---

### Post by tranquito on 2008-02-27
Thanks for that. One problem, you do not have nessesary permissions to open .trash. Any ideas?

---

### Post by tranquito on 2008-02-27
Browsing using the terminal as root I found it at: /media/disk/root/.local/share/Trash/files/home/danny!
At least they still exist! Any suggestions?

---

### Post by bjorkiii on 2008-02-27
Thank god for this i thought it was only me , updates this morning completely well not completely but made things dodgy. Basically good thing i had stuff backed up i know its only alpha release so im not complaining upto then though it was running smoothly, ive had a bit too much too drink to give a lot of detail on problems but nowt was working as it should mouse menus other stuff but its a learning curve. And it was running excellent uptill then but like i say its a alpha :lolflag: but its looking good to me .

---

### Post by LunatikOwl on 2008-02-27
try typing as root
```

chown -R 1000 "/path/to/deleted/dir/"
chmod -R 770 "/path/to/deleted/dir/"

```
now what me and other *nix users do is set up some partition specifically to mount as home. then  when I upgrade my distro I remount this partition as /home and create my first user as the same name of my previous one. this way my settings are preserved.
although I never tried downgrading. Best of luck

---

### Post by tighem on 2008-02-27
I keep a copy of home directory on another disk. Rebuild is as easy as reinstalling and copying everything back over. You're right, everything is stored there. Makes it real easy to recover, but a bugger to lose.

---

### Post by tranquito on 2008-02-28
This little disaster has given me a gret appreciation of the awesome power of the terminal! I'm almost glad it happened! I'm backing everything up now.:)

---

### Post by LunatikOwl on 2008-02-28
My relationship with the terminal also started in an incident similar to yours. It's good to be familiar with the terminal and no gui can replace it. But...
For the lazy ones - if you only need to move file you can always "sudo nautilus".

---

