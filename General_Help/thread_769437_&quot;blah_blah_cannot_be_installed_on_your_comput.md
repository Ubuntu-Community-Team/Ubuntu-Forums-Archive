---
title: "&quot;blah blah cannot be installed on your computer type (i386)&quot; can somebody help?"
date: 2008-04-26
forum: General Help
---

### Post by dluu13 on 2008-04-26
Hello, there's something wrong with my computer.

I can't install anything.  Everything I try to install comes up with this error message.

Program Name cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type. 

I saw somewhere that it said it might be because I'm trying to run 64 bit binary on a 32 bit PC but I'm sure that's not the case.  I checked the CD and it's one for 32 bit.

Just some hardware specs on this computer.
It is:
933MHz PIII
512MB PC-100 RAM (I know I should be using PC-133)

I don't think any other hardware specs are relevant, but:
nVidia GeForce 4200Ti
2 Maxtor 60GB hard drives
2 Samsung CD Drives
1 Floppy Drive
Asus CUSL2 MOBO

I am also dual-booting Windows XP

---

### Post by smoker on 2008-04-26
what is it you are trying to install, and are you installing via the synaptic package manager, or some other method?

---

### Post by dluu13 on 2008-04-26
Something was wrong with my RhythmBox music player, I don't know exactly what.  I tried opening a file with it, and there was some error about it not being able to open the file because of a bug with RhythmBox, Gstreamer.  

I then went ahead and uninstalled it and when I tried to reinstall it, that error message popped up.  It pops up when I try to install anything else as well.  (Eg. games whatever there is)

I am using the Add/Remove programs thing in the applications menu.

I tried Synaptic Package Manager.  I can install things from there.  I tried Rhythmbox first, and it would not install.  It kept saying something about it being obsolete.

---

### Post by smoker on 2008-04-26
rythmbox was looking for the 'gstreamer codec plugins' which you can install via add/remove - type 'gstreamer' in the search box of add/remove, and install all the gstreamer codecs from there.

if you still have trouble with rythmbox, remove it via the synaptic package manager, and reinstall it again, and hopefully all will be fine,

best of luck

---

### Post by JimmyHopkins on 2008-04-26
"Something was wrong with my RhythmBox music player, I don't know exactly what. I tried opening a file with it, and there was some error about it not being able to open the file because of a bug with RhythmBox, Gstreamer.

I then went ahead and uninstalled it and when I tried to reinstall it, that error message popped up. It pops up when I try to install anything else as well. (Eg. games whatever there is)"

That is because mp3 files must be licensed (they are not free). Go to add/remove, change "show:" to "all available apps" and search for and install "ubuntu restricted extras". This will run your music. If not, search for "codec" and download all the codecs.

Most games use windows binary files (something.exe) and thus cannot be play under linux (natively, as in, without emulation). Try downloading "wine", insert your CD, and run "setup.exe". As long as the game isn't very new (crysis),and you have an intel processor (or any i386), you can play most games (I play roller coaster tycoon, dues ex, and halflife 2 all the time).

---

### Post by dluu13 on 2008-04-26
> **JimmyHopkins said:**
> "Something was wrong with my RhythmBox music player, I don't know exactly what. I tried opening a file with it, and there was some error about it not being able to open the file because of a bug with RhythmBox, Gstreamer.

I then went ahead and uninstalled it and when I tried to reinstall it, that error message popped up. It pops up when I try to install anything else as well. (Eg. games whatever there is)"

That is because mp3 files must be licensed (they are not free). Go to add/remove, change "show:" to "all available apps" and search for and install "ubuntu restricted extras". This will run your music. If not, search for "codec" and download all the codecs.

Most games use windows binary files (something.exe) and thus cannot be play under linux (natively, as in, without emulation). Try downloading "wine", insert your CD, and run "setup.exe". As long as the game isn't very new (crysis),and you have an intel processor (or any i386), you can play most games (I play roller coaster tycoon, dues ex, and halflife 2 all the time).

Well, I can't really install anything right now.  It's not exe's that are causing the problem.  I'm trying to install through add/remove programs.

And now, I can't even get rhythmbox back since I uninstalled it.  I can't get it through the add/remove, I can't get it through synaptic package manager since it doesn't show up anymore, and I can't get it through the terminal because I can't find it there either.

---

### Post by smoker on 2008-04-26
a couple of suggestions, have you enabled the 'repositories' in synaptic? - open synaptic, go to 'settings' and click 'repositories' and tick all but the 'source' repo, also tick the 'third party' repo.

also, on the status bar at the bottom of the synaptic box, are there any broken packages showing? if so, go to the filter on the left, select 'custom filters' and 'broken' and then unintall anything that shows there, this may show rhythmbox, and if so, once the broken package is removed, try and reinstall it again.

---

### Post by ibuclaw on 2008-04-26
What kernel **type** are you running?

Open a terminal and type in:
```
ls /boot | grep linuz
```

Regards
Iain

---

### Post by dluu13 on 2008-04-26
Thanks, but my brother was failing and he reinstalled the system.  I am typing on the live CD right now.  I guess I'll wait until it's done and try again.  I'll report back when it's done.  I hope I don't have to do any more fixing though.

---

### Post by dluu13 on 2008-04-26
The Ubuntu is installed all the way from the beginning.  Now, I have the RhythmBox back, but I still can't install.


I did ls /boot | grep linuz and I got:

vmlinuz-2.6.22-14-generic

Is there something that I have to do with that?

EDIT: I found an i386 kernel using apt.  I'm trying to install it right now and see what happens.

---

### Post by dluu13 on 2008-04-26
OK, I installed all updates, and I also use the 386 kernel.  It still does not work.

There is nothing in the broken.

Might it have something to do with actual hardware?

---

