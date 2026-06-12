---
title: "Can't restore my bookmarks to a new system"
date: 2014-02-01
forum: General Help
---

### Post by Extreedoc on 2014-02-01
Old system;10.04, new system: 12.04.
Backed up my bookmarks etc and the file is there on my new system. When I try to "Restore" the file I get: "Unable to process the backup file". Is there anything I can do or am I stuffed?

---

### Post by PotatoHead007 on 2014-02-01
You might just be stuffed :/
Ubuntu 12.04 is built differently to 10.04, if i am correct. So it just might be that you can't restore the file, because it's different. I guess you can try opening the backup and copying files. 
It would help if i knew what bookmarks you are talking about. Firefox, Chrome, or Folders? So yea, not sure if you can back that up.

---

### Post by ajgreeny on 2014-02-01
The hidden **.mozilla** or **~/.config/chromium** folder in your home for the browser (we are talking web-browser or file manager here?) should be transferable from old to new system easily, and that would include your bookmarks and everything else.

If it's your file manager bookmarks, they are in a file **/home/***user***/.gtk-bookmarks** which again should transfer from machine to machine.

Incidentally, what file type is the bookmarks backup file you have?

---

### Post by Extreedoc on 2014-02-01
Thanks both, details: I made a backup of my bookmarks from Firefox, it's a .json file. So... am I stuffed or what? Don't feel sorry for me, I'm used to it!

---

### Post by PotatoHead007 on 2014-02-01
Uum, well, do you only want the bookmarks or do you want the whole folder? Because the way i always do it(dirty way) is just copy and replace :P
Also, the build for firefox changed quite a lot(assuming you just did regular updates on 10.04), and the folders and file names have changed. Have you checked that you are using the same/very similar firefox versions? That might just be the issue.

PS i do feel sorry for you :) I know what it feels like to lose all the firefox bookmarks that have accumilated over the years :P

---

### Post by Extreedoc on 2014-02-01
> **PotatoHead007 said:**
> Uum, well, do you only want the bookmarks or do you want the whole folder? Because the way i always do it(dirty way) is just copy and replace :P
Also, the build for firefox changed quite a lot(assuming you just did regular updates on 10.04), and the folders and file names have changed. Have you checked that you are using the same/very similar firefox versions? That might just be the issue.

PS i do feel sorry for you :) I know what it feels like to lose all the firefox bookmarks that have accumilated over the years :P

I think you might be right, I'll have to do it the hard way or forget it and build up a new collection, pity, there were hundreds of the things... I'm beginning to feel sorry for myself now. :(  Thanks anyway. ;)

---

### Post by ajgreeny on 2014-02-02
If you have a .json file it should still be possible to import in using the bookmarks manager in your system (bookmarks ->show all bookmarks ->import and backup).

You could also open the .json file with a text editor and by a simple search for **"http** you could find all the web-addresses it contains; better than nothing, thouigh I still do not see why the .json file can not simply be imported.

---

