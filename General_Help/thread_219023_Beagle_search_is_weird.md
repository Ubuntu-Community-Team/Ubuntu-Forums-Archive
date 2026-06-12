---
title: "Beagle search is weird"
date: 2006-07-19
forum: General Help
---

### Post by Hanj on 2006-07-19
I've always had a feeling that Beagle search isn't behaving as it should, with some files not being indexed properly. I've done searches where files that I know exist weren't found. 
I tried to examine this more closely and found this strange thing:
I created a folder called "my_test_folder" in my home directory and searched for it. If I searched for "my_t" Beagle found it, but when I tried "my_te" it didn't find it! "my_tes" didn't give any results either, but when searching for "my_test" Beagle found the folder again. Similar things seem to happen with a lot of files.
Am I missing something vital here or is it a bug?

---

### Post by Hanj on 2006-07-20
*Bump*
Isn't this happening to anyone else? I've tried Beagle on two different machines, and I've had problems on both.

---

### Post by steve.horsley on 2006-07-20
Sorry, but it's not happening to me. 
English UK locale setting in Dapper.

---

### Post by reclusivemonkey on 2006-07-20
> **Hanj said:**
> *Bump*
Isn't this happening to anyone else? I've tried Beagle on two different machines, and I've had problems on both.

Yeah same here. Beagle is *very* erratic. I use /home/ftp to store pretty much everything media-wise; music, photos, movies, etc. I have added /home/ftp to Beagle in the hope that I can search it but it doesn't find anything in there at all. I have

```

export BEAGLE_EXERCISE_THE_DOG=1

```

but to no avail. It seems to like searching Liferea, and my Evolution Calendar (sync'd to Google Calendar) but other than that its not good at much else. It will find some items in my Gaim log but not others, and as for searching for files folders, I may as well have an empty hard drive. I suspect that you need to do something to build an index, but I've tried the console and the website and there are no clear instructions on how to do this. There are also many unanswered posts on the forums about it to, so I am sure Beagle needs some work/love yet...

---

### Post by yopnono on 2006-07-21
Yep I have the same issue with beagle. That's why I don't use it, it's no good to me. The gnome search is much better from that point of view.

---

### Post by Hanj on 2006-07-21
Ok, nice to hear I'm not alone then :)
It still seems really strange to me though. If a file is indexed, how hard can it be to test whether the search string is part of the file name? It's just one line of code in all programming languages I know of...

Well, I hope Beagle gets that extra love it needs. It would be such a nice tool if it worked a little better.

---

### Post by Bo Rosén on 2006-07-21
I used it on Hoary and it was pretty good there, but now on Dapper it's just not very useable. Pity, I really like it.

Isn't beagle the Big Thing (tm) in SLES 10?

---

