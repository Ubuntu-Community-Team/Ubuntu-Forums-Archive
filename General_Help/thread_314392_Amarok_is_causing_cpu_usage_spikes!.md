---
title: "Amarok is causing cpu usage spikes!"
date: 2006-12-07
forum: General Help
---

### Post by theseeker on 2006-12-07
Well, I'm using Amarok for a long time now, it's one of the best software linux has in my opinion. Recently, I did a clean install of Edgy. Anyway, whenever I'm using Amarok it seems like it is causing instant cpu usage spikes to 100%. At first I wasn't running the system monitor, but noticed some lagging when I was scrolling down web pages, again for a moment. I became being annoyed by the fact, so I decided to watch the system monitor for some time, it was then that I saw those "spikes" popping on a regular basis (once a minute maybe).

I didn't find any other similar experiences from my google searches, so if anyone has a clue why this is happening and maybe a solution, please post it!

Thanks!

---

### Post by theseeker on 2006-12-07
I forgot to mention that I'm using Amarok v. 1.4.3, which is the default at the ubuntu repos.

---

### Post by ntetreau on 2006-12-08
Hi theseeker, 
I had the same problem as you and I fixed it my upgrading to 1.4.4 which is in the kubuntu repositories.

Just add this to your /etc/apt/sources.list

deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main

then

sudo apt-get update 
sudo apt-get upgrade
sudo apt-get install amarok

For some reason though, amarok would not start after install and I had to delete my tune database this way:

rm ~/.kde/share/apps/amarok/collection.db

Now my cpu stays cool when I'm playing my tunes with amarok!

Good luck!

Nic

---

### Post by eeclark on 2007-01-03
I am hesitant to use this fix my my 100% cpu usage issue with Amarok since I am running feisty.

Running Amarok version 1.4.4 (Build Date Dec 6 2006) and KDE 3.5.5 Libs on Ubuntu.

Any other hints for a Feisty user?

---

### Post by ntetreau on 2007-01-10
Well, I guess there is a small chance that my problems were caused by the databse itself, and therefore would have been fixed when I deleted it.  You could move it elsewhere and give it a try!

Nic

---

### Post by DougieFresh4U on 2007-01-10
I think amarok is great, but the cpu spikes have been a concern for a few months for me and I have tried suggested fixes (upgrade amarok) and still get spikes. I wish there was a simple answer as I can not use amarok while doing other things on my machine. Just thought I would let you know your not alone on this one  :(

---

### Post by alphablue52 on 2007-03-10
I had this problem some time ago and discovered, that Amarok tried to scan my music directory and repeated on the last few percent again and again.
It was due to some special characters in file names and/or tags (for me, it has been some german "ä, ö, ü, ß").
Strange, because Ubuntu uses utf-8 in general, but I often have such problems (e.g. german man pages shown in konqueror still won't work correctly). But it helped to rename these music files.

Just yesterday, Amarok had no cpu usage peaks, but didn't want to play "Blue Öyster Cult - Don't Fear The Reaper". I just changed the interpret in the ID3 tag to "Blue Oeyster Cult", and Amarok worked.

I have no clue if this is a general Amarok bug, but it seeems to me that most KDE developers actually fix just security bugs and work on KDE4 versions. Hopefully, KDE 4 will be fully utf-8 compilant.

---

