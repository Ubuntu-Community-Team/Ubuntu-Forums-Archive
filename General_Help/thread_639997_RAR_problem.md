---
title: "RAR problem?"
date: 2007-12-13
forum: General Help
---

### Post by lDidier on 2007-12-13
ok i just Ubuntu today so im very new, anyway i got a film thats rarred into 7 parts on my pc and now how the hell do i unrar it?

i did this earlier into the terminal:

sudo apt-get install rar 

and it said it installed RAR

but when i right click the files theres no selection for rar and when i go to add it manually it doesnt really work :S how the hell can i get my file!!

---

### Post by ZipoTe on 2007-12-13
ok, you installed rar but.. how about some unrar?:lolflag:

sudo apt-get install unrar

---

### Post by lDidier on 2007-12-13
got those... but they do nothing, i cant do nothing with the files... :s

---

### Post by lDidier on 2007-12-13
look here are screenshots showing the rar and unrar.... but when i right click and extract here on any of my 7 files, they create individual folders by the same name but its empty O.o

[IMG]http://i4.photobucket.com/albums/y107/DjDids/Screenshot-bin-FileBrowser.png[/IMG]

[IMG]http://i4.photobucket.com/albums/y107/DjDids/Screenshot-bin-FileBrowser-1.png[/IMG]

WHYYYYY!!

---

### Post by zvacet on 2007-12-14
> but when i right click the files theres no selection for rar

But you have** unpack here** option.

---

### Post by mali2297 on 2007-12-14
Run the archive manager **File roller** (somewhere in the menus) and open the rar files from there.

If that doesn't work, run unrar from the terminal. Say that the files foo.part1.rar, foo.part2.rar,...,foo.part9.rar are located on your desktop, then type
```

cd ~/Desktop
unrar e foo.part1.rar

```
You should at least get an error message if it doesn't work.

---

### Post by Motorhead Kaze on 2007-12-23
Hey cool!  This will help ME.  Rock on.

---

### Post by SOULRiDER on 2007-12-23
Once this is solved please mark the thread as solved under the Thread Tools menu ont he top. Thanks!

---

### Post by Motorhead Kaze on 2007-12-23
No wait~!

First, I'm just trying to unrar a movie.  Why people rar &$^% files in the first place is beyond me.
I un-rared this file p-avpr.rar  but when trying to play it, on VLC it only shows the first part of the theme music from 2oth Century fox, the spotlights on the logo, etc., then shuts off.   Totem says, "Could not demultiplex stream".  So, is this unrared incorrectly?  Do I have to go through and unrar EVERY file?  If so, is there another command I'm missing?

Thanks!

---

