---
title: "Optimiszing Boot Time"
date: 2007-05-29
forum: General Help
---

### Post by tehhaxorr on 2007-05-29
Having slow boots on my Inspiron 6400. It's a Core 2 machine, should be much snappier. Waiting 1.5 mins + for the damn thing to start up.

Running 7.04. What are some things i can do to increase boot time? I was going to compile another kernel bare bones style but first i was going to try and remove all nonessential services and startup applications.

What are some apps that can go?
What else can i do to improve startup time?

Cheers, Mark

---

### Post by hessiess on 2007-05-29
1.5 mins isant that bad!

ubuntu 1 min "ish"
windows 10+ min

---

### Post by Paul38 on 2007-05-29
I am new here. I was thinking to try Ubuntu instead of Windows XP , assuming that Ubuntu would boot more quickly than XP (this is very important for me). After I configured my XP to boot as quick as possible, my good old Dell dimension XPSB takes now less than 45 secunds to boot (measured from powerON till I get my internet startpage on Internet explorer 6).

Is it possible to boot Ubuntu in less than 40 sec.?

I have also two other simple questions:

When running XP and doing plain internet surfing CPU load is only about 10%. It is a PIII 1GHz.
How will it be with Ubuntu ???
Is Ubuntu always running with the same CPU load?

What about XP's hibernate way of powering down. Do you also have it with Ubuntu ???
How is boot time then ?
;)

---

### Post by TheMono on 2007-05-29
Core 2 Duo @ 2.5Ghz gives me a time of less than 30 seconds.

Try Here: [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

One of the big ones is the concurrency tip, and also to profile your boot. But do the concurrency change BEFORE you profile.

---

### Post by PhatStreet on 2007-05-29
> **hessiess said:**
> 1.5 mins isant that bad!

ubuntu 1 min "ish"
windows 10+ min
I have an XP machine that boots in under a minute, and it's practically run-of-the-mill.

But yeah, concurrent booting and profiling your boot will speed it up a bit.

---

### Post by kuja on 2007-05-29
Some optimizations: 

- Disable anything you don't need running at startup
- Use static IP addresses instead of DHCP if possible
- disabling usplash will also shave a couple seconds off

To see the results of your monkeying, install a package called boochart and then reboot. It will create a png image that it keeps in /var/log/bootchart/. 

I think at one point I had my boot time down to 18s with my system ;)

---

### Post by Dod_basim on 2007-06-01
> **kuja said:**
> Some optimizations: 

- Disable anything you don't need running at startup
- Use static IP addresses instead of DHCP if possible
- disabling usplash will also shave a couple seconds off

To see the results of your monkeying, install a package called boochart and then reboot. It will create a png image that it keeps in /var/log/bootchart/. 

I think at one point I had my boot time down to 18s with my system ;)

 how do i know what is needed at startup? how to disable it?

---

### Post by tehhaxorr on 2007-06-17
I switched to open Suse 10.2 and my system is ready in 20 seconds from Grub.

That's quick.

---

