---
title: "Hard freezes when two monitors plugged in (16.04, Skylake NUC)"
date: 2016-05-28
forum: General Help
---

### Post by jamespetts on 2016-05-28
I have an Intel Skylake i5 NUC on which I have Ubuntu 16.04 LTS installed. I use it in multiple places: mainly at work, but also when I visit my parents. The NUC is fairly new, and this is the first time that I have taken it to visit my parents. At this location, I use two monitors, both of which have a DVI connexion. I plug one monitor in to the HDMI port using a DVI cable and an HDMI to DVI adapter, and another into the DisplayPort using a DVI cable and DisplayPort to DVI adapter.

When I first set this up yesterday evening, it worked well, and ran without problems for about 4 hours. During that time, I downloaded some automatic updates (I had also downloaded updates earlier that afternoon before visiting my parents). I set up AutoFS and mounted some folders connected to another computer on my parents' wired network, and restarted the computer to make sure that AutoFS was working properly on reboot, but the system hard froze seconds after logging in. Not even ALT+SYSREQ R, S, E, I, U, B had any effect. The Numlock light was stuck. Only using the power off button would enable it to be reset. On every restart attempt, the same occurred: the system would hard freeze a few seconds after reaching the login screen, whether I logged in or left it at the login screen. I tried reverting a change made to the NFS configuration file during the AutoFS process, but this made no difference.

I eventually found that this problem only occurred when both monitors were plugged in. With only one monitor plugged in (it did not matter which one), the problem did not recur. If I booted the system with one monitor connected and then plugged in the other one later, it would work fine until the second monitor was connected, and then hard freeze seconds after the connexion. 

This problem does not occur in the BIOS, nor does it occur on the pre-login screen in which I have to enter the password to decrypt my encrypted SSD: with two monitors plugged in, it will remain responsive for an extended period, only to hard freeze seconds after reaching the login screen. This suggests to me that this is not a hardware problem.

I have updated my BIOS from the 0042 version that I had previously been using since I first had the NUC (I updated the BIOS to 0042 before installing Ubuntu to avoid the problems caused by earlier versions of the BIOS for these computers) to the latest 0044 version (which should make my SSD run faster) using the BIOS recovery method of updating recommended for this particular update, but it has made no difference. 

Any assistance would be much appreciated.

**Edit**: On booting into Ubuntu 16.04 from a USB drive with a newly created USB image, this problem does not occur. I am writing this from the computer, with the two monitors connected, in Ubuntu 16.04 from the USB drive, and it is working without trouble. This strongly suggests that the problem is in the software somewhere.

---

### Post by QDR06VV9 on 2016-05-28
Moved to UDV

---

### Post by jamespetts on 2016-05-28
I have seen that this has been moved to the Development Version subforum. I think that this is due to an error on my part in the original post, where I incorrectly stated in one place that I was running 16.10. In fact, I am running 16.04. Would it be possible to move the thread back? I should be very grateful. Apologies for the error.

---

### Post by cariboo on 2016-05-28
Moved to General Help, as I'm not exactly sure where it started.

---

### Post by jamespetts on 2016-05-28
I had originally put it in hardware, but this is probably just as fitting. Thank you for moving it, and apologies for the error.

---

### Post by jamespetts on 2016-05-29
I have now found the solution to this, after enquiring at the Intel NUC forum: upgrading to kernel version 4.6.0 according to [these](http://ubuntuhandbook.org/index.php/2016/05/install-linux-kernel-4-6-ubuntu-16-04/) instructions fixes this issue. It seems to have been a graphics driver problem.

---

