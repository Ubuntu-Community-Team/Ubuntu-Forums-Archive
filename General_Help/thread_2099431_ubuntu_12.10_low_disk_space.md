---
title: "ubuntu 12.10 low disk space"
date: 2012-12-29
forum: General Help
---

### Post by hunterkasy on 2012-12-29
I was gone away from the computer for 2 days and now I am getting low disk space warnings, had over 40gigs of free space now only 2gigs are free

---

### Post by dcottingham on 2012-12-29
I guess the first thing to do is figure out where the space has gone.

Here's a line I find useful for investigating this kind of question:

cd /
du -k | sort -n

This gives you a list of all the directories on your system. Each directory has next to it the size, in kilobytes, of all the files in the directory and all subdirectories. They are sorted to put the biggest numbers at the end of the list.

So you should be able to look at that list and immediately see where 38 Gb disappeared to.

---

### Post by sanderj on 2012-12-29
or the GUI way:

press Super key, type "disk usage" and proceed ...

---

### Post by hunterkasy on 2012-12-29
> **sanderj said:**
> or the GUI way:

press Super key, type "disk usage" and proceed ...

it shows the home folder using up the most space, but it don't show what in the home folder using up the space

---

### Post by sanderj on 2012-12-29
... click on it ...

---

### Post by hunterkasy on 2012-12-29
> **sanderj said:**
> ... click on it ...

it shows my name using 100% and thats about it that is using any amount of space

I included a screen shot

---

### Post by sanderj on 2012-12-29
my guess is that everyting is in your home directory itself. So open Nautilus and check your home directory itself. Probably a lot of (hidden?) files, or one big file.

---

### Post by hunterkasy on 2012-12-29
> **sanderj said:**
> my guess is that everyting is in your home directory itself. So open Nautilus and check your home directory itself. Probably a lot of (hidden?) files, or one big file.

I went through my entire home folder with showing hiddens files the name of the file below is 43gig big

.xsession-errors.old

---

### Post by sanderj on 2012-12-30
OK. So ... you deleted it and have your disk space back?

---

