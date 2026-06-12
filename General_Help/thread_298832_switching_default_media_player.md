---
title: "switching default media player"
date: 2006-11-13
forum: General Help
---

### Post by darkpaw on 2006-11-13
Hi, all.  Fairly new to Ubuntu, but been using variations of Red Hat/Fedora for years now.  There is something about Ubuntu that is driving me insane, and I was wondering if somebody could help me...

In Ubuntu 6.06, the default media player is Totem, which can't play virtually anything.  I installed VLC, and compiled and installed the most recent XVid library, and VLC plays just about everything.  But files I have that are tagged as mpg/mpeg (and QT, for that matter) still try to play in Totem.  Everything I can find on changing the default player says to right-click on one of them and select the player.  I do that, and it does it only the once.  If I right-click on one and select Properties then select "Open with" and pick VLC there...it sets the default for **that one file** to be VLC.  From what I've read, either of these methods should now have VLC as the default player...but every other file I have still opens with Totem.  I hope I don't have to go through my files and change every one of these manually...?!

This sounds like a bug.....or is there more to it than this?

---

### Post by organica on 2006-11-13
I'm running 6.10 and when I right-click and open-with the panel says "Select an application to open [file] and others of type "AVI Video".  For AVI's of course.  Does yours say the same?

---

### Post by darkpaw on 2006-11-13
Thanks for the reply...

When I right-click on one I haven't changed yet, it says "Open with movie player" in a top section of the popup, then a bar, then "Open with Other application".  After I change it to VLC (by selecting it from the "other application"), then the one I changed it on now has "Open with VLC" in the top section, then a bar, then "Open with movie player" and "Open with Other application" under it....but everything else is still the original way.

It remembers it on a file-by-file basis, apparently, which is not good.  Is there a way to make it global?

---

### Post by nix4me on 2006-11-13
remove totem alltogether - sudo apt-get remove totem.

That will solve it.

I use mplayer so i just removed totem, that makes mplayer play everything on my machines.

nix4me

---

### Post by organica on 2006-11-13
> **darkpaw said:**
> Thanks for the reply...

When I right-click on one I haven't changed yet, it says "Open with movie player" in a top section of the popup, then a bar, then "Open with Other application".  After I change it to VLC (by selecting it from the "other application"), then the one I changed it on now has "Open with VLC" in the top section, then a bar, then "Open with movie player" and "Open with Other application" under it....but everything else is still the original way.

It remembers it on a file-by-file basis, apparently, which is not good.  Is there a way to make it global?


Ah ha, I see exactly what you are doing.  Try this instead, it will fix your issue.  Right-click the culprit movie file, then choose "Properties".  In the Properties panel there is a tab called "Open with", click it.  In this tab, you can choose which media player will open ALL the media files of this type (Avi, mpg, ogg, or whatever file you chose).

That should fix it.

---

### Post by darkpaw on 2006-11-14
Nope, already tried that (check up in the original post).  Most threads following this problem (that I could find, anyways) all said to do that, too.  It doesn't work.  It also only changeds it for the single file.

Though it sounds cliche...do I have to reboot before the changes to picked up for this?

---

### Post by Aussiechick on 2006-11-15
I also had this problem.  Removing totem is a pain as there are other files dependant on totem.  I noted there are other streams if you really want to do this.   I got around this problem by going to properties BEFORE opening the file.  In the "open with" tab you must make sure that the spot is marked on Mplayer.  Just clicking on Mplayer does not change the default. I thought I had selected it but when I double checked i actually hadn't

---

### Post by organica on 2006-11-15
> **Aussiechick said:**
> I also had this problem.  Removing totem is a pain as there are other files dependant on totem.  I noted there are other streams if you really want to do this.   I got around this problem by going to properties BEFORE opening the file.  In the "open with" tab you must make sure that the spot is marked on Mplayer.  Just clicking on Mplayer does not change the default. I thought I had selected it but when I double checked i actually hadn't

Good call..you actually have to click the bullet button rather than just select the application choice.

---

### Post by pavelchjen on 2007-11-05
from terminal start gconf-editor. then chose 'desktop'->'gnome'->'url-handler', find mms or rstp and chose in right panel 'command' change volue totem %s to vlc %s

---

### Post by brandonjp on 2007-11-26
> **organica said:**
> Good call..you actually have to click the bullet button rather than just select the application choice.

I've been having this same problem - but it won't LET me click the bullet - i can click the bullet to no end with no response......very frustrating....any ideas?
--bp

---

