---
title: "Default Open With from Archive / File Roller"
date: 2008-06-01
forum: General Help
---

### Post by undoIT on 2008-06-01
I've tried changing the default open with program for a file extension with nautilus. I want to open all .xml files with gedit rather than firefox. The setting works in Nautilus. However, when I try to open files from the archive manager "File Roller" it always opens the file in firefox and if I right-click for open with, it always asks which program I want to use.

I'm using Hardy. In Gutsy, this wasn't a problem. After setting the default open with program, the setting would also work within archives. Is there a way that I can change the default open with program in Hardy for the archive manager?

---

### Post by aquafresh on 2008-07-26
Hi,

I have the same problem. File-Roller does not remeber the "open-with-applications".

Were you able to solve it meanwhile?

---

### Post by undoIT on 2008-07-26
Haven't solved it yet. Just yesterday I was thinking about bumping this thread :P

---

### Post by aquafresh on 2008-07-26
Seems the problem is known. There are bug reports in the ubuntu and in the gnome bugtracker. But no solution yet.

[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/132901](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/132901)
[http://bugzilla.gnome.org/show_bug.cgi?id=544766](http://bugzilla.gnome.org/show_bug.cgi?id=544766)

---

### Post by kuric on 2008-08-30
I'm having the same problem and I would like to know how to set / change File-Roller file associations.

For instance, if I double-click on a mp3 file Totem will open automatically.

But if I double-click on a mp3 through File-Roller (inside of a rar or zip file) that file will open with Banshee.

Here's another friend with a similar question:

[http://bbs.archlinux.org/viewtopic.php?id=54203](http://bbs.archlinux.org/viewtopic.php?id=54203)

No answers yet... :(

---

### Post by kuric on 2008-08-31
Ok, this is what i've discovered to solve my problem and might help you too, by analogy.

In my example, I will change the default "open with" for mp3 files.

Login as root and edit mimeinfo.cache (In openSUSE, the linux distribution I'm using right now, this file is placed on /usr/share/applications).

su
gedit /usr/share/applications/mimeinfo.cache

Search for audio/mpeg=

The first application I specify is going to be the program that File-Roller will use to open a compressed mp3 file.

Example:
audio/mpeg=totem.desktop;banshee-1.desktop;
This will open Totem...

audio/mpeg=banshee-1.desktop;totem.desktop;
This will open Banshee.

It worked with me. Good luck! :)

---

### Post by kuric on 2008-08-31
In your case, perhaps the file you need to edit is defaults.list.

So, try this:

$ su
$ gedit /usr/share/applications/defaults.list

Search for:

text/xml=MozillaFirefox.desktop

Replace to:

text/xml=gedit.desktop

---

