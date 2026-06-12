---
title: "SSD and Swap"
date: 2012-12-19
forum: General Help
---

### Post by Elitenoname on 2012-12-19
I have read a few things about SSD and ubuntu / linux, they say you should not use a swap space. I was wondering if anyone is using a SSD and if this is true, everything seems to be working. and if you do need / use a swap space is it better to have in on the SSD or another hard drive? my setup is a 60GB SSD (OS install) and a 2TB sata drive where i keep all my data.

---

### Post by Pjotr123 on 2012-12-19
Check this:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

That should help. :)

---

### Post by haqking on 2012-12-19
Create a partition on your data drive and use that for swap if possible.

it is preferable over creating a swap partition on a SSD

---

### Post by Elitenoname on 2012-12-19
alright thanks for that helped out

---

### Post by 1clue on 2012-12-19
IMO you should max your RAM out, or at least get up to 8g or so.  Then swap becomes irrelevant.

I use an SSD with 12g.  I also have a spinning disk which has swap on it, because I use tmpfs extensively and it's there just in case, and because I hibernate, but it has never been used as traditional swap.

---

### Post by TenPlus1 on 2012-12-19
My system has a 120gb Sandisk SSD with 20gb for '/' and the remainder for '/home'...  No swap partition is setup and /tmp is assigned to memory via tmpfs...  Everything works fast and fine on my 2gb memory net-top pc...

---

### Post by Grenage on 2012-12-19
Indeed, max out the RAM where possible.  I can't recall using swap recently, but if I was going to, I'd probably put it on the SSD.

I view SSDs as work tools to be ruined and abused for my benefit, not molly coddled and pampered.

---

### Post by Merrattic on 2012-12-19
+1 what TenPlus1 said but with 4gb of RAM, no problems even when under heavy load (video editing etc) and with a Crucial M4 SSD.

---

### Post by 1clue on 2012-12-19
Historically speaking, swap was developed because RAM was outrageously expensive and computing requirements were greater than the capability of the chip makers to make memory that customers could afford.

That premise is now ridiculously untrue.  Memory is incredibly cheap, especially if you satisfy yourself with middle-of-the-road instead of the fastest thing you can get.

If you understand how swap works, you'll realize that one of the best speed enhancements you can make is to upgrade memory on a machine which actually uses swap to a capacity which no longer uses it, or uses it rarely.

There is no longer any reason why a regular computer user needs swap in the traditional sense, but clever as we are we've come up with all sorts of alternative uses for it that make sense so it can't really be eradicated yet for normal desktop/laptop use.

---

### Post by rnerwein on 2012-12-19
> **1clue said:**
> IMO you should max your RAM out, or at least get up to 8g or so.  Then swap becomes irrelevant.

I use an SSD with 12g.  I also have a spinning disk which has swap on it, because I use tmpfs extensively and it's there just in case, and because I hibernate, but it has never been used as traditional swap.
by the way i saw 64gb (high end server sun) swaping. there for say never irrelevant. it's a matter of the kind of using your box - playing or working
cheers

---

### Post by 1clue on 2012-12-19
Ya, I've seen that sort of thing too, but I think we can be fairly safe in assuming that a new user asking this sort of question is not using high end server hardware.

I guess I didn't qualify my statements, but I assumed an average desktop system for my recommendations.

---

