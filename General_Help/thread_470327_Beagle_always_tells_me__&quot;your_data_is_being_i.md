---
title: "Beagle always tells me:  &quot;your data is being indexed&quot;"
date: 2007-06-10
forum: General Help
---

### Post by Blofeld on 2007-06-10
Hi, I'm using Beagle (desktop search) v0.2.16.3 and whenever I open it, it tells me that "your data is being indexed".  I mean that warning never goes away.  Is that normal?  Should I leave the Beagle window open for a while so that Beagle can finally FINISH indexing my data?
Not a big problem, I'm just a bit confused.  Thanks.

---

### Post by Ek0nomik on 2007-06-11
It takes Beagle a bit to index all your data.  How many folders do you have Beagle indexing?

I personally told Beagle to index only folders where I knew I would want to search for things (some key highly used folders).  I left it on over night, and let it do its thing.

Preferences/Search & Indexing has some options for Beagle as well.

---

### Post by brownknight on 2007-06-11
it is normal. you dont need to have the window open. beagle indexes from the background.

---

### Post by Ek0nomik on 2007-06-11
> **brownknight said:**
> it is normal. you dont need to have the window open. beagle indexes from the background.

It eats up a decent amount of resources though I believe.  Indexing is a pretty hard task.

---

### Post by Blofeld on 2007-06-11
@Ek0:  about 25 GbiByte.  The thing that bothers me is that this "your data is being indexed" warning never goes away.

---

### Post by Ek0nomik on 2007-06-11
> **Blofeld said:**
> @Ek0:  about 25 GbiByte.  The thing that bothers me is that this "your data is being indexed" warning never goes away.

How long have you had it run?

---

### Post by Blofeld on 2007-06-12
I've had Beagle installed ever since Xubuntu 7.04 came out, and I've had the window open all night.  And basically, nothing happens, I don't hear the hard disk drive working and I don't have the impression that Beagle is actually indexing.

---

### Post by dedmonds on 2007-06-26
[FONT="Microsoft Sans Serif"]I am experiencing the same problem on my system, and I have had Beagle installed for more than 2 months. I did not have this problem initially, but I now have the same symptoms on both my laptop and my desktop at home.[/FONT]

---

### Post by dedmonds on 2007-07-03
[FONT="Microsoft Sans Serif"]Beagle seems to be working for me now. I removed the Beagle package and re-installed it after deleting the .beagle directory from my home directory.

-duane[/FONT]

---

### Post by Blofeld on 2007-08-08
Thanks for the feedback, Duane, I'll give it a shot!

---

### Post by Blofeld on 2007-08-09
It worked!
Also the old ~/.beagle folder had grown to over 2 GB in size (!), the new folder is now just a couple of MBs.
:lolflag:

---

### Post by Blofeld on 2007-08-09
... and growing!  This morning it was 4 MB, now it's already 11 MB.

---

