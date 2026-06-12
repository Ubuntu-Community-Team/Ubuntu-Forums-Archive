---
title: "What version of GRUB does Ubuntu 7.04 use?"
date: 2007-09-12
forum: General Help
---

### Post by Warren Watts on 2007-09-12
I recently wiped my Ubuntu install and replaced it with Archlinux, which installed GRUB version 0.97 (it says so right at the top of the GRUB boot screen).

I have a number of GRUB splash screens I customized for the version of GRUB that Ubuntu installed, and it "looked different" than what I get with 0.97.

Anyone know:
- What version of GRUB Ubuntu 7.04 uses
- How (if possible) I can edit the layout of the GRUB text screen in 0.97 so it matches the one used by Ubuntu?

---

### Post by p_quarles on 2007-09-12
My installation uses grub 0.97-20ubuntu06. To check your version type:
```
cat /boot/grub/installed-version
```
Here's a how-to on setting up grub splash images:
[https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4](https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4)

---

### Post by Warren Watts on 2007-09-12
Thanks for the help identifying my version of GRUB.. :)

The issue I have isn't with how the splash screens look.  (But thanks for the link!)  My issue is with the placement of the text itself on the screen..  The GRUB what was installed by Archlinux has a smaller bordered box than the GRUB formerly installed by Ubuntu, and it doesn't match the GRUB splashes I have made.
See in the attachment below how I have a shaded area where the text box appears in Ubuntu's GRUB?  
In the version of GRUB that Archlinux installed, the box is smaller.

[URL="http://kingbeetle.servehttp.com/cgi-bin/grub_thumb_view.pl"]
Link to all my GRUB splash screens[/URL]

---

