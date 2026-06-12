---
title: "Constant sound stuttering on 18.04"
date: 2018-11-19
forum: General Help
---

### Post by BkoChan on 2018-11-19
I broke my PC the other week so took the opportunity to upgrade to 18.04
I'm having a problem straight off the bat with audio constantly stuttering but I don't know how to diagnose the issue.

I uninstalled Pulse and tried Alsa but couldn't get any sound playing that way so reverted back to Pulse.
If I have music playing and watch the sound icon in the menu I can see it flicker whenever the stuttering happens.

When I had 16.04 installed there was an issue with it constantly (incorrectly) detecting a device being plugged into my front AUX jack which I solved by using software to disable the jack (I don't use it anyway)

Could someone tell me where to start diagnosing this? or failing that how can I disable the front jack on 18.04 to see if that works?

Thanks

---

### Post by Autodave on 2018-11-19
Your first problem is that you said that you upgraded to 18.04.  I see way too many problems caused by upgrading.  I learned a lon  g time ago to only do clean installs.  Saves me a lot of time and frustration.

I would recommend that you do a clean install and then report back here if still having problems. Please make sure to back everything up to an external source first!

---

### Post by BkoChan on 2018-11-19
Sorry, I could have worded that better. The problem is on a fresh 18.04 install

---

### Post by jerry47 on 2018-12-14
Hi. You&#8217;re correct the problem with the audio studdering and audio menu in the upper right corner flickering has nothing to do with upgrading or fresh install. I&#8217;ve got the same exact problem. Both 18.04 and 18.10. You&#8217;re the only one to mention the flicking. When I first noticed the flickering audio was turned off. Thought it was my wired lan having a problem. 

More about my two installs. Intel NUC7i7BNH kit. Install went fine. No issues except one time while I was away and the screen went blank, I was logged out by the OS. Screen almost completely froze icons scattered all over. Had to do a forced shut down. Hasn&#8217;t happened since. 

The other machine is 5 years old built by me. An Asus P8Z77-V Deluxe running Win 7 SP1. It has had zero issues. Boots in 5-8 seconds. Running dual monitors with an Nvidia 650TI. 16 gig ram. OCZ SSD. 

The Asus has the sound issue with Ubuntu. Used the Nvidia driver for the graphics adapter. It was studdering before the updated drivers. Also upgraded the Broadcom drivers for WI-FI adapter. Bluetooth and Wi-Fi are disabled. Using wired lan for all desktops on our network. 

One other issue that&#8217;s not a big deal but interesting is Ubuntu disables all USB ports after it runs once for the next restart. Boot screen indicates keyboard not detected. If I shut the machine down no problem. No USB problem while OS is running. Only on boot and restarting. 

No issues as far as I can tell with Graphics adapter or driver as the rest of the screen does not flicker. Only the pull down menu with audio slider and shut down button. The whole menu flickers about every 10 seconds. Coincides with the audio studder. 

Let me know if you find a remedy and I&#8217;ll do the same. Meanwhile I&#8217;ve got one SSD with Windows and another with Ubuntu. This is my main machine so I can&#8217;t have it down for long periods while I try to get Ubuntu fixed. 

Been in touch with Manjaro and Manjaro Deepin is about to release 18.00. Soon as that happens will be installing it to see if it has the same audio issue. 

Write me back about your motherboard and hardware. 

Thanks, 
Gerald

---

### Post by jerry47 on 2018-12-14
One more thing. Report back what the system logs indicate. I think it&#8217;s labeled &#8220;important&#8221;. I&#8217;ve got some ACPI issue going on that Windows does not report happening in event viewer. Would be interesting if you have the same errors. May or may not be related. It occurs at boot.

---

### Post by jerry47 on 2018-12-19
My Asus P8Z7-V Deluxe is not compatible with Ubuntu 18.04 or 18.10. Two main issues. The sound stuttering mentioned above and problems with Grub-Plymouth. Excessive boot times. Installed Manjaro Deepin booting in 7 seconds. Half of Ubuntu. Reduced resolution during boot even though Grub calling for monitor default resolution. Manjaro had no resolution issue during boot. 

I pulled the Nvidia GTX 650TI and reinstalled Ubuntu 18.10. The default GPU being onboard Intel. Booted quickly just as Manjaro did using the Nvidia adapter. 

Sound still stuttered on both Intel and Nvidia Graphics. On Manjaro using Nvidia GPU.

---

