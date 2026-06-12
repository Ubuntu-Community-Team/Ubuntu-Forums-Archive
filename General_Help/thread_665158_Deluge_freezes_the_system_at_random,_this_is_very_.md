---
title: "Deluge freezes the system at random, this is very frustrating"
date: 2008-01-11
forum: General Help
---

### Post by 449 on 2008-01-11
Whenever Deluge is running there is a good change I'm going to get the blinking light of death. It will randomly freeze up my whole system completely on the stop and the caps lock and scroll lock lights blink simultaneously. It didn't used to happen so frequently, but now it's at the point where I can't even use Deluge without this happening. What's going on? I appreciate any help you guys can give me here. 

Thanks everyone.

---

### Post by disturbed1 on 2008-01-12
A few more details ;)

How many torrents are you uploading/downloading? 
Some system specs (CPU/RAM)?
Any programs running besides deluge? Not anything like mencoder running in the background, with avidemux, audacious and firefox's 52 youtube tabs open with a make -j4 running in the background while you're hammering away on Enemy Territory? :D
Are these same programs running everytime deluge locks the system? Could be appA+appB+deluge=crash?
What version of deluge are you running?

---

### Post by 449 on 2008-01-12
Pentium 4 3.0GHZ
512MB RAM
Intel Graphics Media Accelerator 900
250GB ex HDD
no internal

It just started freezing by its self now. But most of the time the more programs open the more likely it is to happen. But a lot of the time it's completely random. I'm running Deluge 0.5.4.1. Right now I have two downloading, and 32 seeding,but even when I pause them it still freezes. 

[IMG]http://img300.imageshack.us/img300/2459/screenshot1oo2.png[/IMG]
I'm not entirely sure on the details, hopes this helps.

---

### Post by disturbed1 on 2008-01-12
32!!!!!!!!!!!!!!!! Take about 30 of those out and see what happens ;)

You're low on the ram :( If your HD has an access light, keep an eye on it to see if it's thrashing about once deluge is loaded.

Downloading 1 linux iso torrent, and seeding 4 linux iso torrents, it's only taking up ~35mb of real RAM (132MB of virtual). As long as your apps stay low RAM usuage as in the pic, you'll be ok. After awhile FireFox swallows the RAM, I'm upto 143mb now.

Upgrade deluge to a more current version. A .deb for Ubuntu is available at their website [http://deluge-torrent.org/](http://deluge-torrent.org/) it should of popped up that an update was available, mine did.

---

### Post by 449 on 2008-01-12
> **disturbed1 said:**
> 32!!!!!!!!!!!!!!!! Take about 30 of those out and see what happens ;)

You're low on the ram :( If your HD has an access light, keep an eye on it to see if it's thrashing about once deluge is loaded.

Downloading 1 linux iso torrent, and seeding 4 linux iso torrents, it's only taking up ~35mb of real RAM (132MB of virtual). As long as your apps stay low RAM usuage as in the pic, you'll be ok. After awhile FireFox swallows the RAM, I'm upto 143mb now.

Upgrade deluge to a more current version. A .deb for Ubuntu is available at their website [http://deluge-torrent.org/](http://deluge-torrent.org/) it should of popped up that an update was available, mine did.

I did everything you said and it still froze again.

---

### Post by AstarothCY on 2008-01-12
Same problem here. I'm beginning to fear data loss.

Deluge will freeze your system with a clean install of deluge with no torrents at all. As long as you load up any one torrent, it will freeze completely. No mouse control, total system freeze.

I'm dropping it. Any recommendations? (not azureus, too heavy)



EDIT: Never mind. Install the .deb from the Deluge website.

[http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

The one on the Gutsy repos is a really old version. I hope they update it.

---

### Post by AstarothCY on 2008-01-13
Never mind, new version crashes as well. a bit more randomly, but it does crash in exactly the same way.

Fix it please, it's dangerous.

---

### Post by 449 on 2008-01-13
> **AstarothCY said:**
> Never mind, new version crashes as well. a bit more randomly, but it does crash in exactly the same way.

Fix it please, it's dangerous.

Agreed.

---

### Post by disturbed1 on 2008-01-13
I just don't have the same issue :( But, I usually don't have any more than 3-4 torrents at a time.

You could try
Azureus [http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php)
Opera [http://www.opera.com/download/linux/](http://www.opera.com/download/linux/)
Or any of the clients in synaptic.

---

### Post by yoasif on 2008-01-13
Use Ktorrent, by far the best torrent client, and far far better than deluge.

---

### Post by 449 on 2008-01-13
> **yoasif said:**
> Use Ktorrent, by far the best torrent client, and far far better than deluge.

I will disagree from experience and preference. And I still get freezes in Ktorrent.

---

### Post by slayer^_^ on 2008-01-19
i didn't understand why deluge had that so terrible freeze trouble, then i noticed it happened only with a torrent that had something like 2000 peer sources and 1000 seed sources.

i thought that **putting the maximum connection attempts for second to 25** (surely not -1) would have solved the problem and it did.

i experienced no more freezings and deluge works great!

you can try to raise that number of connections till you experience crashes, but i suggest to keep that value, because perhaps the freezings are influenced by the total amount of sources of your torrents.

hope it helps!

---

### Post by mechgt on 2008-05-11
Could it be that it's a network driver issue? The following bug report proposes that it may be a networking problem, and it's seems to apply to many torrent clients. Some suggest that running ndiswrapper with a Windows driver may solve the problem.

[https://bugs.launchpad.net/ubuntu/+s...on/+bug/211026](https://bugs.launchpad.net/ubuntu/+s...on/+bug/211026)

I now have the freeze issue with Hardy 8.04 and Deluge.

This (below) also leads me to believe that it could be network drivers + torrent:
I recently upgraded to Hardy, and at first had no issues. Deluge ran just fine, the same as it had always run on Gutsy. I then took a disk image and moved it to a new server (all new hardware, including new network card). Everything appears to run fine, until I start Deluge, and the system will freeze within minutes of me starting it.

I have another network card on the server, I'm going to try it and see if that changes anything.

---

### Post by mechgt on 2008-05-14
Now after switching to the new card, and having run with it for a few days, I have no problems to report.  I'm running the same version of Deluge as before (0.5.8.9) and running on this network card, and opposed to the on-board NIC no more system freezes.  

It appears that this is in fact somehow related to the network card.

---

