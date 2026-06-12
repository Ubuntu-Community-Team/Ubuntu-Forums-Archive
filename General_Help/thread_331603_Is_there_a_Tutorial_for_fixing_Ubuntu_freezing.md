---
title: "Is there a Tutorial for fixing Ubuntu freezing?"
date: 2007-01-04
forum: General Help
---

### Post by Dmole on 2007-01-04
**Is there a Tutorial for fixing Ubuntu freezing?**](*,)

---

### Post by meng on 2007-01-04
What freezing?

---

### Post by nsabatino on 2007-01-04
> **meng said:**
> What freezing?

Maybe someone should first point him to a Forum Posting tutorial?

---

### Post by druhboruch on 2007-01-04
Are you sure you are not writing about other popular OS?

---

### Post by meng on 2007-01-04
I think he/she has lost interest. I know I have.

---

### Post by Dmole on 2007-01-04
well as amusing as your posts are there not helpful to me.

if you want some background before answering my question
My Xubuntu 6.06 gets unresponsive after a few days without attention.
The logs don't point to anything there's just a gap the size of the crash period, a few days.
unresponsive meaning black screen and the num lock key is unresponsive.

yes i googled around and searched the forms to no avail
so i'm asking for guidance.

---

### Post by meng on 2007-01-04
> **Dmole said:**
> well as amusing as your posts are there not helpful to me.
Dmole: I'm not sure what you expected in response to your initial post. Perhaps you should read it again from the perspective of someone who is NOT familiar with your problem.

Now, to your great credit (NO sarcasm! quite genuine) you have followed up with a post that explains in more detail the problem you have. Now and only now can someone perhaps help you. Unfortunately, that someone is not me because I'm not familiar with that problem. If your follow-up post had been submitted as your original post, it is possible that a solution may have been offered by now.

Well, enough reprimanding :D I hope things work out for you. Just do yourself a favor in future and help us to help you.

---

### Post by Dmole on 2007-01-04
sorry i thought my question was simple
perhaps i should have used the term hanging as a synonym to freezing.
I'm surprised that no one has written a tutorial on how to find out what is making Ubuntu hang. a "20 question" type of thing.
there must be some 'last executed command log' or crash-dump or some method of elimination possibilities without waiting weeks for it to get symptomatic and hang.

---

### Post by meng on 2007-01-04
Well even though I'm probably ignorant of the nature of this problem, I'll pitch in some (lame) ideas:
Is this a desktop or notebook? (I assume it's a desktop, not many folks leave their notebook running that long!!) What are your power management settings? Do you have lots of spare hard drive space?

The thing is, that Linux in general, and Ubuntu specifically, is renowned for tolerating very long uptimes (server OR desktop) so I'm puzzled as to why you're experiencing problems. My GNOME/Ubuntu is on continuously for weeks at a time (interrupted only for restarts as recommended by certain system updates).

---

### Post by druhboruch on 2007-01-04
Dmole,
I have 2 servers running edgy 24/7 for last 39 days:  Zimbra and MythTV backend.

Faulty hardware may be responsible for your troubles.  
I would start troubleshooting with running memtest, then I would scan disks for errors and finally replace power supply or CPU fan.

---

### Post by Dmole on 2007-01-04
thanks for the ideas it is an old system.  :)

so basically your suggesting that Ubuntu won't handle hardware with character.
but i doubt windows 2003 is more flexible in this respect, and it has no qualms with the machine.

I also get hangs on my newish laptop running 6.10 but while I'm using it. one of the problems was the auto complete in the firefox search bar.
but my laptop is less important, the point is that i suspect software more than hardware in the case of my desktop.

i'll still swap some components and run some diagnostics on the hardware but there must be some help for software. i have seen other people on the threads reporting Ubuntu hangs.

I'm still looking for a hang diagnosing tutorial.
maybe i'll learn enough to make one :)

[edit]
ps.
power management settings= everything on all the time (i think this would be symptomatic in the first few days at least if it were a problem)
40GB Free hard drive space on "/" more on other mounts
[/edit]

---

### Post by Dmole on 2007-01-05
still looking for a hang diagnosing tutorial...](*,)

---

### Post by Dmole on 2008-01-08
never found that tool or tutorial but I did find that the problem was between bittorrent applications(Azureus or rtorrent) and the file system drivers, Hope that helps someone. if it happens to you try changing the fs of your downloading partition.. don't remember the fs. also that little compatibility check box in Azureus had no effect.






here are some logs that did not help with the problem:

#=> /var/log/messages : General log messages
#=> /var/log/boot : System boot log
#=> /var/log/debug : Debugging log messages
#=> /var/log/auth.log : User login and authentication logs
#=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file
#=> /var/log/dmesg : Linux kernel ring buffer log
#=> /var/log/dpkg.log : All binary package log includes package installation and other information
#=> /var/log/faillog : User failed login log file
#=> /var/log/kern.log : Kernel log file
#=> /var/log/lpr.log : Printer log file
#=> /var/log/mail.* : All mail server message log files
#=> /var/log/mysql.* : MySQL server log file
#=> /var/log/user.log : All userlevel logs
#=> /var/log/xorg.0.log : X.org log file
#=> /var/log/apache2/* : Apache web server log files directory
#=> /var/log/lighttpd/* : Lighttpd web server log files directory
#=> /var/log/fsck/* : fsck command log
#=> /var/log/apport.log : Application crash report / log file

:)

---

