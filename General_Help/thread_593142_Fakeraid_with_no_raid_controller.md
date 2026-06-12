---
title: "Fakeraid with no raid controller?"
date: 2007-10-26
forum: General Help
---

### Post by trxDraxon on 2007-10-26
Was wondering if it was possible to setup a basica software raid with 2 IDE drives without a raid controller?

I have an older machine that I have a 40gig SATA drive and 2 80gig IDE drives.  I wanted to put swap and / on the 40gig and the software stripe the 2 80's and mount /home on it.  Ive read a ton of the fakeraid howtos but non seem to talk about setting one up with no raid controller.

Any help woudl be appreciated.

---

### Post by Tanker Bob on 2007-10-26
Absolutely. I set my RAID1 up with the alternate install CD for gutsy. I have fakeraid support on my motherboard, but it proved more of a hinderence so I disabled it. The key tool for setting up and monitoring software raids is mdadm. I'm not sure how to set up one without reinstalling from scratch from the alternate CD, but there probably is a way that you can find through a good web search. The howto that I used is at [http://www.iki.fi/kuparine/comp/ubuntu/en/raid.html](http://www.iki.fi/kuparine/comp/ubuntu/en/raid.html). ubuntu's built-in RAID software is excellent, supporting RAID 0, 1, and 5. No special hardware needed.

---

### Post by trxDraxon on 2007-10-26
Hrm...I just took a look at the link you posted and I am using the alternate Cd but I dont get the option for software raid during the install.   I was wondering if it wasn't giving me the option because i don't have a controller.

EDIT:  I see where I screwed up, think I got it now.

---

### Post by trxDraxon on 2007-10-26
Yeah it worked this time.  In the partitioner I forgot to change the USE AS option to software raid.  Installing now =D

---

### Post by Tanker Bob on 2007-10-26
Great, I'm glad it worked for you. The CD makes it easy and it works very well so far. I boot off of my RAID1 array without an issue.

---

