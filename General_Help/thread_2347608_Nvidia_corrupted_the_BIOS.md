---
title: "Nvidia corrupted the BIOS?"
date: 2016-12-27
forum: General Help
---

### Post by ClaraMFerreira on 2016-12-27
Hello to all,

I would love to get some input and understand what is this problem that has happened before, somehow fixed, and returned to a point where I don't know if I should take my laptop to a technical support or if I can fix it myself.

I have a custom build Clevo notebook, whose specifications are as followed (inxi -F)

```
System:    Host: Ood-Sigma Kernel: 4.4.0-57-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Notebook model: W65_67SH Bios: American Megatrends version: 1.03.03 date: 12/04/2013
CPU:       Quad core Intel Core i7-4700MQ CPU (-HT-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) 
           Clock Speeds: 1: 2894.062 MHz 2: 3020.343 MHz 3: 2968.031 MHz 4: 2403.375 MHz 5: 3005.906 MHz 6: 2899.875 MHz 7: 2666.906 MHz 8: 2910.937 MHz
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller 
           X.Org: 1.18.3 driver: nvidia Resolution: 1360x768@59.8hz 
           GLX Renderer: GeForce GT 740M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 367.57
Audio:     Card-1: Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel 
           Card-2: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller driver: snd_hda_intel 
           Sound: Advanced Linux Sound Architecture ver: k4.4.0-57-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
           IF: eth0 state: down mac: 00:90:f5:f4:1d:8e
           Card-2: Intel Centrino Wireless-N 2230 driver: iwlwifi 
           IF: wlan0 state: up mac: 00:c2:c6:50:f3:b6
Drives:    HDD Total Size: 500.1GB (47.8% used) 1: id: /dev/sda model: WDC_WD5000BPKX size: 500.1GB 
Partition: ID: / size: 148G used: 94G (67%) fs: ext4 ID: swap-1 size: 8.59GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 14.0C mobo: N/A gpu: 36C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 284 Uptime: 2 min Memory: 893.2/7903.8MB Client: Shell (bash) inxi: 1.9.17 
```


About two months ago, the system was stable with nvidia-352 drivers, however in the updates it appeared a "nvidia-transition" package, which was going to transition my drivers into nvidia-361. Something went terribly wrong, and when I booted, the laptop went into a login loop; but the worst is that the fans kicked in the maximum speed, and the laptop started beeping (one long beep in AMI BIOS = memory failure), followed by a shutdown 1 minute afterwards. I temporarily purged the nvidia and went back to nouveau, which fixed the login loop, but the shutdowns persisted. I could login normally into the system, no bugs whatsoever, but again the fans kicked in, beeps, and shutdown. Worth mentioning that it wasn't a sudden shutdown, the system receives a signal to shutdown and does so normally, without my control.
The laptop was at normal temperature (37ºC) which made me even more confused. Then I discovered that it did the same while I was in the BIOS menu. When I tried to diagnose the problem by unplugging all the USB, removing the battery, then again inserting the battery, as soon as the battery reached again the 100% with the cable on, the problem stopped.

I thought it was an isolated problem, and never thought about it again (my bad). I went back to nvidia-340 and used the intel profile, as the nvidia gave me the black screen problem at startup (solved by closing the lid, and opening, ta-dah!). With the good old steam winter promotions, I switched to the nvidia profile and at reboot, the beeps and shutdowns returned worse than ever. This time I knew what the beep code meant, and tried several times to perform a memtest, which failed over and over due to the shutdowns. Frustrated, I tried again the same fix as before: worn out the battery a bit, recharge at 100% with the laptop shutdown, and boot. It gave me no problems for a while and I was able to complete the memtest (no errors found), and I updated to the nvidia-361 with the nvidia profile (the black screen bug was finally fixed), and for a while it worked well, until out of nowhere the beep and shutdowns re-appeared.

I am very confused and the only problem I found in the logs that I never noticed before was this:
 ```
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] ------------[ cut here ]------------
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] WARNING: CPU: 0 PID: 0 at /build/linux-lts-xenial-FdAdUy/linux-lts-xenial-4.4.0/drivers/iommu/dmar.c:830 warn_invalid_dmar+0x7e/0x90()
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] Your BIOS is broken; DMAR reported at address 0!
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] BIOS vendor: American Megatrends Inc.; Ver: 1.03.03; Product Version: Not Applicable                  
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] Modules linked in:
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] CPU: 0 PID: 0 Comm: swapper Not tainted 4.4.0-57-generic #78~14.04.1-Ubuntu
Dec 26 11:48:16 Ood-Sigma kernel: [    0.000000] Hardware name: Notebook                         W65_67SH                        /W65_67SH                        , BIOS 1.03.03 12/04/2013
```

