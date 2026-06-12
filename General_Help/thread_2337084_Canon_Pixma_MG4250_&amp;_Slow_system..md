---
title: "Canon Pixma MG4250 &amp; Slow system."
date: 2016-09-14
forum: General Help
---

### Post by mcsonic on 2016-09-14
In a very senior moment (I am actually over 60, which fact I'll shamelessly use as an excuse throughout) I've upgraded straight from Ubuntu 12.04 to 16.04 LTS. 

I know, I know... 

OK, so having realised this, I'm now expecting all manner of bad stuff to happen. What seems to be happening so far is:

1. It's taking a wee bit longer to start up.

2. It won't print to my Canon Pixma MG4250 - although each attempted job comes up as completed. My W10-running laptop prints perfectly via wired/wireless/SD card etc. And Ubuntu 12.04 printed okay before the upgrade apart from some colour issues.

I'm hoping someone on here can tell me whether these kinks are just the tip of an iceberg, the enemy within, an accident waiting to happen, etc. etc. 

I'm also hoping someone can tell me should I/ can I fix this, with a clean install or something like that?

Thanks in advance. I'll now go and interfere with something I can't easily screw up so easily. Like a lawnmower or a chainsaw.

MM

---

### Post by mastablasta on 2016-09-14
> **mcsonic said:**
> 
1. It's taking a wee bit longer to start up.
that is quite possible a normal reaction. depending on your hardware system specs. 

```
dmesg
``` command in terminal would reveal what is happening during boot. you can see if anything is taking Quite long time or spewing out errors.

> 
2. It won't print to my Canon Pixma MG4250 - although each attempted job comes up as completed. My W10-running laptop prints perfectly via wired/wireless/SD card etc. And Ubuntu 12.04 printed okay before the upgrade apart from some colour issues.



if it used some proprietary driver to print (and i think some Cannons do), then you will need to reinstall it.

e.g.:
[SIZE=2]http://robert.penz.name/532/a-howto-for-using-a-canon-pixma-mg4250-under-ubuntu/
[/SIZE]
[SIZE=2]https://foxrafi.wordpress.com/2014/12/04/install-canon-pixma-mg4250-on-ubuntu-12-04-3-lts/

When this one get's broken and you cna't fix it anymore, replace it with HP or Samsung (now also to be HP). compatible with Linux out of the box.
There are a few others out there with good Linux support ("Brother" i believe).
[/SIZE]

---

### Post by mcsonic on 2016-09-14
Thanks, really helpful. 

Can I just return to that question of whether it's advisable or even worthwhile to do a clean install of 16.04? 

Cheers, MM

---

### Post by Geoffrey_Arndt on 2016-09-14
Probably a better end result after a clean install.   However, the down side is you have to save off all the data you want to keep, reinstall _some of the programs_ you had, and re-install the printer drivers (Canon's are not as user friendly to Linux users as are HP (#1) and Epson (#2) and even Brother (#3)).   Best not to skip over LTS's, and then do upgrades - - although it can be done if one has a "Vanilla" (clean) system and disables all non official repos such as PPA's.

---

### Post by mcsonic on 2016-09-14
Thanks Geoffrey. Might just do that.

---

### Post by dragonfly41 on 2016-09-14
Before going to the extreme of a reinstall .. first check out your print jobs ... 

[http://localhost:631/admin](http://localhost:631/admin)

there might be some job in the job queue which needs unblocking.

---

### Post by mcsonic on 2016-09-14
Yeah dragonfly41, that's the thing: I've cancelled every print job that didn't print. Won't even do a test print.

---

### Post by mcsonic on 2016-09-14
And now I'm thinking "did I upgrade straight from 12.04 to 16.04? " Can you actually do that? 

What I did was respond to a message in the updater saying a new Ubuntu version was available. A seamless/troublefree process ensued and that was that.

Sorry to be this much of a noob, but there you have it: I don't actually remember what version I was running before the upgrade. 

(Is that something I can check somehow?)

So many questions. All stupid.

Thanks, folks. MM

---

### Post by mastablasta on 2016-09-15
> **mcsonic said:**
> And now I'm thinking "did I upgrade straight from 12.04 to 16.04? " Can you actually do that? 



not really. it should go from 12.04 to 14.04 and then to 16.04.

the issue i likely the driver (which you will need to reisntall anyway, if you do the clean install). so you might as well remove it now and try to reinstall it. if it all works then you are good to go i believe. except for the slowness on boot, which at this point it is hard to say what is causing it.


backup all the necessary data, note down or write down the programs you are using before performing a clean reinstall (if you go that way).

---

### Post by col48 on 2016-12-01
-> mcsonic

I note that on the Canon website, the Linux driver for the MG4250 is advertised as supporting Ubuntu 12.04 - no mention of anything later.
My 4250 worked fine on 12.04, like yours, and now I have 16.04 dual boot with 12.04.

On 16.04 (after installing the same driver), colours come out wrong (eg oranges are much darker than they should be).  Otherwise, simplex (ie single-sided) printing is OK but duplex (double-sided) manages to push page 1 up the page so that the header is lost and sometimes the first part of the text is lost or distorted - the footer is correspondingly high up the page as well (the second page is OK).  This problem still shows itself if you tell it to print a 3-page doc in the order 3,1,2 - page 1 looks bad.  I think the first page printed (page 3 in that case) is also bad, but I can't remember for sure. [I am a senior citizen too!]

I am wondering if there is a workaround, for which I plan to start a fresh thread if I can't find enlightenment beforehand.

---

