---
title: "Rsync Remote Backup Service Suggestions"
date: 2007-02-02
forum: General Help
---

### Post by ShawnCollins on 2007-02-02
Hi,

I just started using Ubuntu as my primary home computer and was wondering about online backup options.  I used XDrive for my windows machine, but it was horribly unreliable and I don&#8217;t think it supports Linux.  I&#8217;ve gathered from other posts on this forum that the best backup option for my home directory is probably to setup a cron job to run something like RSYNC.  

I am wondering if anyone has any experience with online services that support rsync.  I did a little research and came across rsync.net and exavault.com .  I like Exavault for the price, but am wondering what other things I should look for with a provider and if rsync is a good way to go.

Thanks for all your help!

-Shawn

---

### Post by jpeddicord on 2007-02-02
Rsync is a very good program for transferring files, especially since it only stores what has changed since the last sync. As for a host, I personally use DreamHost and store my private files in an off-site directory, but you probably don't want a web host now, do you?

I say just pick the site that gives you the most GB/dollar. Google the site, and see some reviews first before buying.

---

### Post by ShawnCollins on 2007-02-03
jacobmp92,

Thank you for the quick response.  I never considered the web-hosting option - that's definitely something to consider (how is the reliability?).  In the meantime, I'll probably go with exavault.com since the GB/$ is better.

Thank you again.

-Shawn

---

### Post by jtc on 2007-02-15
> **ShawnCollins said:**
> I am wondering if anyone has any experience with online services that support rsync.  I did a little research and came across rsync.net and exavault.com .  I like Exavault for the price, but am wondering what other things I should look for with a provider and if rsync is a good way to go
Myself I've been using rsync.net since about a month back, and I must say I'm very satisfied. They seem to have stable servers, good connections, etc. What really impresses me thought is their support.You always get quick and helpful answers from people who without a doubt know what they are talking about.

---

### Post by shane2peru on 2007-02-21
> **jacobmp92 said:**
> Rsync is a very good program for transferring files, especially since it only stores what has changed since the last sync. As for a host, I personally use DreamHost and store my private files in an off-site directory, but you probably don't want a web host now, do you?

I say just pick the site that gives you the most GB/dollar. Google the site, and see some reviews first before buying.

I looked at using rsync to backup my web site to my computer, however I couldn't figure out how to do it.  It should be the same as backing up to your web host only switching the destination for the source.  Can you give me an example of your rsync line to backup to your web site so I can figure it out.  Obviously you will need to replace any sensitive info with some generic info.  Thanks.

Shane

---

