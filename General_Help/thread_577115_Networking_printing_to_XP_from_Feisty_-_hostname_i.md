---
title: "Networking printing to XP from Feisty - hostname issue"
date: 2007-10-15
forum: General Help
---

### Post by mmtowns on 2007-10-15
I'm running Feisty and sharing my Brother HL-1240 printer with a Windows laptop (and eventually my MacBook running OS X, but that's for another day!)

I used [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) to share my printer via the Global Settings.  When I tried to add the network printer in XP using "http://ubuntu:631/printers/BrotherH", I get an error in a dialog box...

"Windows cannot connect to the printer.  Either the printer was typed incorrectly, or the specified printer has lost its connection to the server.  For more information, click Help."

So....I changed it to "http://192.168.0.101:631/printers/BrotherH" and it works.  But, I'm getting my IP address dynamically from my router and I'd rather not assign my Linux box a static IP address (although I am ultimately willing to do this, if it is the only way to fix the problem).  When I reboot, I'll obviously have a different IP address, so I'll have to change my XP network printer settings.  I also noticed that I can't ping "ubuntu" from my XP box.  

Does anyone know of a work around such that my XP box can "see" the hostname of my Linux box?

Finally, yes I'm 99% confident that my Linux box's hostname is "Ubuntu" because "Ubuntu" is returned at the command line when I type "hostname."  

Any suggestions y'all might have are appreciated....

---

### Post by tylerious on 2008-04-08
Rather than creating my own post, I'm going to bump this one since I have the exact same problem (and strangely enough, the same printer). I am running Gutsy. Trying to print via IPP works with [http://xxx.xxx.xxx.xxx:631/printers/BigBrother](http://xxx.xxx.xxx.xxx:631/printers/BigBrother), but not [http://ubahn:631/printers/BigBrother](http://ubahn:631/printers/BigBrother).

I am at a university, so I get dynamic IP addresses and have no control over my school's DNS.

Can anybody help us out on this?

---

### Post by mmtowns on 2008-04-08
I never did end up getting this problem resolved....well, at least on the software side of things.

I bought a print server and hooked it up to my Brother.  I assigned my print server a static IP address and figured it out from there.

I'm guessing this doesn't help you out a lot, but thought I would share my "resolution" so that you didn't keep wondering if I had solved it or not.  

I'm hoping someone else can chime in here...

---

