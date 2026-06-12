---
title: "kjournald won't let my drive spin down"
date: 2005-09-06
forum: General Help
---

### Post by xx404 on 2005-09-06
I'm trying to get my noisy drive to shut up so I've set a drive spin down but every time it starts to spin down it immediately spins up again. I've issued the following commands and it appears that kjournald is the culprit. How do I prevent it from constantly messing with my drive?

echo 1 > /proc/sys/vm/block_dump
dmesg

---

### Post by atoponce on 2006-11-09
I am having the same problem.  Every day, many times a day, kjournald is going nuts.  It lasts for about 2 minutes.

I am running a web, mail, mysql, jabber and ssh server on the box, and it's under heavy load is it is.  I don't need kjournald slowing it down even more.  Is there a way to tweak kjournald?  What is it exactly anyway?

Thanks.

---

### Post by atoponce on 2006-11-10
I think that I have determined that Postfix may be causing the heavy read/write on the HDD, but I am not 100% sure.  Can anyone confirm?  When I start Postfix, it's not long, but kjournald begins doing it's thing.  And does it quite frequently throughout the day.  If Postfix is stopped, I only hear it once a day at around 7:30am.

If anyone could confirm Postfix causing the issue, it would be appreciated.

Thanks.

---

### Post by makadam on 2006-11-23
Hello atoponce

I observed the same occurrence as you atoponce.
I have a Toshiba Tecra 8000 Laptop that i used as a server with DHCP, DNS, Apache, MySQL, PHP and Mailserver (Courier, Postfix). When Postfix is down the noise emission is quite low, else every minute the HD spins up and down. I tried to find some configuration settings for postfix but i haven´t any chance so I hope somebody else has already experience with this issue.

---

