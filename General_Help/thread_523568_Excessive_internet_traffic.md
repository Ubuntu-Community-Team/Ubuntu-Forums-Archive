---
title: "Excessive internet traffic"
date: 2007-08-12
forum: General Help
---

### Post by toobmany on 2007-08-12
Hi all.  I've been using Dapper Drake for some time now but can't reconcile the amount of internet traffic.  We don't download video or music but even so our daily use is about 25M download and more concerning about 5M upload when the only outgoing traffic is email without attachments.  My ISP suggests there could be an email worm at work even though I'm running ClamAV and Firestarter; or there could be bit torrent working in the background even though I've never enabled it.  I also keep the system updated.  Any advice would be appreciated, bearing in mind please I've got limited programming skills.  But I love Ubuntu.

Computers are like air-conditioners, they stop working when you open windows.

Peter

---

### Post by hikaricore on 2007-08-12
My guess would be that the update manager could be to blame.  Occasionally a process that the update manager is a front end for (i can't remember the exact name as I'm not using Gnome) checks the ubuntu repositories for system updates.  Each time it does this it connects to multiple servers and downloads package lists if they have changed.  Depending on the number of extra sources you have in your sources.list file, this traffic can grow to quite a reasonable size.

Like I said this is just a guess, atleast something to start with.

You may want to think of any other programs or Gnome-Panel applets you have running.

Email checkers.
Stock tickers.
Weather checkers.
And other things of this nature periodically download data to update their information.

p.s.  You won't (very very unlikely) be getting any email worms in Ubuntu/Linux because windows viruses don't work on Linux.

---

### Post by Warren Watts on 2007-08-12
> **hikaricore said:**
> You won't (very very unlikely) be getting any email worms in Ubuntu/Linux because windows viruses don't work on Linux.

If you happened to have an unsecured email server running on your machine, spammers might me hijacking your mail server....?

Here is a link to a free tool that will check a mail server for open relay:
[URL="http://www.abuse.net/relay.html"]
http://www.abuse.net/relay.html[/URL]

---

### Post by toobmany on 2007-08-12
Thanks, Warren.  I'm registering now.  Should my answer to "Address to test:
(as host name or dotted quad)" be "mail.bigpond.com"?  That's how it appears in the server settings in T/bird

Peter

---

### Post by Warren Watts on 2007-08-12
Sorry for the delay in answering... It was 4:30 in the morning last night when I responded to your thread, and I went to bed...

Just use your IP as the address to scan.  Not your private LAN IP; use the IP you get from your ISP.

---

### Post by ramjet_1953 on 2007-08-13
If you are operating via a wireless network, a neighbor may be piggy-backing onto you wireless router.

Regards,
Roger 8)

---

### Post by toobmany on 2007-08-14
> **toobmany said:**
> Thanks, Warren.  I'm registering now.  Should my answer to "Address to test:
(as host name or dotted quad)" be "mail.bigpond.com"?  That's how it appears in the server settings in T/bird

Peter
Warren, thanks for the tip, according to the test it appears there is an unsecured email server running.  now i just need to discover how to shutit down.  Abuse.net doesn't seem to have the answer, could you point me in the right direction?

---

