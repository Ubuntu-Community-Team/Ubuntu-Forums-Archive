---
title: "Proxy type solution, meter bandwidth and record url history?"
date: 2014-01-21
forum: General Help
---

### Post by doctorzeus2 on 2014-01-21
I'm looking for a simple (Proxy?) type package/solution to load on 13.04 server.  It's configured with two NICS/IPs.   It will receive multiple inbound requests (browsers configured to use the proxy) on the one IP, and then go out/back to the Internet on the second one.  

Requirements:
[LIST]
[*]enable username/password or some type of authentication; block anonymous no user/pass connects
[*]logging of the following attributes-
[LIST]
[*]URLS with date/time stamps
[*]bandwidth usage (not sure what's the typical way to collect this- very detailed would be nice but overall usage chart over xYZ periods is fine too)
[/LIST]

[*]Meter and throttle bandwidth usage, i.e. limit 192.168.1.2 to !> 10Mbps;  not a "requirement" but nice to have built in would be flexible control of enable/disable access, i.e. after 10PM no access for IP xyz, or better ONLY ALLOW access for IP xyz.. etc.
[/LIST]

Anything out there simple like this?  I glanced at squid and that seems like way overkill, probably has what I need though.  But I'm thinking there's probably something a lot more streamlined and simple that would foot the bill.  Thanks in advance..and wish me luck on sorting out this ubuntu-one trainwreck and getting my original account back.

---

### Post by SeijiSensei on 2014-01-22
Squid really would be the best solution for all of this.  It supports authentication and access controls by user.  It logs every object requested including client IP, URL, object size, elapsed time, and other characteristics.  There are also report generation tools like [slarg](http://sourceforge.net/projects/slarg/) that will let you monitor bandwidth usage and destinations by requesting IP.  I'm not sure if Squid can throttle.  It can be configured to use different access controls at different times of day.

If you're looking for something to use in an organizational setting, it's worth investing the time to learn Squid.  If you're looking for something to use at home, you might consider [Dan's Guardian]("http://dansguardian.org/").

---

