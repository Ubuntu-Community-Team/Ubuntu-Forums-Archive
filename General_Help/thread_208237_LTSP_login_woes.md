---
title: "LTSP login woes"
date: 2006-07-03
forum: General Help
---

### Post by v4169sgr on 2006-07-03
I am running the Ubuntu LTSP install and am using a PXE clent to log in.

After the server has been power-cycled, the client can power up successfully and displays the LDM login manager. I can then access user accounts on the server, so long as the client is not restarted, and I keep going back to the LDM.

But if I power off the client, on powering on the client again I do not achieve the LDM display. Instead what happens is that for a brief moment I see the 'X' mouse cursor from the X display, then I am dumped at 'LTSP Login:' at the console and find that all user authentications fail i.e. I am locked out.

Hence I am able to connect the client ONCE in any given uptime at the server; if I wish to connect the client again I need to reboot the server.

What is going on?

Debugging is not helped by not knowing where to look for logs.

Reference posting: [http://ubuntuforums.org/showthread.php?t=208172](http://ubuntuforums.org/showthread.php?t=208172)

Many thanks for your help!! :D

---

