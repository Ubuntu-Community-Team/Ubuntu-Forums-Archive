---
title: "strange Evolution problem sending email"
date: 2014-11-11
forum: General Help
---

### Post by angeloQ on 2014-11-11
Hi all, joined the forum in 2007, this is my first post!

Anyway, I've got a strange problem with Evolution and one particular email account.

If I try to send an email from a particular account, Evolution gives me the error message : "The reported error was "RCPT TO <name@domain> failed: "JunkMail rejected - host86-169-86-150.range86-169.btcentralplus.com ([192.168.1.150]) [86.169.86.150]:41784 is in an RBL, see
http://www.spamhaus.org/query/bl?ip=86.169.86.150"".

The strange thing is that other email clients (thunderbird and geary) can send from that account without any problems.  My laptop, running the same OS and email client, does not have this problem.

I've tried rebooting my modem/router to try to get a different IP address, but that didn't work.

Evolution has no problem sending from another email account.

I like the features of Evolution and want to carry on using it as my daily email client, but this problem is getting in the way!

I'm running Ubuntu gnome 14.04.01 inside virtual box, win 7x64 host.

Thanks in advance,

Angelo

---

### Post by buzzingrobot on 2014-11-11
I don't have a solution, but Spamhaus is widely used to block spammers.  It's done by IP addresses, rather than domain name. I suspect they've listed an IP used by your ISP.  I don't know why Evolution hits the block, and Geary and Thunderbird do not.

You might contact the ISP  about this.  Other customers are likely seeing it, too.

---

