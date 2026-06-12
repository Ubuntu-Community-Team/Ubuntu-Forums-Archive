---
title: "Download limit."
date: 2007-12-31
forum: General Help
---

### Post by isurf on 2007-12-31
Hi,

I'm new to Ubuntu, and would like to have a following control in my system.
My Internet connection is limited (monthly data transfer). I would like to limit daily download to 50 MB per day, including all the data transfers. Once the limit is reached on a specific day, the complete access to the Internet should be blocked. there shouldn't be any further data transfer occurring from the computer including those happens in the background. I googled a lot for this and could not find a single solution for this.
So, if any of you can help me, that would be of great help to me.
Any help is much appreciated and thanks in advance.

---

### Post by LaRoza on 2007-12-31
I don't think Ubuntu will download anything without your say so.

When you install something through Synaptic (command line, Add/Remove, etc) it tells you the size before and waits for permission to continue. 

The Updates are also like that, you can make sure by going to System->Administration->Software Sources to configure behavior and when it checks.

---

### Post by erginemr on 2007-12-31
Hello,

My connection is limited as well (4 GB/month). I don't know if there is any program in Linux that will keep track of data transfer, but out ISP provides a service that lists the amount of monthly transfer via a web page and I regularly check that page not to exceed my monthly limit. 

You may contact your ISP to learn whether they provide a similar web service.

---

### Post by isurf on 2007-12-31
Thanks for all your comments.

However, the problem is that I find it hard to keep visiting my ISP's stats page for that. Moreover, if I/any guest happen to use a major part of the allotted limit then I would be left with out access for the entire month. I am thinking of a programs which monitor the total data trasnfer through a particular network device (eth) and once when the set limit for that day/week comes it should alert me and at the same time should have an option to stop all access till I authorise. Unfortunately, it's not only me using my computer, and those who use do not have much knowledge abt internet as in case if they spent an hour on Youtube, they might end up using the monthly quota. I found a similar software for windows like NetLimiter, tried to download it but can't get into their homepage. 

Will this (Netlimiter) work with WINE? Anyone please help me otherwise I would have to move to XP back which I hate to do after using Ubuntu (:smile:)

---

### Post by lisati on 2007-12-31
> **erginemr said:**
> Hello,

My connection is limited as well (4 GB/month). I don't know if there is any program in Linux that will keep track of data transfer, but out ISP provides a service that lists the amount of monthly transfer via a web page and I regularly check that page not to exceed my monthly limit. 

You may contact your ISP to learn whether they provide a similar web service.

As well as a "Chcek my account" page, the ISP I use offers an optional  service which automatically sends you an email when you've used something like 80% of your monthly allowance. 

Perhaps some suitably knowledgable  programmer out there can put there mind to coming up with a program that automatically monitors traffic. Monitoring one particular machine shouldn't be too hard - perhaps through the Linux equivalent of monitoring the ports in Windows. However, it might be confounded by trying to monitor routers and other such gizmos between your network and the ISP.

Cheers, and good luck.

---

