---
title: "Asterisk: Zaptel and X100P Configuration problem"
date: 2006-12-27
forum: General Help
---

### Post by mdmohideen on 2006-12-27
Hi,
 I am facing issue with X100P card installed on my system.

My current setup..
 - Configured zaptel on ubuntu box
 - Installed and configured Asterisk on Ubuntu box
 - Configured few extensions in SIP and IAX ( working good)
 - Installed X100P card on the system

 With this setup on my system (running mode), as soon as I connect (using RJ11) the incoming phoneline(SBC) service connection to the "line" port in X100P, the call line(dial tone) is establised before I make the calls. After few mins, the line is engaged and then dead until I unplug the connection from X100P.
 I was wondering how would I resolve this issue. Any help or inputs will be greatly appreciated.

Thanks,
Mohideen.

---

### Post by magicfab on 2007-01-29
For asterisk you can try to see this guide:
[https://wiki.ubuntu.com/AsteriskOnUbuntu](https://wiki.ubuntu.com/AsteriskOnUbuntu)

Regarding your particular problem, I wonder how you installed the Zaptel drivers ? In the guide I am putting together, I was able to document a sucessful update of the driver by using standard packages (no CVS downloads).

Be warned, however, that the FreePBX part has not been tested. The document is work in progress.

---

