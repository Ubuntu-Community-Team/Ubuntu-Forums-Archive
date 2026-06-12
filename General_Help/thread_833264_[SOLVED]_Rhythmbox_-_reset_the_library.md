---
title: "[SOLVED] Rhythmbox - reset the library"
date: 2008-06-18
forum: General Help
---

### Post by martinrandau on 2008-06-18
I have a big music collection (around 100gb) which always has worked well with rhythmbox. 

Recently though, I tried to reset the library as some songs (located on an external hd, linked to from inside the /home/martin/Music folder) were showing double (I checked details and they were the same files). What I did was that I changed the library to an empty folder, waited for rhythmbox to say that I have 0 songs, and then went back to the music folder and waited for rhythmbox to recollect the songs. To my great confusion, each song now shows 3 times!

I want to know a way, through deleting a settings files etc, to reset the all of rhythmbox's memory. I want it to be completely unaware of that there is music in /home/martin/Music, so that when I add that folder to the library the songs will be singular.

---

### Post by lizzard on 2008-06-18
I'm not sure, but I think removing ~/gnome2/rhythmbox/rhythmdb.xml should reset the music collection.

---

### Post by martinrandau on 2008-06-18
Thank you, that seems to have worked! Salute!

---

### Post by juar1 on 2010-01-30
Update: now the file is located on ~/.local/share/rhythmbox/rhythmdb.xml in Karmic Koala (9.10)

---

### Post by 666f6f on 2010-03-14
um.. why do they keep moving (the configuration files/directories).. :-k

---

### Post by krismatth3 on 2010-05-01
> **666f6f said:**
> um.. why do they keep moving (the configuration files/directories).. :-k

 I agree, stop changing things for the sake of changing them. In 10.04, this file is now located at ~/.local/share/rythmbox. Argh!

---

### Post by chudder on 2010-06-27
> **krismatth3 said:**
> I agree, stop changing things for the sake of changing them. In 10.04, this file is now located at ~/.local/share/rythmbox. Argh!

worked for me!  Thanks

---

### Post by texaswriter on 2011-10-09
Still good a year later!!

---

### Post by V4hid.ir on 2012-07-06
> **juar1 said:**
> Update: now the file is located on ~/.local/share/rhythmbox/rhythmdb.xml in Karmic Koala (9.10)

Where is this file in ubuntu 12.014 ??!

---

### Post by plucky on 2012-07-06
> **V4hid.ir said:**
> Where is this file in ubuntu 12.014 ??!

Still in the same place.

Open Nautilus (file Manager) and select **View > Show Hidden Files** and navigate to rhythmdb.xml in your ~/.local/share/rhythmbox/ directory.

Any file with a . at the front is a hidden file.

Good Luck

---

### Post by treii28 on 2013-02-20
> **V4hid.ir said:**
> Where is this file in ubuntu 12.014 ??!

Same question - where is it now? It appears to have moved again. no rhythmbox (or anything else starting with an 'r') anywhere in ~/.local/share on my box

---

### Post by wildmanne39 on 2013-02-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

