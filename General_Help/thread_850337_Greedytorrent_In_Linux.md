---
title: "Greedytorrent In Linux"
date: 2008-07-05
forum: General Help
---

### Post by rykel on 2008-07-05
Hi,

I wonder if you have successfully used GreedyTorrent in Ubuntu Hardy?

If so, how did you configure WINE to handle that program?

Thanks.

---

### Post by mempman on 2008-07-05
> **rykel said:**
> Hi,

I wonder if you have successfully used GreedyTorrent in Ubuntu Hardy?

If so, how did you configure WINE to handle that program?

Thanks.

If u want to try that program via wine, do the following:

1. Install wine (via Synaptics)
2. Download the *.exe file for GreedyTorrent
3. Go to a terminal, and enter : 

```

wine *.exe 

```


Basically, if the program doesn't work, pay close attention to the messages you receive in the terminal window.

---

### Post by caljohnsmith on 2008-07-05
And just for future reference, you can check whether a Windows program is compatible with Wine by searching in the Wine App database: appdb.winehq.org. Of course not all Windows programs will be listed there, and that seems to include Greedy Torrent at the present moment. So whether you get it to work or not, you could submit your results to the database to help others out who are interested in that program too. :)

---

### Post by rykel on 2008-07-05
Hi,

Here is some info for you if you are interested... installing GT is a no-brainer, but running it and getting it to work with Deluge was quite an effort!

**$ wine '~/.wine/drive_c/Program Files/GreedyTorrent/GTor.exe'**

I cannot seem to cut and paste the full log here because Ubuntuforums gave me this error message... anyway, I have attached it as a .txt file.

[INDENT][B]The following errors occurred with your submission:

   1. You have included 18 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.
[/B][/INDENT]

Here is a screenshot from Deluge too... btw, is Tracker Proxy in Deluge the equivalent of Proxy Server in uTorrent? (GT website says to set localhost in uTorrent under Proxy Server)

I managed to get Deluge and GT to work together for a short while, then after that, Deluge did not seem to be able to detect the presence of GT anymore...!

---

### Post by monoufo on 2008-07-06
ooo gross.  Why would you use such a thing?  don't be a leech and seed your torrents properly.  Really big things are seeded to at least 1:1.  smaller things often get much higher than that, 2,3, maybe more.  Private tracker stuff is seeded for a long time and can reach 5 or higher before i stop them.

---

### Post by rykel on 2008-07-07
I do seed. And I do seed until ratio 5 or more often, with or without GT. (mostly without GT)

I find GT useful especially when my ratio is reset by my client (either due to technical fault, resets, accidental deletes, tracker ratio bugs etc.) and I had previously seeded beyond ratio 2.0. GT allows me to quickly climb back to where I was so that I can continue seeding.

btw I seldom use GT, I am only mainly testing it out under Wine in Ubuntu.

Oh yeah, GreedyTorrent.com has a forum where users and admins alike can discuss the merits (and demerits) of GT.

LATEST UPDATE: I am able to get GT to work by frequently starting/restarting Deluge, followed by a fresh start of GT. (I use **"wineserver -k"** before I start GT afresh everytime)

Now, GT Log View does show what it is supposed to show.... but Preferences still hang the program.

---

### Post by rykel on 2009-03-18
Hi,

I noticed that there is still no answer to the following question:

What is the equivalent of the utorrent Proxy Server in Deluge? (Deluge has Peer, Web Seed, Tracker and DHT fields under Proxy, but nothing called Proxy Server.)

Thanks for helping!

---

### Post by rykel on 2009-11-18
Hi all,

I am just glad to report that Greedytorrent now works PERFECTLY in Karmic/WINE! (see screenshot)

---

### Post by FGuin on 2010-01-22
Greedytorrent is not so great as Torrent Ratio Keeper. You should try Torrent Ratio Keeper. It allows to cheat only on needed trackers and set different settings for each tracker. You can download it [here]("http://www.torrentratiokeeper.com/forum/viewtopic.php?f=9&t=224").

---

### Post by cristianused on 2010-08-11
it worked very wheel for me in 10.4LTS :) on greedytorrent i put a port and 1mb=1,43mb upload and on deluge i put to tracker proxy localhost and at port the port i put on greedytorrent i closed thouse 2 aplications and started them bouth again. and it works very wheel wine is set as windows xp and is the last version of wine. at this hour.
i tested it to se if its working and its working.

---

