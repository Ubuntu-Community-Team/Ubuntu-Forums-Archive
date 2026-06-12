---
title: "Can't mount non-HD devices..."
date: 2006-09-05
forum: General Help
---

### Post by CA_Warren on 2006-09-05
Basically, I can't mount any non-(internal)-hard-drive devices anymore. Kubuntu 6.06 still sees them - they come up on the desktop, it recognizes if it's an iPod or SD card or hard drive, and how large it is, etc. - but upon double-click it says "Internal Error." Upon 'mount /media/sda1', I get the standard "mount: can't find /media/sda1 in /etc/fstab or /etc/mtab".

Is there a package or metapackage I could reinstall to try to fix this? What error logs should I look at to try to see what's behind KDE's uber-vague 'Internal Error'?

Help would be much appreciated.


Below is slightly more elaboration for those who have time - basically I think Automatix or a very recent update is at fault.

Recently I installed Automatix. Soon thereafter, though I didn't make the connection at that point, I stopped being able to mount external HD's, iPod's, or even an SD card with the internal card-reader.

I posted on the forums, got nary a response, and had some other glitches going on so I reinstalled Kubuntu 6.06. I keep /home on another partition, so no problem. After reinstallation, mounting works just fine.

I went to reinstall all of my programs, update the ones that came with the release, and then install Automatix again. Mounting doesn't work again ](*,) . I try from the command line, but to no avail.

SO: I have to imagine it was either Automatix or a very recent update (since there were no problems until very recently). Any ideas? I have reinstalled the basic 'mount' and 'pmount' packages - also no avail.

---

