---
title: "Made the switch from Apple, monitor question"
date: 2014-01-07
forum: General Help
---

### Post by DigiAngel on 2014-01-07
Hey All,

Topic says it...made the switch from OS X as Mavericks is terrible.  That being said I'm on a mid-2010 27" iMac and I'm dual booting Mav and Ubuntu 13.10.  Here's a list if things I have a question on:

3)  Enabling second monitor ruins application window size (open apps move to second monitor, new apps go to it as default) - Any way to change this behavior?

Other than that it's been a good go of it...very happy with my results.  Thanks for any help you can provide.

---

### Post by buzzingrobot on 2014-01-07
I recall an option in Evolution preferences to allow inline images.  Its wording may be less than obvious.

Compiz Config: Unity is implemented as a Compiz plugin.  My assumption is that the config module is not shipped by default because changing some settings can break Unity.

Have you tried "Unity Tweak Tool" (in the repos) or "Ubuntu Tweak" (PPA)?  Both enable changes and tweaks to interface behavior.

---

### Post by DigiAngel on 2014-01-07
Thanks for the response...yes I have both of those tweak tools.  I LOVE Ubuntu Server and run it as my router here..but I have to say I was not prepared for Ubuntu Desktop to be so functional and enjoyable to use.  My perception that Linux isn't ready for the desktop has been completely blown away...a good start to the new year :)

---

### Post by Bucky Ball on 2014-01-07
For the monitors you might want to install and tweak arandr. Its in the repositories.

---

### Post by tgalati4 on 2014-01-07
What keyboard shortcuts are you using for "screenshot"?  On a PC, the PrintScreen and Alt-PrintScreen always work, but I'm not sure what they are automatically mapped to on the mac  Perhaps the keys are being grabbed by another application.

The auto power on is a feature of the proprietary power controller on the Mac.  True, on PC's, the BIOS normally has this feature.  A work-around would be to use wake-on-lan and use a server or router (running a useful operating system) to send that WoL packet at the appointed time.  To put the machine back to sleep would part of the backup script using one of several sleep methods.

For customizing the second monitor look in *xrandr* and its settings.  The settings you use depend on hardware, so you will have to do some research:

[https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor](https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor)

[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

### Post by DigiAngel on 2014-01-07
Thanks BB and tgalati4..looking into the monitor issue now.  Was told that I should split this thread out into single issues, so i'll focus on the monitor with this one...thanks again :)

---

### Post by DigiAngel on 2014-01-07
Got the tweak, same effect though...it's very strange.  Thanks though.

---

