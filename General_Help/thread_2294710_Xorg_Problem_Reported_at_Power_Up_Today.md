---
title: "Xorg Problem Reported at Power Up Today"
date: 2015-09-12
forum: General Help
---

### Post by Mark_in_Hollywood on 2015-09-12
For several weeks I have been having screen freezes, mouse freezes and greyed out browser pages. Today, using REISUBK I rebooted out of a stuck screen/mouse. On re-boot, the Problem Reporting window came up, twice, first before the OS had loaded much (and vanished) and shortly thereafter, once the OS was up & running. I clicked OK to send a report. It is about Xorg. That's all I know, I didn't read the whole report. (I wish I had now). I rebooted again. I called System Log and looked at Xorg, but see no errors. Actually, although I searched for the keyword: error, I don't see what is relevant to the Xorg and mouse.

See screenshot for CPU and drive usage during problem. Since I can fix this by rebooting it's not serious, but I would like to know if I installed the NVidia proprietary drivers if that would eliminate this problem.[ATTACH=CONFIG]264381[/ATTACH]

---

### Post by tgalati4 on 2015-09-12
Your IOWAIT's are quite high.  This could indicate a bad hard drive.  What is the SMART status of your hard drive?

```
sudo smartctl -a /dev/sda
```

The log files are suggestions and not helpful if there is a real hardware problem.  A software graphics problem shows up as:

```
grep EE /var/log/Xorg.0.log
```

---

### Post by Mark_in_Hollywood on 2015-09-14
The same Report a Problem window came onscreen at power up this morning. This time I opened the report and read through it. It would appear that the OS is looking for the NVidia drivers I had installed, prior to upgrading to Ubuntu 14.04 LTS. On that upgrade to 14.04 I chose non-proprietary video drivers.

About a month ago, I tried to run Blizzard's Diablo II. It failed on the opening splash screen. I also have a Wacom tablet plugged in and the error report mentioned the Wacom as well as text that seemed to say the OS was looking for the NVidia drivers. Those being the **EE** in the grep command.

I have chosen to re-install the NVidia driver (ver. 340.76) and upon rebooting, there is no Error Report window coming onscreen. I'll re-open this post if a problem reappears.

Thank you, Linux Community.

---

### Post by tgalati4 on 2015-09-15
Since you have now installed a proprietary video driver, every time you upgrade your kernel, you may need to reinstall the video driver.

---