Right now, the issue is very unstable. Sometimes it works okay at first, and then shutdowns about one hour later, sometimes it's right at the start. I searched a lot through google, and there was some common issues that weren't my case:

* Overheating - Never a problem, the laptop has been stable at around 37ºC, the GPU never overheated since I bought this laptop (even during gaming and/or Summer).
* Fan problem - Opened my laptop, the fan is spinning just fine, all screws are well tightened.
* Unstable kernels - Not sure, the kernel was updated into the latest version during this crisis, and the problem persists.

Unfortunately, the BIOS has very few options for me to tweak, and I am clueless in how to update it.

If anyone has any clues on what the problem might be, please let me know. If I ever get it fixed (somehow), I will update this thread anyway, as perhaps a poor soul with a problem similar to mine might benefit from it.

The kernel log is located here: [https://paste.ubuntu.com/23693526/](https://paste.ubuntu.com/23693526/)
And the syslog: [https://paste.ubuntu.com/23693538/](https://paste.ubuntu.com/23693538/)
(It shows the session where I thought the problem was fixed, until at about 14:50 it shutdown, and then another session where it beeped at start, followed by a shutdown)

So, trying to brief my problems into one place:

* Initial trigger: After ex-changing nvidia-drivers or logging with nvidia-profile, the fans turn at maximum speed, the system beeps and shutdowns.
* One long beep = AMI BIOS Code translates it into memory failure.
* The OS logins and works just fine, with or without the beep-shutdown issue.
* The beep-shutdown issue is unstable, and occurs in the OS, BIOS, memtest, and sometimes before live-boot from a USB.
* It also occurs with Nouveau, nvidia-340 and nvidia-361.
* When the memtest completed successfully, no errors where found.
* Logs keep mentioning that the BIOS is broken.
* Temperature sensors report everything at 36-40ºC after shutdown.
* The nvidia drivers were obtained in through the oficial packages, no external ppa was used.
* Using a live-boot USB pen with 16.04, it works fine (but I rather not install 16.04 until this problem is 100% solved, to avoid shutdowns during the installation - yep I am very pessimistic)


And I think that is all. Thank you all for reading all this! :)

If you require more information, just ask away (or any commands I need to do, to diagnose further the problem).


**Update 05-01-2017:**
Since the live-boot worked fine, I decided to upgrade with a fresh install of 16.04. There were no problems until I installed the nvidia drivers, then it started to beep and shutdown all over again. The nvidia drivers seem to be the source of all this problems, but I'm unsure how it connects to the BIOS or hardware.

**Update 07-01-2017:**
Installed the most recent drivers (375.26) for my graphic card, from the ppa:graphics-drivers, and so far no problems. I have also launched games and the laptop is still working well, with no signs of the beeping-shutdown issue. It might return in the future (I'm really pessimistic), but if anyone stumbles upon this problem too, here are my 2 cents:
* Revert to Intel/Nouveou drivers first, check if it still persists;
* If you must really use Nvidia, try the latest drivers in the oficial repositories;
* If it fails, only then try the ones in the ppa. Check the suitable driver in the oficial website (e.g. in my case, I go to the geforce website). Please read well the instructions in the ppa, if you are unfamiliar with how ppa's work, read a bit before plunging in! (also, learn this amazing command: ppa-purge ppa:name/ppa)

---

### Post by mc4man on 2016-12-27
What's not clear - when using the Intel gpu is all ok or do you get this beep/shutdown issue also?

---

### Post by Bucky Ball on 2016-12-27
[QUOTE=ClaraMFerreira]Frustrated, I tried again the same fix as before: worn out the battery a bit, recharge at 100% with the laptop shutdown, and boot.[/QUOTE]

So all this is happening on battery power? Out of curiosity, does the exact same issue occur when you are running ONLY on the wall power, no battery? Take battery out, plug into wall socket, confirm you have exactly the same issue.

In my experience, when a battery is dying it can cause odd, unexplained things to happen, even when not in use but only attached to laptop, so take the battery out of the computer and test.

Good chance your issue lies elsewhere, but no harm in ruling things out as well as in. :)

---

### Post by ClaraMFerreira on 2016-12-27
Thank you both for your answers.

It occurs in both the intel and nvidia profiles :(

The problem occured with the battery on and cable plugged at first. I also tried with battery only, and cable only (no battery) and still the same issue, didn't fix it. I am unsure why the recharge worked the first two times. Unfortunately it's not fixing my problem now, so I'm not sure if it's the battery. :(
I will take the battery out from on now, just to be sure.

---

