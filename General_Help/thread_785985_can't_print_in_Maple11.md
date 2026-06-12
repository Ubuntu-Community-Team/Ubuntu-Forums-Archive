---
title: "can't print in Maple11"
date: 2008-05-07
forum: General Help
---

### Post by Pollywoggy on 2008-05-07
I am using CUPS for printing in Hardy and I can print from Gnome and KDE apps but I tried to print from Maple (xmaple) and Maple complained that it could not find the print service.  I added a /etc/cups/client.conf file with the line

ServerName localhost

I still can't print although Maple has stopped complaining that it can't find the print service.
It occurs to me that this might be because I installed Maple in my home directory and not for systemwide use.  Also, the problem appears to be due to Java.  When I started Maple from the command line and tried to print, I got this:

#16 /home/pollywog/maple11/jre.IBM_INTEL_LINUX/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb758d2cd]
#17 [0xb2a7b41b]
#18 [0xb2a759a4]
#19 [0xb2a73157]

Any ideas?

---

