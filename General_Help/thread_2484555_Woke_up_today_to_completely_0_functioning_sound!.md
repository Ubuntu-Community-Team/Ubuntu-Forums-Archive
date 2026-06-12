---
title: "Woke up today to completely 0 functioning sound!"
date: 2023-03-02
forum: General Help
---

### Post by raderall on 2023-03-02
There seems to be an on going problem with the recent Xubuntu updates where a lot of the monitors that weren't made in recent times are unable to play audio output to plugged in speakers. 

Someone posted a fix here that seems to work. Me I just got to the point and plugged them into the back of my 
[https://askubuntu.com/questions/1403575/hdmi-audio-issue-ubuntu-22-04](https://askubuntu.com/questions/1403575/hdmi-audio-issue-ubuntu-22-04)


It simply says to change the "GRUB_CMDLINE_LINUX="" to,  
GRUB_CMDLINE_LINUX="intel_iommu=on,igfx_off"

---

### Post by HermanAB on 2023-03-03
‘Woke’ - there, that is your problem!

Jokes aside, you should look at the first error. There is a left over lock file that you need to delete. A reboot may also help to get the drivers loaded.

---

### Post by ajgreeny on 2023-03-03
When you say "woke" do you mean coming out of suspend mode or are you rebooting?

---

### Post by ActionParsnip on 2023-03-03
Please follow the below
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Give the output of step 3 if you reach it

---

### Post by raderall on 2023-03-03
I'm doing step 3 now. 
the first part of step 3 gave this after I punched it in.
HTTP request sent, awaiting response... 404 Not Found
2023-03-03 08:04:49 ERROR 404: Not Found.

and then the "bash alsa-info.sh --stdout" did nothing. 

uname -r tells me this "5.19.0-35-generic"
 Is it suppose to list an Alsa driver too?

Everything before this worked perfectly.

And I remind you the splash screen before the Xubuntu start displays something wrong with the audio codecs and another error and people here are telling me there appear to be problems up stream. If I could get that splash screen before desktop loads posted here this would be a big help. I use sudo nano in the terminal to open "what file exactly? then post the messages in here. and I tried doing a repair reinstall of my Xubuntu, however no dice, still no sound.

---

### Post by raderall on 2023-03-03
I removed that lock file, reinstalled pipewire, again still no sound, and that same error message is back. I'm sure the problem is upstream as I'm also having problems when I hibernate the computer, it just comes right back on no matter what.

---

### Post by ActionParsnip on 2023-03-03
Yeah seems to be gone. I get a 404 here too...

---

### Post by raderall on 2023-03-04
I figured out the problem, things upstream updated wrong as I had 99.2% of my harddrive used. I had a left over partition space that's 3 times the size, however I had it for a previous XUbuntu Installation that I bricked and I needed to keep it to back up important files. And I could never get that partition to merge with the main. So I removed it and planned to reintall Xubuntu fresh and discovered I needed the USB to be set up with NBR, NOT GPT, so now I'm stuck at a GNU Grub menu. If you know the correct codes to boot into my Windows 11 partition that would make it so easy. It's either that or find out how to get Unetbootin working on this Tinycore SD, and how to even view usbs or additional hard disk contents. Or wait until tomorrow to use a family members computer to get that Xubuntu 22.10 on the USB with the correct NBR set up. and also in the bios or USFI or whatever, There's a left over Debian and two Ubuntus listed. How do I remove those?

---

### Post by ajgreeny on 2023-03-04
Great!

Please now mark the thread as **SOLVED** from the Thread tools menu up top. It is a big help to others searching the forum.

---

### Post by raderall on 2023-03-04
Seems experimenting with Tinycore somehow fixed my usb so I got Xubuntu 22.10 installing and running, but now that problem where I cannot get my monitor to play audio, which I prefer as the plug is much closer to the monitor than the desktop machine, is back. it seems previously a setting known as pro sound worked for this which got lost. if you know a way to get it to detect the monitor as an option to choose let me know.

---

### Post by raderall on 2023-03-04
Okay still nothing from my monitor speakers! the splash screen lists quickly something about invalid or missing codecs for my HDA Intel PCH sound chip, and something above it about a bad nod and another word. I do not know where or how to retrieve that predesktop splash list. How do I locate that?

---

### Post by raderall on 2023-03-05
I still do not know what "File" the splash screen load logs are or where to go to find that! repeated google searches have been not helpful at all. I guess I have to take a picture with my cell real quick and upload it huh? and I plugged the speaker cable into the back of my desktop and now it works. I mean it is better sound quality. it seems like some update removed the "Pro Audio" from the list of options, and I have no clue even after reinstalling this after another problem upstream how to get that setting back. at this point I don't want to be bothered with all this. but I will get that picture of my splash screen listed arrows involving RGF or Nod and audio codecs.

---

### Post by raderall on 2023-03-15
Thanks for doing virtually nothing for me. I need to know how to recover the log that the splash screen posts before the desktop boots up. But it seems like a wider problem that the most recent Xubuntu update seems to kick audio support for alot of older monitors. I did however just plug the speakers directly into the back of my pc and it's kinda a better sound quality anyhow so.

---

### Post by DuckHook on 2023-03-15
> **raderall said:**
> Thanks for doing virtually nothing for me.
There are no guarantees that forum members can help you. We collectively try our best, but if your problem is unique and not encountered here before, then there are limits to what knowledge any of us can bring to bear. Moreover, we all have private lives. As a user&#8209;run volunteer forum, we help in our spare time. You yourself are a case in point: apparently not revisiting for a week.

To keep your issue in the public eye, you can bump your thread every 12 hrs to dredge it up from the bottom of the sea.
> I need to know how to recover the log that the splash screen posts before the desktop boots up.
As to your problem, you have asked how you can bring up the "splash screen" from the boot process. This is neither possible (without videoing the process) nor necessary. What I assume you want are the error messages.

The traditional way to see your boot process is:```
sudo dmesg
```
The modern way to see your logs, filtered only for errors:```
journalctl -p 3 -xb
```Post the output back to this thread.
> But it seems like a wider problem that the most recent Xubuntu update seems to kick audio support for alot of older monitors. I did however just plug the speakers directly into the back of my pc and it's kinda a better sound quality anyhow so.
I have a similar problem to yours in that my HDMI sound sink has disappeared altogether The cause may or may not be the same. This happened after an upgrade some weeks ago. In my case, I don't use HDMI audio, preferring to plug into the speaker outputs for better sound, so the problem is so low priority that I never really researched it. This is an instance of what I stated above: that forum members may simply have no answer to your problem.

For the sake of curiosity, I will do a bit of digging. But no promises. My resources are no better than yours&#8212;consisting of a series of websearches. What I can do, you can do.

---

### Post by DuckHook on 2023-03-15
Found this:  [https://askubuntu.com/questions/1403575/hdmi-audio-issue-ubuntu-22-04](https://askubuntu.com/questions/1403575/hdmi-audio-issue-ubuntu-22-04)

It didn't help me but it may help you.

---

### Post by MAFoElffen on 2023-03-15
+1 to try... (Adding 'intel_iommu=on,igfx_off' to the grub command line argument)... but does or doesn't work, based on the infinite combinations of hardware combinations. 

To see if you need that boot parameter option, normal output of
```

sudo dmesg | grep -i 'dmar'

```
Is going to look like this:
```

[    0.015423] ACPI: DMAR 0x00000000991E7000 0000A8 (v01 INTEL  EDK2     00000002      01000013)
[    0.015464] ACPI: Reserving DMAR table memory at [mem 0x991e7000-0x991e70a7]
[    0.294796] DMAR: Host address width 39
[    0.294798] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.294805] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 19e2ff0505e
[    0.294810] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.294815] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.294819] DMAR: RMRR base: 0x000000997e0000 end: 0x00000099a29fff
[    0.294823] DMAR: RMRR base: 0x0000009b000000 end: 0x0000009f7fffff
[    0.294826] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.294829] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.294832] DMAR-IR: Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.296373] DMAR-IR: Enabled IRQ remapping in x2apic mode

```
Abnormal output of that is similar to this:
```

[   31.698564] dmar_fault: 497 callbacks suppressed
[   31.698566] DMAR: DRHD: handling fault status reg 3
[   31.698570] DMAR: [DMA Read] Request device [01:00.0] fault addr 7ee29000 [fault reason 12] non-zero reserved fields in PTE
[   31.766887] DMAR: DRHD: handling fault status reg 3
[   31.766889] DMAR: [DMA Read] Request device [01:00.0] fault addr 7ee52000 [fault reason 12] non-zero reserved fields in PTE
[   32.770714] DMAR: DRHD: handling fault status reg 3
[   32.770717] DMAR: [DMA Read] Request device [01:00.0] fault addr 7ee52000 [fault reason 12] non-zero reserved fields in PTE
[   33.774278] DMAR: DRHD: handling fault status reg 3
[   33.774281] DMAR: [DMA Read] Request device [01:00.0] fault addr 7ee52000 [fault reason 12] non-zero reserved fields in PTE
[   38.688166] DMAR: DRHD: handling fault status reg 3
[   38.688171] DMAR: [DMA Read] Request device [01:00.1] fault addr 109698000 [fault reason 12] non-zero reserved fields in PTE
[   40.234258] DMAR: DRHD: handling fault status reg 3
[   40.234262] DMAR: [DMA Write] Request device [01:00.0] fault addr 1ffe2d000 [fault reason 12] non-zero reserved fields in PTE
[   40.234381] DMAR: DRHD: handling fault status reg 2
[   40.234383] DMAR: [DMA Read] Request device [01:00.0] fault addr 1ffe25000 [fault reason 12] non-zero reserved fields in PTE
[   40.234446] DMAR: DRHD: handling fault status reg 2
[   40.234448] DMAR: [DMA Read] Request device [01:00.0] fault addr 1ffe2a000 [fault reason 12] non-zero reserved fields in PTE
[   41.937178] DMAR: DRHD: handling fault status reg 3
[   41.937183] DMAR: [DMA Read] Request device [01:00.0] fault addr 1ffe2f000 [fault reason 12] non-zero reserved fields in PTE

```
That boot parameter usually handles that kind of work-around... Like I said, it depends on the specific hardware combination.

What I would suggest is to report this as a Bug to Launchpad filed against pipewire, and include
```

sudo dmidecode > ~/Documents/dmidecode.txt

```
Let the Dev's figure out what is wrong in the packages and code. This problem is not widespread, but is affecting you and 'DuckHook'... So it can be confirmed by DuckHook on that Bug Report. It's time to escalate it to the proper channels. (At least from my perspective.)

Just a suggestion.

---

### Post by DuckHook on 2023-03-15
> **MAFoElffen said:**
> What I would suggest is to report this as a Bug to Launchpad filed against pipewire, and include&#8230;

&#8230;Let the Dev's figure out what is wrong in the packages and code.
Excellent suggestion and aids in community efforts towards the fix.

Further research turned up this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2009136](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2009136)

This definitely addresses my problem.

The workaround is simple: when booting, use the older 5.19.0-32 kernel. The problem started with the latest kernel upgrade. Apparently, -35 has a regression that the devs are busy fixing. Hopefully, the next kernel release will deal with it. Until then, use the older kernel at boot and you should get your HDMI back.
> This problem is not widespread, but is affecting you and 'DuckHook'&#8230;
Actually, quite widespread and appears to affect almost all AMD graphics cards.

I've tagged it as "Yes, it affects me" to add my voice to the growing chorus.

@raderall

Your problem may be this one or it may be different. If booting into the -32 kernel does not work for you, then yours is probably a different problem. If the workaround is successful, then you should report on the launchpad page that it affects you too.

You might also wish to pin the 5.19.0-32 kernel and its related headers/libraries so that the next full-upgrade doesn't remove them.

---

### Post by raderall on 2023-03-25
journalctl -p 3 -xb was just what I was looking for! 
```
Mar 25 15:05:35 MasterPC kernel: usb 3-1: device descriptor read/64, error -71
Mar 25 15:05:35 MasterPC kernel: usb 3-1: device descriptor read/64, error -71
Mar 25 15:05:35 MasterPC kernel: usb 3-1: device descriptor read/64, error -71
Mar 25 15:05:35 MasterPC kernel: usb 3-1: device descriptor read/64, error -71
Mar 25 15:05:35 MasterPC kernel: usb 3-1: device not accepting address 4, error -71
Mar 25 15:05:35 MasterPC kernel: usb 3-1: device not accepting address 5, error -71
Mar 25 15:05:35 MasterPC kernel: usb usb3-port1: unable to enumerate USB device
Mar 25 15:05:35 MasterPC thermald[556]: Thermal DTS or hwmon: No Zones present Need to configure manually
Mar 25 15:05:35 MasterPC systemd-udevd[372]: event10: Failed to call EVIOCSKEYCODE with scan code 0x7c, and key c>
Mar 25 15:05:35 MasterPC kernel: hdaudio hdaudioC1D0: no AFG or MFG node found
Mar 25 15:05:35 MasterPC kernel: snd_hda_intel 0000:01:00.1: no codecs initialized
Mar 25 15:05:38 MasterPC lightdm[1788]: gkr-pam: couldn't unlock the login keyring.
Mar 25 15:05:43 MasterPC lightdm[1936]: gkr-pam: unable to locate daemon control file
Mar 25 15:05:55 MasterPC kernel: ntfs3: Unknown parameter 'windows_names'
```
I mean my OS is stable but are any of these errors causing lag or potential problems or vulnerabilities?

---

### Post by DuckHook on 2023-03-26
Your output implies that you are still using the *-35 kernel. I told you to go back to the *-32 kernel. Why aren't you?

---

### Post by raderall on 2023-03-26
So the Kernel I'm using atm, is alittle bit too new for some of my current apps or whatever. So I either need to wait a couple of months for them to catch up or is there a third party Kernel I could install or something? What are my options I'm alittle bit tired but can think more tomorrow.

---

