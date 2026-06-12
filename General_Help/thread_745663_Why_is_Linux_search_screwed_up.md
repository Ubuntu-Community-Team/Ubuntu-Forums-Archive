---
title: "Why is Linux search screwed up?"
date: 2008-04-04
forum: General Help
---

### Post by twistadias on 2008-04-04
Im new to linux and though it way easy it install to ubuntu configuring my printer/scanner, webcam is a royal pain in the ***.

The various guides on the forums usually tell to to edit such and such file and that all good, but most of them do not tell you the location. Now you would think that searching these files would be easy. But its just the opposite in my case.

As you can see in the image the file 45-libsane.rules is in /etc/udev/rules.d
I have the set the location in the search to /etc/udev/rules.d but it stilll won't show the file.

[[IMG]http://img36.picoodle.com/img/img36/4/4/4/t_Screenshot1m_809b275.png[/IMG]](http://www.picoodle.com/view.php?img=/4/4/4/f_Screenshot1m_809b275.png&srv=img36)

Why do basic things like these work perfectly in windows and not in linux??

---

### Post by ed-koala on 2008-04-04
Try searching for it in Filesystem instead of the exact directory and see what happens.  I tried it on my machine for a file there and it found it just fine.

---

### Post by gsmanners on 2008-04-04
> **twistadias said:**
> Why do basic things like these work perfectly in windows and not in linux??

Using gnome-search-tool isn't something most Linux users would consider a basic thing. A lot of Linux users use Tracker, Beagle, or something low level like find, locate, or whereis.

---

### Post by twistadias on 2008-04-04
> **ed-koala said:**
> Try searching for it in Filesystem instead of the exact directory and see what happens.  I tried it on my machine for a file there and it found it just fine.

nope still doesnt show up. 

Beagle and trackers are indexing tools. I don't want to slow down my pc indexing. 
Is there any search tool that searches through all the drives like windows xp without indexing?

---

### Post by twright on 2008-04-04
i would recommend submitting a bug report at launchpad.net

tracker only indexes when you are not doing anything, it uses a negligible amount of resources

---

