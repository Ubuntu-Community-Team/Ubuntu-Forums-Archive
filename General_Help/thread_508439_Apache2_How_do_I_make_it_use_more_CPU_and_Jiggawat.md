---
title: "Apache2: How do I make it use more CPU and Jiggawatts?"
date: 2007-07-24
forum: General Help
---

### Post by krazyj on 2007-07-24
Hey all,

 Im running a local file/webserver in my house. Ubuntu Fiesty w/ Apache2.

 I want it to use more CPU! More simultaneous connections! More powah!

 Ive got it checking proxies right now (through a PHP script) and, admittedly the timeout is 10s per proxy, it still seems to be checking only one proxy at a time and taking FOREVER. When I checked my CPU usage, I was at 0-5%. I didnt buy a 1ghz machine for it to run slow! Workhorse, baby! How do I get Apache using multiple connections (checking multiple proxies at once) and utilizing more CPU.


Thanks,
Josh

---

### Post by EndPerform on 2007-07-24
Jiggawatts?  Did you remember to hook it into the flux capacitor first?  Seirously though, it might not be the machine that's taking so long.  It might be having issues negotiating the proxies on the network due to a number of reasons.

In order to check multiple connections, you'll probably need to modify your script to do so.  Apache2 by default spawns 5 processes and will (if I remember the configuration right) spawn up to 5 more if it needs to.  Check the script first.  If it only does one connection, you'll need to edit it to do multiples or else call up multiple instances of the PHP page in a browser and point it to different locations.

---

### Post by krazyj on 2007-07-24
> **EndPerform said:**
> Jiggawatts?  Did you remember to hook it into the flux capacitor first?  Seirously though, it might not be the machine that's taking so long.  It might be having issues negotiating the proxies on the network due to a number of reasons.

In order to check multiple connections, you'll probably need to modify your script to do so.  Apache2 by default spawns 5 processes and will (if I remember the configuration right) spawn up to 5 more if it needs to.  Check the script first.  If it only does one connection, you'll need to edit it to do multiples or else call up multiple instances of the PHP page in a browser and point it to different locations.

Thanks!

Excuse me, for I am a noob. Do you know what config values this would correspond to? I assume I could configure this through Webmin? If not through the .conf file for Apache? If so, then what values am I looking for?

:confused:
:extends hand to be held:

EDIT: I saw something under Webmin labeled 'Maximum concurrent requests'. Hot? Cold?

---

### Post by krazyj on 2007-07-24
Think of the jiggawatts.

Bump.

---

### Post by krazyj on 2007-07-25
Another bump.

---

### Post by EndPerform on 2007-08-02
Have you modified your PHP script to check more than one connection?  As I said, it doesn't matter how many Apache processes you spawn, it's a matter of how your script deals with connecting to the proxies.

---

