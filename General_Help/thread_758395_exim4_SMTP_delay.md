---
title: "exim4 SMTP delay"
date: 2008-04-18
forum: General Help
---

### Post by jcison on 2008-04-18
I can usually figure my way around a problem eventually, but this time, I'm absolutely stumped.

I've got Ubuntu 6.04 with exim4 running as the mail daemon.  (I have it configured with TLS and SASL per [https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4) and SpamAssassin per [http://koivi.com/exim4-config/](http://koivi.com/exim4-config/), though I experienced the issue I'm about to describe even before I configured TLS.)

When I connect with my client to send mail on the same network as my server, it hangs around 10-15 seconds with "Connected to [server]," then goes through the whole login and send steps in milliseconds.

When I connect from a different network, there's no hang whatsoever.  It goes through the connect, login, and send steps immediately.

I keep digging through the config files but can't find anything.  The various sys logs say nothing about a delay or error, so I can't figure out where something is going wrong.  Anyone have any suggestions?  I would appreciate it greatly!

Let me know if you need any other info from me.

---

### Post by jcison on 2008-04-22
All fixed.  It appears to have been an ident delay.

In case anyone else is experiencing the same problem and stumbles upon this thread, I just dropped the ident delay from the default of 30 seconds by adding the following lines:

rfc1413_hosts = *
rfc1413_query_timeout = 2s

I went with two seconds, obviously.  I use a split-config and a local conf file located at /etc/exim4/conf.d/mail/00_local, so that's where I added the lines.

---

### Post by dcstar on 2008-04-23
> **jcison said:**
> All fixed.  It appears to have been an ident delay.

In case anyone else is experiencing the same problem and stumbles upon this thread, I just dropped the ident delay from the default of 30 seconds by adding the following lines:

rfc1413_hosts = *
rfc1413_query_timeout = 2s

I went with two seconds, obviously.  I use a split-config and a local conf file located at /etc/exim4/conf.d/mail/00_local, so that's where I added the lines.

To verify that mail sources are valid, things like reverse DNS lookups are common these days (using the RFC 1413 method).

If you do not have your local environment set up correctly to satisfy the same criteria that correctly set up external connections do, then you can experience delays.

This delay seems so be one of those "gluepot" protections that won't reject a possibly spam connection outright, but slow it down enough to thwart the spammer's attempt at a quick connection.

The real solution is to fix your internal environment so it can recognise internal connections, not reduce the spam protection of your system.

---

### Post by jcison on 2008-04-23
> **dcstar said:**
> The real solution is to fix your internal environment so it can recognise internal connections

Would you by any chance know what could be configured incorrectly and causing that?  All host/dig lookups on my local IPs come back correctly and immediately.  I'm not sure how to manually perform ident lookups, though, so I can't verify what's happening with the local IPs.

Even if there is a problem there, the IPs are owned and defined by my ISP, so would that mean the ISP's host isn't responding to ident requests correctly and/or quickly enough?

---

### Post by dcstar on 2008-04-25
> **jcison said:**
> Would you by any chance know what could be configured incorrectly and causing that?  All host/dig lookups on my local IPs come back correctly and immediately.  I'm not sure how to manually perform ident lookups, though, so I can't verify what's happening with the local IPs.

Even if there is a problem there, the IPs are owned and defined by my ISP, so would that mean the ISP's host isn't responding to ident requests correctly and/or quickly enough?

You need to check whatever logs are available and see exactly what is happening - I suspect any connection from a local LAN IP has no corresponding entry in whatever DNS system your server is using, so there is a delay.

You can test this by entering local LAN ip addresses into nslookup and seeing what response you get.

You should be able to configure exim to tell it your local IP range so it doesn't bother to do any lookups.

---

### Post by jcison on 2008-04-25
> **dcstar said:**
> You need to check whatever logs are available and see exactly what is happening - I suspect any connection from a local LAN IP has no corresponding entry in whatever DNS system your server is using, so there is a delay.

You can test this by entering local LAN ip addresses into nslookup and seeing what response you get.

You should be able to configure exim to tell it your local IP range so it doesn't bother to do any lookups.

Actually, I think you're confusing DNS with ident.

As I said, DNS queries (host, dig, nslookup - pick your poison) come back correctly and immediately.

As for ident, here's some clarification on RFC 1413 (from [http://rfc.net/rfc1413.html](http://rfc.net/rfc1413.html)):

"The Identification Protocol (a.k.a., 'ident', a.k.a., 'the Ident Protocol') provides a means to determine the identity of a user of a particular TCP connection.  Given a TCP port number pair, it returns a character string which identifies the owner of that connection on the server's system."

The problem is I'm not very familiar with ident.  It appears to me that the host connecting to exim4 via SMTP would need to be running an ident daemon in order to respond to the query and identify the user making the connection.

And I *think* I just figured out the problem.  When I connect to exim4 to send mail from a remote network and exim4 tries to connect back on ident (port 113), the firewall cuts the connection immediately and exim4 continues on.  When I connect from *my* local network, though, the firewall isn't stopping port 113 and it's waiting for Windows to response on 113 and hanging until exim4's configured timeout is reached.  (I just tried telneting to 113 from all the various scenarios and confirmed that behavior.)

So, it seems the solution would be just to make sure port 113 is blocked in the firewall between my host and workstations and exim4 should give up immediately.

Is there anyone out there familiar with ident who can confirm my conclusion?

If I'm right, I'm not sure I really see much benefit to exim4 running an ident query.  What are the odds a spammer is going to have an identd process running (or at least a legitimate one)?  I suppose it could be used to help track down a problem from a legitimate server running identd, but I don't see any evidence of identd responses being recorded in the logs.  (Of course, that may simply be because few server actually run and/or allows ident queries from the outside.)

---

### Post by jcison on 2008-04-25
> **jcison said:**
> So, it seems the solution would be just to make sure port 113 is blocked in the firewall between my host and workstations and exim4 should give up immediately.

Or vice-versa.  It seems the Windows firewall already blocked 113 and was causing the connection to just hang rather than block immediately.  I created an exception to allow my server through on 113, which then causes it to close immediately (since there's no daemon there).

I did some more reading on ident and it seems the "connect back on 113" functionality I described above is accurate.  I'd still be curious if anyone has any insight on just how useful it is in regards to SMTP, though.

---

