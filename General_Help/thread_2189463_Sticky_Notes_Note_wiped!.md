---
title: "Sticky Notes: Note wiped!"
date: 2013-11-22
forum: General Help
---

### Post by Mk32 on 2013-11-22
I put my laptop to sleep today and when I come back, a note that was not in active window or in edit/view mode had all of its text replaced by ...

/

and that was it. I found the .note backups in ~/.local/share/tomboy, but not the one I had! It's two blasted Welcome to Tomboy and some other note I deleted long ago. 

Help? There's no undo, I didn't have all text selected in the note...nothing! All gone! Still shows the last creation date of 10/2/2013.

EDIT: Tried looking around and found [https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/61570](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/61570). 

What a dangerous bug. I'm not out of disk space -- 17.3 GiB free.

---

### Post by grier-devon on 2013-11-22
> **Mk32 said:**
> I put my laptop to sleep today and when I come back, a note that was not in active window or in edit/view mode had all of its text replaced by ...

/

and that was it. I found the .note backups in ~/.local/share/tomboy, but not the one I had! It's two blasted Welcome to Tomboy and some other note I deleted long ago. 

Help? There's no undo, I didn't have all text selected in the note...nothing! All gone! Still shows the last creation date of 10/2/2013.

EDIT: Tried looking around and found [https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/61570](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/61570). 

What a dangerous bug. I'm not out of disk space -- 17.3 GiB free.

Only 17.3 GB free? Your pretty close to that 100% usage. See if you can clear up some additional space and then see is it wipes out any other notes you create, just could be that bug. I don't really use Tomboy notes but is there a way to save your notes? Did you save them and where unable to recover them? If there is a way to save them and you didn't you should be anyway cause what if the system doesn't unlock correctly when you come back to it? Everything gets lost anyway.

---

### Post by Mk32 on 2013-11-22
It's a 25GiB partition. =/ 17.3GiB isn't even close to full. 

Tomboy Notes is not the same thing as gnome-applet thingy. 

Didn't save them. They weren't high priority but I guess they are now :)

---

### Post by tgalati4 on 2013-11-22
I stopped using Tomboy because of it's note-losing ability.  I'm not sure if it is a mono thing or some bugs that cause note wipes under certain conditions.  I use *zim* instead, and it seems to be more stable.  Plus, it's easier to back up the zim notebook file than a bunch of hidden Tomboy files.

---

### Post by Mk32 on 2013-12-04
Back when I used a Mac mini for my daily driver, I learned to not use Stickies. It's basically the same thing as Sticky Notes except it dates back to System 7.5 I think. You can back up the StickiesDatabase file which is in the System Folder (or somewhere in the /Library/Preferences folder in OS X IIRC) but I found it simply easier to create a .rtf notes file and toss it in the Dock. For my system I put the link in the menu bar. 

The benefits in OS X was that it was easier to remember it when it was migration time. For Linux, the same thing applies, plus gedit has a nice undo and autosave features. (I tried putting gedit on my iMac G4, I got a shock of a lifetime re: 150MiB installation, and in the end it didn't work anyways. Sad because it reminds me a lot of Notepad++ on Windows, which is **great** for editing HTML by hand, which I do frequently.)

Anyways yes, warning to those out there - Do not trust Sticky Notes with anything. Tomboy also has issues. Just use a text file.

---

### Post by Habitual on 2013-12-04
zim-wiki never lost anything!

---

