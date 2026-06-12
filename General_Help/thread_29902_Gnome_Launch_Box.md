---
title: "Gnome Launch Box"
date: 2005-04-26
forum: General Help
---

### Post by jcooper on 2005-04-26
Does anyone know if the patches / packages listed on the site are required on Ubuntu? I'm not too happy patching gnome menus unless I absolutely have to! It appears the [patch has been committed](http://bugzilla.gnome.org/show_bug.cgi?id=163470), but I dont know if its in 2.10?

Has anyone else installed this utility?

[Gnome Launch Box](http://micke.hallendal.net/gnome-launch-box/)

---

### Post by kkvenkit on 2005-04-28
I installed it from the universe repository (off-hand) and it works great.  

Check out [http://ubuntuforums.org/showthread.php?t=18740&highlight=gnome-launch-box](http://ubuntuforums.org/showthread.php?t=18740&highlight=gnome-launch-box) for info on how to bind the program to a key-press (ie, press F7 to have the program started) -- very useful.

---

### Post by wowtip on 2005-05-08
I also got it working from 'universe', sort of...

It starts up allright, but then as soon as I type anything, one letter appear and either the program hangs (requiring ctrl+alt+f1 and kill -9) or quits immediately with the following output:

```

...@GreboGuru:~$ gnome-launch-box

** ERROR **: file lb-bookmark-list.c: line 92 (html_startElement): assertion failed: (parser->current_bookmark == NULL)
aborting...
Aborted

```

Any ideas what might be the problem?

---

### Post by geoffDeGeoffGeoff on 2005-06-17
I installed it from universe.
When I run it from command line a box appears then it crashes my computer and I need to do a hard reboot.
Help, I want quicksilver on my ubuntu pc!!

---

### Post by willrea on 2005-06-17
Geoff, try pressing ctrl +esc and it should quit the program. I'm having the same problem

---

### Post by cillian on 2006-03-20
I installed from svn revision 450 and everything worked excellently for ages (and beautifully with transparency enabled). I've been installing updates as usual on my Breezy box but nothing exciting that I can think of and now all of a sudden after typing one letter it crashes with:
** ERROR **: file lb-bookmark-list.c: line 92 (html_startElement): assertion failed: (parser->current_bookmark == NULL)
aborting...

Just after I had acquired a dependancy on it too ... I tried make clean, and reinstalling it. I tried moving ~/.gnome-launch-box.myuser to see if it would make a new one ... it didn't ... and most weirdly even as root it tells me that ~/.gnome-launch-box.myuser is beyond my permissions even though it's owned by myuser ...

:cry: I need my launch box

Edit
I did an strace on it and saw that it was crashing when it read my bookmarks in firefox! I didn't know it did that!
Anyways I had recently added some bookmarklets (for simpy.com since de.lirio.us is on it's last legs) and that's when it stopped working. I removed the bookmarklets and I've got the launch box again! Yay!\\:D/ 

I've filed a bug report so maybe we'll have a fix in svn soon. 
(I'd nearly prefer a proper simpy firefox extension)

---

### Post by davidsiegel on 2007-10-10
Check out [GNOME Do.]("http://launchpad.net/gc") Unlike GNOME Launch Box, GNOME Do is under active development.

[ATTACH]45900[/ATTACH]

---

