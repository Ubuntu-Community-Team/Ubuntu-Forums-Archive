---
title: "Graphics issue?"
date: 2013-03-15
forum: General Help
---

### Post by Gibsonlpsb on 2013-03-15
Just got the latest version installed but my desktop repeatedly refreshes itself about every 15-30 seconds. This has happened to me on other distros too on this computer. I guess its a graphics issue. Do i get graphics drivers for Linux to solve the problem? Any help would be great!

---

### Post by Mark Phelps on 2013-03-15
Since you're seeing a desktop, you already have the "graphics drivers for Linux" installed.

To see what graphics chipset you're using, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA".  That will tell us the make and model graphics chipset you're using.

---

### Post by Gibsonlpsb on 2013-03-15
02:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1) is the current "chipset". I was aware that i had a Geforce 8600 GT before that tho. But thank you! I was just asking if it was a good idea to goto the NVIDIA site to get the updated version of them, to see if it would solve the issue, and since there was an update on the 13th for the linux-based version. I haven't proceeded in doing so because i wasnt sure if it would conflict or anything. This is my first desktop using Linux, so i'm a beginner.

---

### Post by Bashing-om on 2013-03-15
Gibsonlpsb; Hi !

As a rule in general, obtaining a driver from Nvidia is a means of last resort (unless you really know what you are doing) as it gets broken with each kernel update requiring the driver to be (re)installed. - this route is outside of 'buntu's package management system.

Again the recommended path is:
1. open source drivers
2. proprietary drivers from the "Additional Drivers" utility
3. If these venues are not productive, one might resort to installing the drivers from the Nvidia site.

What steps have you taken to this time, to guide you on further steps.[INDENT=3]
try'n to help

[/INDENT]

---

