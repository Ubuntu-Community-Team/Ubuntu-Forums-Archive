---
title: "Ubuntu stuck while booting Initframs unpacking failed: Decoding failed"
date: 2021-12-27
forum: General Help
---

### Post by rene1301 on 2021-12-27
So.. Iam daily driving Ubuntu for about 2 months now and honestly it was working fine unitl today.
There is an Initframs failure while booting, just out of nowhere. I cant recall doing an Update or anything majore before shutting the PC down yesterday, so such an issue is quite surprising tbh.
I googled a bit and found a few possible fixes but I could not try them out because none of my keyboards are working anymore when I come to the screen (I tried two USB and one PS2). Maybe a bios setting issue?? 
Any suggestions how I can at least get a working Keyboard at this point so that I can try some fixes?
Mainboard is a B350 PC Mate and installed is Windows 11 besides Ubuntu each on an seperate SSD.

Picture of the Terminal is attached

Thank you all in advance for helping a newbie

---

### Post by Bashing-om on 2021-12-27
Hello rene1301 - Welcome to the Forum

As a first stab at this I suggest that you run a file system check/repair from your liveUSB.
See: [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)
for the tutorial is ya need direction.


Depending on this result is what happens next :D

[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by rene1301 on 2021-12-28
I tried it and it came out as clean, any other suggestions?

---

### Post by Dennis N on 2021-12-28
> **rene1301 said:**
> I tried it and it came out as clean, any other suggestions?
Use Advanced Options in the grub menu and boot with an older kernel version.

---

### Post by rene1301 on 2021-12-28
> **Dennis N said:**
> Use Advanced Options in the grub menu and boot with an older kernel version.

When I go Into advanced options I only have two choices, Start ubuntu normally or start it in recovery mode, both end up in the initframs issure without a keyboard working
Am I doing something wrong?

---

### Post by Dennis N on 2021-12-28
So, you don't see this dialog? Ubuntu would not leave you with just one kernel version.[U]

Update:[/U]
A guide like this one may provide a fix:
[https://linoxide.com/fixing-broken-initrd-image-linux/](https://linoxide.com/fixing-broken-initrd-image-linux/)

---

