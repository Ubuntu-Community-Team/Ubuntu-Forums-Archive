---
title: "get-iplayer problem started yesterday"
date: 2016-04-05
forum: General Help
---

### Post by grey1beard on 2016-04-05
I've been using get-iplayer for several years with no major problems, up until yesterday evening.

I normally copy and paste the iplayer url I want into Terminal i.e.**get-iplayer  [http://www.bbc.co.uk/iplayer/episode/b076r0sr](http://www.bbc.co.uk/iplayer/episode/b076r0sr)**

Tried again this morning to download 'The Vikings Uncovered' and Terminal put up a message *"ERROR: Failed to get version pid metadata from iplayer site"*
Tried again with the whole url, but no go.
Tried a different programme, but got the same response.

Used sudo apt-get update etc, but I have the latest version of get-iplayer.

Grateful for any help.



John

ps Still using 12.04 because I like it !

---

### Post by slickymaster on 2016-04-05
Have you tried with```
get_iplayer --get http://www.bbc.co.uk/iplayer/episode/b076r0sr
```

---

### Post by grey1beard on 2016-04-05
Thanks for the quick reply.
I copied that into terminal but got the same response.
I have now noticedthat in an earlier line terminal states 
[I]WARNING: rdf URL contained no data
WARNING: PID URL contained no RDF data. Trying to record PID directly.[/I]

I don't know if this is of any extra significance.
John

---

### Post by slickymaster on 2016-04-05
Can you please post back the output from```
apt-cache policy get-iplayer
```

---

### Post by grey1beard on 2016-04-05
Result - 

get-iplayer:
  Installed: 2.94-2-g52a2c12-ppa23p4~precise
  Candidate: 2.94-2-g52a2c12-ppa23p4~precise
  Version table:
 *** 2.94-2-g52a2c12-ppa23p4~precise 0
        500 [http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu/](http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
     2.80-1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

John

---

### Post by slickymaster on 2016-04-05
I notice that you're using the PPA version for >= Wily.

Have you tried to downgrade the PPA version for Precise: [https://launchpad.net/ubuntu/precise/+source/get-iplayer](https://launchpad.net/ubuntu/precise/+source/get-iplayer)

---

### Post by grey1beard on 2016-04-05
No, I haven't tried that.
Could you post instructions, or do I just follow your link ?
Many thanks
John

---

### Post by howefield on 2016-04-05
Might be worth holding off for a little while before you go down that route. :)

If your current installation was working till yesterday, it may not be your machine at fault.

---

### Post by grey1beard on 2016-04-05
Hi howefield,
I never think it's the machine that's at fault. I always assume it's an operator error ;)

Many thanks
John

---

### Post by slickymaster on 2016-04-05
> **howefield said:**
> Might be worth holding off for a little while before you go down that route. :)

If your current installation was working till yesterday, it may not be your machine at fault.

Fair point, howefield. Just wondering if the PPA version for Precise wouldn't be the most appropriate one.

---

### Post by howefield on 2016-04-05
> **grey1beard said:**
> I never think it's the machine that's at fault. I always assume it's an operator error ;)

Hehe, in this case, I feel it isn't likely to be user error :)

---

### Post by grey1beard on 2016-04-05
Just tried a little experiment.
The Geldorf programme on Yeats is on a different BBC channel, and has been up for a couple of days, but the end result was exactly the same.
I can draw no conclusion for the moment.

Can any one else download this successfully ?

---

### Post by slickymaster on 2016-04-05
Can you please try one last thing to see if it will work```
get_iplayer --pid b076r0sr --tvmode=best
```

---

### Post by grey1beard on 2016-04-05
Heads up

I tried to search using *get-iplayer geldorf yeats* and it failed to download the programme schedule from any BBC channel !

---

### Post by grey1beard on 2016-04-05
Got the following result -
                       $ get_iplayer --pid b076r0sr --tvmode=best
get_iplayer 2.94-2-g52a2c12-ppa23p4, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

WARNING: rdf URL contained no data
WARNING: PID URL contained no RDF data. Trying to record PID directly.
INFO: Trying pid: b076r0sr using type: tv
INFO: Trying to stream pid using type tv
INFO: pid not found in tv cache
Matches:

INFO: 1 Matching Programmes
WARNING: Could not download programme metadata from [http://www.bbc.co.uk/programmes/b076r0sr.xml](http://www.bbc.co.uk/programmes/b076r0sr.xml)
ERROR: Failed to get version pid metadata from iplayer site

---

### Post by howefield on 2016-04-05
You really are wasting your time (probably).

Have a browse through the get_iplayer forums and you'll find your answer :)

---

### Post by slickymaster on 2016-04-05
What about```
get_iplayer --pid b076r0sr --playlist-metadata
```

---

### Post by grey1beard on 2016-04-05
I'm going to mark this as solved, even though it's not !!!
Seems to be out of my hands.

Regards all,
John

---

### Post by ajgreeny on 2016-04-05
The same problem here with the schedules unavailable refusing to show any of the TV channels, though radio is still working fine to get schedules but not to get the audio.

Here's why.
[https://squarepenguin.co.uk/forums/announcement-7.html](https://squarepenguin.co.uk/forums/announcement-7.html)

---

### Post by ajgreeny on 2016-04-05
Back up and running again according to the get-iplayer forum.

---

### Post by howefield on 2016-04-05
> **ajgreeny said:**
> Here's why.
[https://squarepenguin.co.uk/forums/announcement-7.html](https://squarepenguin.co.uk/forums/announcement-7.html)

Announcement appears to have been deleted.

> **ajgreeny said:**
> Back up and running again according to the get-iplayer forum.

Yep, it is.

---

### Post by grey1beard on 2016-04-05
Yes, I can confirm that, for the moment at least, we are downloading again.
However, it's nice to now know of alternative routes ;)

John

---

