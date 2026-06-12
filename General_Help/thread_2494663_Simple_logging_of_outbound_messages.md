---
title: "Simple logging of outbound messages"
date: 2024-01-23
forum: General Help
---

### Post by macbluehusky on 2024-01-23
Occasionally my server gets an abuse notification about an outbound message to a remote site.  The notification lists the receiving site and the message type.  I have scanned my site for rootkit malware and it seems pretty clean.  I suspect there is a bogus user out there among the many users and it is allowing a external source to logon and send the abuse message.  What I would like to do is to log all outbound traffic with something like iptables or other simple logging app, and to be able to identify on the log message the logon of the user who generated the message.  Is the user ID available on iptables or is there another better solution?

---

### Post by TheFu on 2024-01-23
If you don't trust anything about the server, start over.  Get a new VPS and install everything there fresh, migration the data over and get that down really well, since you'll be hardening the new server before you ever switch to it.

"pretty clean" isn't sufficient.  You need to 100% know it isn't compromised.  The best tool I know for that is to have automatic, daily, versioned, backups. With those you can compare files that should change against what is actually on the system.  If a new subdirectory shows up and you didn't create it, then you know you've been hacked and need to wipe and start over.  There is no 100% certain way to "clean" a system once it is compromised.  That's a desktop Windows thing, not a Unix thing.

---

### Post by macbluehusky on 2024-01-24
Yeah I had figured as much but was hoping to get a glimpse as to what is happening first, before going to a new server.  The outbound spam happens only once in a while, so I am looking into best way to diagnose with logging of outbound traffic.

---

### Post by TheFu on 2024-01-24
> **macbluehusky said:**
> Yeah I had figured as much but was hoping to get a glimpse as to what is happening first, before going to a new server.  The outbound spam happens only once in a while, so I am looking into best way to diagnose with logging of outbound traffic.

If you have an MTA setup, why not look at the logs for that?  It would be odd NOT to have an MTA on a Unix-like OS that sends email.

Also, you can setup your MTA to block outbound messages using all sorts of rules. Hopefully, the system isn't an open relay. There are MTA testing sites that will check your MTA for security issues.

---

### Post by SeijiSensei on 2024-01-24
/var/log/mail.log should show every incoming and outgoing message. Just find the one that was sent to the site that filed the abuse report.

---

