---
title: "[SOLVED] No Sound"
date: 2008-04-14
forum: General Help
---

### Post by Dumbestcrayon on 2008-04-14
Im sure you have read this before and are probably tired of reading it.
I have searched for three days because I dont like posting for help especially if I can find it myself. But like I said I have been looking for three days and I have found ALOT of great information but still havent fixed my problem. I am kinda new to linux so please be patient with me and thanks alot in advance for any of your help.

I have no sound. When I click the sound icon on the top I get this message "No volume control GStreamer plugins and/or devices found." The information that I HAVE gotten is:

I have found my soundcard information when I did the command "lspci -v" which is..

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: fast devsel, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

I dont know if the bottom line is the problem or not because it says <access denied>

I checked Synaptic under libraries and gstreamer0.10.alsa is showing installed

I also checked [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel) and I believe the bottom one is my sound card which would be snd-hda-intel

This is where I am currently lost because I dont know what else to do

---

### Post by spiderbatdad on 2008-04-14
Try this please:
```
sudo depmod -a
sudo modprobe snd-hda-intel
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
sudo modprobe snd-seq-oss

```

Reboot.
If that fails, try to follow these instructions.[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

---

### Post by Dumbestcrayon on 2008-04-14
yeah man I looked at those instructions and Im not understanding them.
The message Im getting now, and was before, is 

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

Im assuming my sound card isnt configured.

I followed [THESE INSTRUCTIONS]("http://ubuntuforums.org/showthread.php?t=205449") and got to step 4 and when I put that line in it just goes straight to the next line with no confirmation or anything..not sure if its supposed to or not but i went on to the next step and added

like this..

brett@brett-laptop:~$ sudo modprobe snd-hda-intel
brett@brett-laptop:~$ 

Still got no sound card found and Im not sure where to go from here

---

### Post by Tews on 2008-04-15
I had that problem and solved it by upgrading to the latest Alsa version ... go here for a quick way to do it ....  [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24]("http://ubuntuforums.org/showpost.php?p=4298894&postcount=24")

---

### Post by Dumbestcrayon on 2008-04-15
> **Tews said:**
> I had that problem and solved it by upgrading to the latest Alsa version ... go here for a quick way to do it ....  [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24]("http://ubuntuforums.org/showpost.php?p=4298894&postcount=24")

Hey I want to thank you alot because I went there and followed the instructions and It didnt work at first but I ended up having to go to System-Administration-Software Sources and I had to check every box under the "Ubuntu Software" tab except the bottom one "Installable From CD-Rom/DVD", that one needs to be unchecked because it will automatically try to update from the cd first [which you dont want]. Then make sure to check everything under "Third-Party Software" and "Updates". Then I redownloaded the two files and ran the script again.

Problem solved.

And I want to thank Temüjin for helping me over AIM with it.

---

### Post by Tews on 2008-04-16
Thats what we're here for!  :lolflag:

---

