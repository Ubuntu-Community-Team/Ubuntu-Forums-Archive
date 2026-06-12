---
title: "Previously stable system randomly locking up"
date: 2013-04-24
forum: General Help
---

### Post by fizikz on 2013-04-24
The problem: all of a sudden all input devices cease to work. The mouse freezes in place, and nothing on the keyboard works at all(hotkeys, capslock light, etc), not even Alt + Sys Rq + (r e i s u b) which usually works to reboot a locked up system. 

Previously, my system, an Asus G1 running Ubuntu 12.04, was very stable, so I'm suspecting that it has to do with the wireless adapter upgrade that I just did, going from the old Intel 3945ABG to an Intel 5100AGN. Is there anything that should be done when changing hardware like this?

lsmod used to show iw3945 with the old card, and when I did the upgrade, it seamlessly disappeared and iwlwifi took its place. 

I hope the wifi adapter is not a red herring. I am open to other thoughts, however this problem showed up within an hour of the upgrade.

---

### Post by fizikz on 2013-04-25
I can confirm that it is probably not a hardware problem, since I have been running in windows for several hours (dual boot) without any instability. 

What could cause Ubuntu to lock up that way, and what could I check? Something in the logs?

---

### Post by JRV on 2013-04-25
I doubt that it is in the wireless, mine does it too, on rare occasions, with wired internet.

I think it is in the video driver.  Mine is Nvidia.

I do not have this problem on my system with Intel graphics.

---

### Post by georgelappies on 2013-04-25
Started happening to me now in 13.04. Never had it before. All input would freeze up completely. Only way to get machine back is to hold in power button for 5 seconds to force shutdown...

---

### Post by fizikz on 2013-04-26
JRV, you may be right about it being the graphics drivers. I also have an Nvidia card. However, I have had a very stable system for quite some time. I did recently (a week or so ago) update to the latest proprietary drivers 304.88. It's only now that I'm suddenly having these crashes. I re-installed the driver and started using Ubuntu again and after a while it still crashed again.

One slightly unusual observation is that normally, I see the Nvidia splash screen during boot, but now I no longer see that. Any suggestions on how to troubleshoot a driver issue? lsmod does show the nvidia driver being used.

georgelappies, I'm still running 12.04 on this particular system, although I'm upgrading to 13.04 on a separate system for testing. Perhaps use lsmod to see which driver is being used. Do you have an Nvidia graphics card too?

---

### Post by fizikz on 2013-04-27
Any ideas what to look for? Which logs to inspect? These freezes make Ubuntu totally unusable!

---

### Post by gordintoronto on 2013-04-27
The first thing to check with an old laptop is overheating. Do you use a temperature monitor?

---

### Post by fizikz on 2013-04-27
The temperatures are normal for the laptop. I have dusted and cleaned it before as well. 

I wonder, can the wireless adapter be the cause of the freezes? I've had several of them in Ubuntu, but just a few minutes ago, it happened in Windows too. I'm not sure what to check to be sure it was the wireless adapter, but the wireless upgrade was the most recent change that was made. 

I may put the old adapter back in and see whether the system becomes stable or the freezes continue.

---

### Post by gordintoronto on 2013-04-28
PLease let us know the outcome! There are so many possible causes of a system crash, even a loose connector could be the culprit.

---

### Post by fizikz on 2013-05-02
I am thoroughly confused about this problem, I don't know what caused the freezes, and I also don't know how they've stopped. I've been running for 2 days with no issues, at least for now... 

The only thing I can think of is the naming of the of the network interfaces. The original wireless adapter 3945ABG was wlan0, and when I upgraded to the 5100AGN, the new adapter was called wlan1. When I swapped it out with another identical 5100AGN (to test for a defective adapter), it was identified as wlan2. For some reason, it recently reverted to calling my updated adapter by wlan0. I don't see the significance in the interface names in the context of the freezing problem, but I thought I'd mention the one difference I observed between the crashing and non-crashing times.

I have no idea if the problem is actually solved, but at least things have been stable since the last 2 days.

---

### Post by fizikz on 2013-05-06
And after several days of no crashes, I've had a series of crashes again. They came as suddenly and as mysteriously as they has gone. 

I still don't know what's causing the crashes, or which logs to inspect. I hope I don't have to resort to a clean install.

---

### Post by fizikz on 2013-05-10
I've borrowed an Intel 6200AGN from another system and will be using it for a few days to see if the crashing continues or stops. It's been about a day so far with no crashes yet, although I did get a strange internet drop which resolved itself after a while ([http://ubuntuforums.org/showthread.php?t=2143995]("http://ubuntuforums.org/showthread.php?t=2143995")).

Additionally, whereas with the 5100 I was only seeing single stream link rates in Ubuntu (but dual stream link rates in Windows XP), with the 6200 I'm seeing dual stream link rates reported by iwconfig and Ubuntu.

I'll see how the Intel 5100AGN fares in the other system, but so far it is working and reports dual stream link rates in Windows 7.

---

### Post by tgalati4 on 2013-05-10
If these are pcmcia cards then it is possible that your slot is worn out.  That will cause a hard freeze since it is directly connected to the system bus.  All it takes is a crack in the solder that holds the pins on to cause intermittent problems.

---

### Post by fizikz on 2013-05-10
They are mini PCI-e slots / cards. Although cracks and the like could develop at any time, there was no intermittent freezing problem before the wireless adapter upgrade.

---

### Post by fizikz on 2013-06-04
This problem is finally solved. I think the issue was hardware incompatibility of the Intel 5100 and 6200 adapters with the Asus G1. It was confusing, since they both functioned perfectly well... except for random system freezes.

After lots of trial and error, I have found that the Intel 4965 and iwl4965 driver work well with the Asus G1. I have been using it about a week with no system instability. The wireless performance is quite good, too, and I finally have wireless N. 

Hopefully this saves someone some time and frustration.

---

### Post by fizikz on 2013-07-14
A bit after a week, the Intel 4965 started having drops too. Finally, as a last resort, I dumped Intel and went with an Atheros 9380 pulled from a Mac. The 9380 using the ath9k driver has been stable for over 2 weeks now with no drops. I hope the search for an N wireless adapter for this laptop is now over.

---

