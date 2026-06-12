---
title: "Microphone help needed (fiesty)"
date: 2007-04-27
forum: General Help
---

### Post by jonnymccullagh on 2007-04-27
I have a new laptop and installed fiesty. The laptop has a built-in microphone and a microphone socket but I cannot seem to get either working.
The device is listed as ALC880 - it is showing as an Intel but I think it is a Realtek.
I have attached a screenshot of System -> Preferences -> Sound. When a test a cannot get any response when speaking into either microphone.
I have also played with the settings in Volume Control and toggled between my 3 audio capture devices and set the volume on all of them to highest settings.
I'm at a loss now and I'd appreciate any help,
thanks,
j

---

### Post by mac.ryan on 2007-04-27
Have you checked the bugs filed in launchpad? For example: this one seems pretty close to your problem... but is it the same laptop?

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110599](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110599)

...on a desktop I configured yesterday, I had a similar problem and the only workaround that made the trick (out of 3 proposed) was to install kmix (the kde mixer) and set stuff from there. (Sounded so weird for a gnome user that I did it as last resource... but it worked!).

---

