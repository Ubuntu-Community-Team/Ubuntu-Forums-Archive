---
title: "get_buddy error in eog"
date: 2013-06-28
forum: General Help
---

### Post by Paresh on 2013-06-28
Anyone else getting this problem with eog?

I am running Ubuntu 13.04 (64 bit)

When you double click a jpeg, eog loads and then closes immediately without displaying the jpeg file.  So I decided to try it from the terminal and got this:

```
paresh@desktop:~$ eog '/home/paresh/Desktop/V14.png' 
eog: /build/buildd/cairo-1.12.14/src/cairo-mempool.c:160: get_buddy: Assertion `offset + (1 << bits) <= pool->num_blocks' failed.
Aborted (core dumped)

```

The image is a scanned image from the scangui app, but I get this on most images I try.  Although I do get a successful load as well on the same image, it's about 50/50 as to whether it fails or not, so I can't pin down anything more specific.  I have no problem loading the image in gimp or any other app.

I don't have a clue how to proceed from here.

Paresh

---

### Post by ajgreeny on 2013-06-28
So, is it a jpeg or a png that gives you this problem?  You start saying jpeg, then show a command for eog with a png.

---

### Post by Paresh on 2013-09-05
It happens on both jpeg and png.  but it does not happen every time, even with the same image file

---

