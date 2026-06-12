---
title: "ISP detecting zero access trojan"
date: 2014-05-15
forum: General Help
---

### Post by tbredschneider on 2014-05-15
Hi,

I recently had my internet service suspended because my internet provider detected a zero access trojan on the network.  I'm running Ubuntu 12.04 and this is the second time it has happened.  The first time I was never able to locate any infiltration - despite my best efforts - but ended up re-installing the operating system just for peace of mind.  

It has been about two months since then.  I do regular scans with Clam Av, all which have turned up clean.  But they say the same zero access trojan has been detected on the network.  They provided me with a symantec download for windows to remove the virus, but when I explain that I run linux they sound surprised and don't have an answer for me.

I'm not too sure what else I can do.  Any guidance is appreciated.

Thanks
Tyler

---

### Post by Luke M on 2014-05-16
Almost all such things are written for Windows, so it's unlikely your ubuntu is infected (assuming you aren't running Windows in a virtual machine or something...)

---

### Post by QIII on 2014-05-16
Hello!

Do you have an unsecured wifi router one of your neighbors might be tapping into?

---

### Post by HiImTye on 2014-05-16
the symantec pages specifies these IP addresses as connected to the trojan, so you can monitor your network for attempts to access those IPs
```
69.176.14.76
76.28.112.31
24.127.157.117
117.205.13.113
200.59.7.216
113.193.49.54
193.105.154.40
```
it also lists that it attempts to contact these time servers```
    ntp2.usno.navy.mil
    ntp.adc.am
    chronos.cru.fr
    wwv.nist.gov
    clock.isc.org
    time.windows.com
    time2.one4vision.de
    time.cerias.purdue.edu
    clock.fihn.net
    ntp.duckcorp.org
    ntp.ucsd.edu
    ntp1.arnes.si
    ntp.crifo.org
    tock.usask.ca
```so if you use ntp they could be getting a false positive. I would ask them what specific activity they detected on your network. here's the technical details of the trojan in question [http://www.symantec.com/security_response/writeup.jsp?docid=2011-071314-0410-99&tabid=2](http://www.symantec.com/security_response/writeup.jsp?docid=2011-071314-0410-99&tabid=2)

---

### Post by tbredschneider on 2014-05-16
Possibly.  I'm only a tenant in a rental unit, so I'm going to have to ask about changing the security settings.

---

### Post by tbredschneider on 2014-05-16
> **QIII said:**
> Hello!

Do you have an unsecured wifi router one of your neighbors might be tapping into?

Possibly.  I'm a tenant at a rental property, so I'm going to have to ask about changing the security settings.

---

### Post by tbredschneider on 2014-05-16
> **HiImTye said:**
> the symantec pages specifies these IP addresses as connected to the trojan, so you can monitor your network for attempts to access those IPs
```
69.176.14.76
76.28.112.31
24.127.157.117
117.205.13.113
200.59.7.216
113.193.49.54
193.105.154.40
```
it also lists that it attempts to contact these time servers```
    ntp2.usno.navy.mil
    ntp.adc.am
    chronos.cru.fr
    wwv.nist.gov
    clock.isc.org
    time.windows.com
    time2.one4vision.de
    time.cerias.purdue.edu
    clock.fihn.net
    ntp.duckcorp.org
    ntp.ucsd.edu
    ntp1.arnes.si
    ntp.crifo.org
    tock.usask.ca
```so if you use ntp they could be getting a false positive. I would ask them what specific activity they detected on your network. here's the technical details of the trojan in question [http://www.symantec.com/security_response/writeup.jsp?docid=2011-071314-0410-99&tabid=2](http://www.symantec.com/security_response/writeup.jsp?docid=2011-071314-0410-99&tabid=2)

If I were to set up my firewall to deny outgoing access to those IP addresses (or whatever activity my provider is detecting), would that prevent future problems?

Thanks
Tyler

---

