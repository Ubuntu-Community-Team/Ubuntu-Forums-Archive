---
title: "Strange boot problem..."
date: 2007-06-27
forum: General Help
---

### Post by Christopher Young on 2007-06-27
Hi.  I am pretty much a Linux n00b.  I have been running Ubuntu 7.04 for about 1 month now.  Recently I decided to try and dual boot Gentoo.  After about 20 minutes (not even getting to installing portage) I decided "Ubuntu works just fine, screw this."  So I just rebooted.

Then things got weird.  After going through the initial booting (I saw the Ubuntu logo and the loading bar) I get dropped into terminal with ROOT privileges.  No logging in, just dropped into root.  After messing around for a bit trying to load gdm and trying "startx" I gave up and typed "shutdown -r now".  Says it's sending the TERM signal, screen flashes.  Bam.  Login screen?  From there I can use Ubuntu perfectly with no problems.

Any idea on what I may have done?

Please tell me what files you may need me to post. :)

---

### Post by Qu4k3R on 2007-06-28
Are you using the correct boot options for ubuntu ?

Maybe could it be gentoo ?

---

### Post by Christopher Young on 2007-06-29
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d464b386-eb6d-4c02-a4d2-5e6435fe7c02 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault



^^^^From Grub.  That's my default.

---

