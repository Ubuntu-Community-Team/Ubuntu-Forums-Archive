---
title: "RAID HowTo?"
date: 2007-12-04
forum: General Help
---

### Post by jabagawee on 2007-12-04
Special circumstances, but then again, don't we all have them?

I'm going to be building a home server with a main 80GB drive and two 750/1000GB drives. I'm not too sure if I'll be getting the 750s or the tetrabytes. / (root) will be on the 80GB for no particular reason. The two extras will be RAID-1'ed at /media/dump. /media/dump will be a Samba share for everyone to see. When I want to upgrade to RAID-5, I know I'm going to have big problems. Can someone help me get all this straight? First, a tutorial on how to do RAID in the first place. I've never found a concise enough answer on Google. Next, I need to know how to do the expansion of the RAID array when time comes along. 

[http://www.economysizegeek.com/2006/07/15/migrate-raid1-to-raid5-and-grow/](http://www.economysizegeek.com/2006/07/15/migrate-raid1-to-raid5-and-grow/)

I've found that, but my n00bish Linux skills serve only to confound me. I'm not even sure if this information is relevant. Help?

---

### Post by erickramirez on 2007-12-04
There's a great post in the "Tutorials & Tips" forum by kragen and is available at [http://ubuntuforums.org/showthread.php?t=408461]("http://ubuntuforums.org/showthread.php?t=408461").

Cheers,
Erick Ramirez
Melbourne, Australia

---

### Post by bodhi.zazen on 2007-12-04
That is an awesome post.

The wiki has some information also :

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[https://help.ubuntu.com/community/RaidConfigurationHowto](https://help.ubuntu.com/community/RaidConfigurationHowto)

---

### Post by jabagawee on 2007-12-05
Thanks for the help. However, I will be sticking fully with a software RAID, as opposed to a fakeRAID. Does anyone have any clear concise instructions on how to perform the RAID-1 to RAID-5 migration I detailed?

---

### Post by njparton on 2007-12-05
If you can afford it, buy a 3ware card with 4 or more ports :wink:

Raid 1 to 5 migration can be done by the card itself. Avoid software raid by an OS or software raid card - I've had plenty of problems with these in the past.

---

### Post by jabagawee on 2007-12-05
Avoid software RAID? But it's Linux....

:P Fine, 3ware it is.

Edit:  Anyone know of a cheaper RAID controller card with RAID-1-to-5 migration? 3ware sounds prohibitively expensive.

---

### Post by njparton on 2007-12-06
Try getting a used one on ebay.

Otherwise if you're storing precious data it's worth the investment in my book.

---

