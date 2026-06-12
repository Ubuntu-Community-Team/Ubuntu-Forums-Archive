---
title: "Ubuntu 12.10 running hotter than windows 7"
date: 2013-02-10
forum: General Help
---

### Post by Seeker9 on 2013-02-10
[LEFT]Hello

[LEFT]I recently purchased an Acer Aspire V3-551G laptop, and dual booted it with Windows 7 and Ubuntu 12.10 ( with desktop environment). But, while idling on Windows 7, the heat coming out of the fans is almost non-existent, while there is a very noticeable amount of heat while using Ubuntu 12.10. I have already installed Jupiter, and put it on power saving. I am new to Ubuntu, so help will be greatly appreciated.[/LEFT]
[/LEFT]

---

### Post by Seeker9 on 2013-02-10
Anyone

---

### Post by lovevn on 2013-02-10
Hi, I used to use Ubuntu 11.04, 11.10 and now 12.04. I also installed it dualboot with windows 7. When I use windows 7, it's about under 40'C, but it's from 42 to 50, somtimes go up to 60'C ( I see it on jupiter indicator) on Ubuntu.
How about your laptop's temparature when using ubuntu? if you want it's lower, you should use Gnome classic (no effects). It's helpful. :p

---

### Post by Mark Phelps on 2013-02-10
Sorry, but there may simply be nothing else you can do.  Recent Ubuntu builds have a kernel problem that prevents the OS from throttling back the processor when idling -- causing it to run hot.  The typical "solution" (if you want to call it that) is to do what you've already done -- run Jupiter.

---

### Post by pqwoerituytrueiwoq on 2013-02-10
> **Mark Phelps said:**
> Sorry, but there may simply be nothing else you can do.  Recent Ubuntu builds have a kernel problem that prevents the OS from throttling back the processor when idling -- causing it to run hot.  The typical "solution" (if you want to call it that) is to do what you've already done -- run Jupiter.
i thought that was just a couple mainline release candidates, i have not seen any issues with the cpu governor, you can try the 3.8 kernel in the raring repo or the 3.8 mainline kernel
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/)
for a 64bit system you want all the files ending in amd64.deb and the one ending in all.deb
then install them with sudo dpkg -i /path/to/downloads/*.deb

are you using the amd driver for the GPU that will probably help the temps, look in software sources under the additional drivers tab, you may want to add the xswat ppa for the latest stable driver

---

### Post by Seeker9 on 2013-02-10
Thanks for the replies guys, I will try. Could it be that the switchable graphics are permanently on?

---

