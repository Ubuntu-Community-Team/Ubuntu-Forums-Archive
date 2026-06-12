---
title: "[SOLVED] Screen Resolution Difference between Cold/Warm boot and logouts"
date: 2008-05-14
forum: General Help
---

### Post by crtlbreak on 2008-05-14
Good Day Forums
Using 8.04 (online upgrade from 7.10) on a AMD with 2GB RAM.

I have a niggle (dont we all!) about the desktop resolution being a 640 x 480 when I cold or warm boot on 8.04. I then need to do a "logout" to gain my 1280 x 1024 back.
[COLOR="Blue"]Where will I start looking for the difference in xsession resolutions between the cold/warm boot and the logout/login?[/COLOR]
I know that /etc/X11/xorg.conf is the default config file - and this is correct - but warm and cold boot still deliver a 640 x 480 resolution till I perform a logout  - upon logout  - the moment the login window reappears it is in the correct 1280x 1024 resolution - rather frustrating.
The same occurs when I try login as root - so the issue does not seem user based - more like session based.
Yes - I have an NVIDIA graphics card - the famous and now infamous!

---

### Post by crtlbreak on 2008-05-28
I have (after much fooling around) found the issue. :confused:
As I have a KVM switch that I can switch between workstations - The ubuntu box is booting up wile I am working on the other machine.  When it boots up it loads the default 640 x 480 resolution as it cannot see the monitor connected. The only way to get around this is to keep the KVM switch towards ubuntu booting up - then it will load the higher resolution - OR log out and log back in again.
I went to a HUGE exercise of even replacing the hard drive and installing fedora core6 to prove it. Fedora core 6 behaves the same way as ubuntu - so it is DEFINITELY not an OS issue - rather the OS is behaving correctly - it does not see the high-res screen connected and therefore loads default  640 x 480 resolution.
Live and Learn!!!!
:lolflag:

---

### Post by danwood76 on 2008-05-28
Get a better KVM, most good KVM these days emulate the monitor to some degree to stop things like this happening.
They also emulate mouse and keyboard aswell ;)

---

