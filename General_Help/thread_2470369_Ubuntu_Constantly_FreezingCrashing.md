---
title: "Ubuntu Constantly Freezing/Crashing"
date: 2021-12-27
forum: General Help
---

### Post by thatrius on 2021-12-27
I'm on Ubuntu 20.04, and my computer has been freezing more and more often lately. It's gotten to the point where it happens 10 minutes in after starting up, and the only thing I can do is either cold reboot, or the Alt+PrtSc+REISUB key-combo. 

I have no idea what might be causing this. My initial suspicion was low swap space, but even after setting swappiness to 90 it still crashes, and it doesn't look like the machine even uses any of it anyway.

I'm on a desktop with 32G RAM between 2 HyperX sticks. My graphics card is a GeForce GTX 1060. I also have all the drivers up to date.

Also it's worth noting that previously, the freezes seemed to coincide with USBs being plugged in/out, but since the freezes happen regardless now, it could have been a simple coincidence.

Please help!

---

### Post by thatrius on 2021-12-27
Just went ahead and upgraded to 21.04, and the problem doesn't seem to have recurred yet. I *was* greeted with a healthy 20+ "System Problem Detected" popups upon reboot though, not sure what that was about...

Hopefully it doesn't freeze again... I'll post an update later on whether it does, maybe 20.04 is just a buggy version or something ¯\_(&#12484;)_/¯

---

### Post by thatrius on 2021-12-27
Welp, it did it again. Not even REISUB worked to shut it down safely this time, now I gotta pull the plug each time it crashes.

I am back to being in very dire need of advice. Any help would be really appreciated

---

### Post by HermanAB on 2021-12-28
Try booting with the install media - do not install - just let it proceed to the desktop and play with it.  If it doesn’t crash then the problem is likely the video device driver since the install program uses a simple generic driver.

---

### Post by tea for one on 2021-12-28
Could be a failing HDD or SSD?
Perhaps you can try a [COLOR="#0000FF"]live session[/COLOR] for a few hours to see if the freezing/crashing persists?

Ubuntu does not ship with REISUB fully enabled.
It can be enabled by editing a system configuration file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**
By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

Lastly, there is a recently created utility, designed to provide relevant system information so that forum members can offer suitable advice.
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

---

### Post by Autodave on 2021-12-28
If you are using any USB hubs, disconnect them and see if that helps.

---

### Post by thatrius on 2021-12-28
Thanks for all the help!

Okay I think it *was* the drivers  - I tried a live boot, and interestingly enough it didn't seem to want  to crash, at least for the hour or so that I left it on. 

I also ran journalctl -b -1 -e and it returned what seems to be some crash logs, most of which mentioned NVIDIA. Followed [this]("https://www.linuxcapable.com/how-to-install-or-upgrade-nvidia-drivers-on-ubuntu-21-10-impish-indri/#ftoc-heading-3") tutorial on updating graphics drivers, and installed a 495 beta (the previous was 460). 

No  crashes so far this morning, so I think it may have been fixed. Coud've  sworn I had my graphics drivers up-to-date. The only other ones that  appeared in Software & Updates had lower numbers (except the X.Org X  one), so I dunno.

---

### Post by TheFu on 2021-12-28
When it comes to GPU drivers, don't go out and download them like you would for Windows.
Use
```
sudo ubuntu-drivers autoinstall
```
This gets the drives that Canonical has tested with Ubuntu libraries and are built specifically for Ubuntu systems.  It also won't grab the wrong version for the specific GPU.

---

### Post by thatrius on 2021-12-29
Good to know, thanks! Running nvidia-driver-470 now

495 was mostly okay, but there did happen to occur a single crash under its supervision. The journalctl error was "nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000927c:0:0:0x0000000f"

No idea what this means, but perchance it can serve to aid someone who is more knowledged than I, and who also happens to be installing the NVIDIA 495 beta driver

---

### Post by TheFu on 2021-12-30
Never install a beta nvidia driver unless you expect crashes.

---

### Post by thatrius on 2021-12-31
Well it seems I'm back to square one.

My computer has fallen back into its old habits of crashing regularly, leaving only a few minutes between freezes. 

Journalctl is still spamming the same error - nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000927c:3:0:0x0000000f

Literally nothing has changed since installing the 470 driver, which worked perfectly fine for 2.5 whole days. Is there any way to tell what could be wrong with it?

---

### Post by tea for one on 2022-01-01
You replied in this thread [https://ubuntuforums.org/showthread.php?t=2467826&page=6&p=14073390#post14073390](https://ubuntuforums.org/showthread.php?t=2467826&page=6&p=14073390#post14073390) where the OP reported that the solution was to use Ubuntu 21.10. 
Have you tried this version?

Also, there is a very useful utility, which will supply a software and hardware report so that forum members can see relevant details:-
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

---

### Post by TheFu on 2022-01-01
I'd suspect the GPU or PSU or a cable AFTER going through all the settings, looking for something non-standard.  Have you posted to the nvidia support forums with this issue yet?

I'm not seeing any issues with my GT 1030 using 
```
nvidia-compute-utils-470        470.86-0ubuntu
nvidia-driver-470               470.86-0ubuntu
nvidia-kernel-common-470        470.86-0ubuntu
nvidia-kernel-source-470        470.86-0ubuntu
nvidia-settings                 470.57.01-0ubuntu
nvidia-utils-470                470.86-0ubuntu
```
My kernel is 5.4.0-91-generic. I didn't patch over Xmas. Today is patch day here.

---

