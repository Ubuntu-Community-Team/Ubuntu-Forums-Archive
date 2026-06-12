---
title: "IBM Thinkpad W520 crash on suspend/resume"
date: 2014-08-04
forum: General Help
---

### Post by Jason_Pacheco on 2014-08-04
I was previously running 12.10 without any issues. Since a clean install to 14.04 I've been having consistent crashes on suspend resume. The symptoms vary, more recently the laptop will resume but I will have a black screen with a cursor (that moves). I can switch over to a terminal and stop/start lightdm to get things back. In these cases there will be a /var/crash/_usr_bin_compiz...crash file which is too large to post ~75MB.

Another common symptom is that the kernel panics on resume accompanied by a /var/cras/susres....crash file, at which point I need to do a hard restart. Occassionally too the kernel will panic on the suspend. I'm not sure if it's related but I did have issues getting my Nvidia drivers working properly, but they seem to be OK now with the nvidia-current (304.117) package. I have an onboard Intel chipset but I use the Nvidia chip instead because I frequently need to export the display to a monitor which didn't work on the Intel chip in 12.02.

This issue seems to happen most frequently when closing the lid, as opposed to selecting "suspend" from the power menu. Also, I don't have a hybernate option in the power menu anymore, which is odd. I'm not sure what logs, diagnostics to run/post, please let me know and I'll be happy to provide the necessary information.

Thanks,
Jason

---

### Post by tgalati4 on 2014-08-04
Have you performed all of the updates on 14.04?  Perhaps there was a kernel update to fix suspend/resume.  This certainly sounds like a regression.  In 12.10, suspend and resume are documented in /var/log/pm-powersave.log and pm-suspend.log.  I understand that this has changed in 14.04, so look around in /var/log.

I'm running an older T43p and it runs fine on 12.10.  Haven't moved to 14.04 yet.  Waiting for you to work the bugs out.

---

### Post by Jason_Pacheco on 2014-08-05
Yes, everything is up-to-date.  I've had lots of bugs compared to 12.10; my advice is to stick with 12.10 for a while.  Do you know how much longer they will support 12.10?  I'm considering switching back because 14.04 is just unstable for me.

Jason

---

### Post by tgalati4 on 2014-08-05
Well, technically, 12.10 is out of support, but 12.04 (moving backwards) should be supported until April 2017.  If you want newer packages, try incremental updates-->13.04 and use it for 6 months then move to 13.10.  Perhaps by that time 14.04 will more stable for your hardware.  Because the [W520]("http://www.thinkwiki.org/wiki/Category:W520") is a beast of a machine, it uses quite a bit of power, so I image that power to the bus is critical for proper suspend and wake.  I'm pretty sure it is related to the dual graphics chips.  Perhaps turn one off in BIOS.  Did both graphics chips work correctly under 12.10?

Open a terminal:

```
sudo apt-get install acpitool
acpitool -w
```

Turn on various parts of the bus with the -W switch and try suspend/resume.  If you do one device at a time, you might be able to narrow down the culprit.

---

### Post by Jason_Pacheco on 2014-08-05
Sorry, I was running 12.04 LTS, not 12.10.

I have always had the Intel chip disabled in the BIOS and am only running on the nVidia chip, since exporting the display through Intel didn't work in 12.04.  I haven't tried it in 14.04 but I suspect it probably doesn't work.

I've installed acpitool and will play around with disabling various things to see if it sheds any light on the issue.

Jason

---

### Post by tgalati4 on 2014-08-06
Sometimes the onboard Intel chip needs extra video RAM to export the display correctly.  Be sure to set the video RAM (which is shared with normal RAM) to a large number in BIOS.

I bet if you turn off the nVidia chip, then suspend and resume will work on 14.04.  Proprietary drivers hook directly into the kernel (hence the name "tainted" when applied) and that makes troubleshooting difficult because they are a "black box" or "binary blob" without any source code to investigate.

The other option is to move to 12.10, 13.04 or 13.10 as an intermediate step until 14.04 gets sorted out.  You didn't really need to use this computer, so you have the time to test all of these distros.

---

