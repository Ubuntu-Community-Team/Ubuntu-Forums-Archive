---
title: "feisty dhcp server says : &lt;no client hardware address&gt;)"
date: 2007-04-28
forum: General Help
---

### Post by hanasaki on 2007-04-28
Since upgrading to feisty, the feisty dhcp server states following which is filing my logs.
[INDENT]<no client hardware address>)
[/INDENT]it does give out an address.  The client is also feisty.

---

### Post by gavinmc on 2007-05-10
I see this error too but on edgy.  Not clear what the cause is.

May 10 08:02:51 medlycott dhcpd: DHCPACK to xx.xx.xx.xx (<no client hardware address>) via eth0
May 10 08:02:51 medlycott dhcpd: DHCPACK to xx.xx.xx.xx (<no client hardware address>) via eth0

I'm not clear if it's a problem.

---

### Post by gavinmc on 2007-05-10
[http://www.archivesat.com/dhcp-server.isc.org/thread237578.htm](http://www.archivesat.com/dhcp-server.isc.org/thread237578.htm)

quote from that page:
------------------------------------------------------------------------------------------

strange dhcp log entry

   *** From dhcp-server -- To unsubscribe, see the end of
this message. ***

On Sun, Mar 05, 2006 at 10:15:29PM -0800, squid wrote:
> Mar  5 21:44:54 jimbo dhcpd: DHCPACK to 10.9.165.92
(<no client hardware address>) via eth2.302
> 
> ideas why its saying theres no mac address? 

Because the client did not supply one.

I bet if you look, this is in response to a DHCPINFORM.

This is a bug fixed in 3.0.4b3 (previous to 3.0.4b3, it
would log the
mac address incorrectly as "00:00:00:00:00:00"
when in fact the client
supplied a zero htype, zero hlen, and all-zero chaddr). 
There's a
factual difference between hlen = 0 and hlen = 6, chaddr =
00:00:00:00:00:00, so this is a logging bug that was fixed
in a round
of related changes.

> whats weird too is when i look in the leases file I
have a lease for that ip with a mac address

The kinds of software that are producing these packets (no
chaddr,
often no ciaddr either (on INFORM this is a protocol
violation, see
rfc2131)) are generally software that runs on Windows
machines in "user"
space (think macromedia flash) and are attempting to do
their own DHCP
in order to obtain options that way (I guess they can't get
it from
Windows' DHCP client).

So it wouldn't be unusual that you have a lease entry. 
What you're
looking at is the output of two completely different
software packages.

-- 
David W. Hankins		"If you don't do it right the first
time,
Software Engineer			you'll just have to do it again."
Internet Systems Consortium, Inc.		-- Jack T. Hankins

------------------------------------------------------------------------------------------

---

