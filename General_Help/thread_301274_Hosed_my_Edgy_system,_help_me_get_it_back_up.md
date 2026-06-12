---
title: "Hosed my Edgy system, help me get it back up"
date: 2006-11-16
forum: General Help
---

### Post by lowracer on 2006-11-16
OK here's the short and long version of it:

Short:  My system's hosed and the only way I can log in is via the failsafe terminal.  How do I fix it so I can get back in to GNOME or KDE?

Long: I installed XGL/Beryl and it was fun to play with but when I'd go back into GNOME, my windows were hosed, no way to move them or minimize/resize since those controls around the edge of the window were gone.  So I logged in to KDE, used apt-get to remove ubuntu-desktop completely, then I reinstalled it.  At one point I had to boot into a purely textual system with huge fonts, and did the reinstall there as root.

Now I can't log in to either GNOME, KDE, or failsafe GNOME.  I can't see my backup drive to back up my home directory.  Hopefully someone has a quick fix that can get me back and running without trashing my home directory.

Thanks...

---

### Post by UltraSonicSite on 2006-11-16
From the lack of information given to me, it seems the only logical solution is to reformat. Linux is odd like that =(

---

### Post by lowracer on 2006-11-16
OK I think I'm going to wait for a second opinion.

Does anyone know what the /dev name is for an external firewire drive?  I could probably back up my home directory if I could just mount the external drive.  But I don't know what it is called.

---

### Post by UltraSonicSite on 2006-11-16
Fair enough, if for whatever reason you have to resort to a reformat, try to keep away from Beryl, and other "eyecandy" window managers. They have a tendency to, for whatever reason, mess up the X server.

---

### Post by Joe_CoT on 2006-11-16
Honestly, removing ubuntu-desktop wasn't a good idea :( 

The problem with xgl is that it majorly changes core system stuff, like the xserver.

What guide did you use? If you can link to the guide, that'd help a lot. Odds are, you replaced your xserver with one in a third party repo they gave you, and it screwed things up. You probably want to remove those repos and reinstall the packages (though still give me a link to the guide so i can see what else was changed).

running startx from the console, can you describe the error xserver is giving?

---

### Post by lowracer on 2006-11-16
I have a bookmark to the guide I used...  but, it's on the hosed system.:( 

At this point I'm ready to do a complete reinstall, but I need to get access to my home directory.  I'm booted into the live CD for Edgy, but I can't see my /dev/sda1 drive.  I've got my firewire drive mounted but now I can't get to my home folder.  /dev/sda1 shows up in gparted.

---

### Post by Joe_CoT on 2006-11-16
Yeah, if you don't know the guide, can't read minds :-/ You can try what i said about the repos and getting me the xorg error.

If you're just going to reinstall (may be easier), and need the home directory, try this
```
sudo mkdir /media/drive
sudo mount /dev/sda1 /media/drive
```

Then your filesystem will get mounted in /media/drive, and you can copy from there.

---

### Post by lowracer on 2006-11-16
startx from the failsafe terminal says:

xauth: creating new authority file /home/mark/.serverauth.4896
X: user not authorized to run the X server, aborting.

Couldnt get a file descriptor referring to the console

I wonder if this is related to my having reinstalled ubuntu-desktop as root from that terminal with the huge fonts?

---

### Post by Dubbayoo on 2006-11-16
I messed up Dapper big time messing with compiz. I only fixed the errors by upgrading to Edgy. It just wasn't worth it. I'll wait til it's part of the base system.

---

### Post by lowracer on 2006-11-16
> **Dubbayoo said:**
> It just wasn't worth it. I'll wait til it's part of the base system.

Well if I get my data back it will have been worth it.  I thought the "OS X Expose" feature where you can tile all the windows to select the one you want, and rotating the cube by moving the mouse to the left or right edge were very useful tools.  I could live without the wobbly windows and other eye candy junk.

OK I got the drive mounted and am backing up.  

Thanks for all the help!

---

### Post by Joe_CoT on 2006-11-16
Sorry it didn't work out for you. If you still want to use beryl, and you have a not nvidia card, you may want to try using aiglx instead.

[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

i've used the aiglx method (on my desktop) and the xgl method (on my laptop), both in edgy, with no problems whatsoever. If you decide to use one, and have the same or similar issue with it **do not** remove ubuntu-desktop, and instead just post the issue ;)

---

### Post by lowracer on 2006-11-16
I have the nVidia 7600GS...  and I think I'll wait until Feisty is released before I mess with Beryl again.

I spoke too soon about the backup.  For some reason the LiveCD system has mounted my firewire drive read-only...

---

