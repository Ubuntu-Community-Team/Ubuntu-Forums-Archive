---
title: "Laptop trouble sleeping properly (battery drain) - fresh install lacks hibernate?"
date: 2024-07-18
forum: General Help
---

### Post by csae2608 on 2024-07-18
Hello,

ii have noticed that the laptop here rather fresh Thinkpad with 8th gen Intel processor looses lot of battery during sleep (lid closed).
and after some day if i open lid it would no longer have battery.

it is set to 

[HTML] cat /sys/power/mem_sleep
s2idle [deep]
[/HTML]

but it still looses alot of energy during sleep which is not appropriate.


this laptop has also AMDGPU installed so maybe this could cause the battery drain?


Now i was thinking of reinstalling Ubuntu but i doubt it would help the cause;

i found that Ubuntu does not install Hibernate mode;

is there an option during installation to make this standard, like in the past, where it would use 1.5x RAM for a proper Hibernate swap partition?
with 16 GB RAM that would be around 22.5 GB which i could afford; then i could initiate hibernate properely instead of just closing the lid and loosing so much energy during sleep.


thanks.

---

### Post by csae2608 on 2024-07-18
[HTML]Failed to hibernate system via logind: Not enough swap space for hibernation

[/HTML]


failed to add that the laptop is also dual-booting windows/ubuntu (22.04).
maybe therefore there is such a big power drain during suspend? the ubuntu has its own disk, though.

---

### Post by QIII on 2024-07-18
Moved to **General Help**

---

### Post by currentshaft on 2024-07-19
Did you install the latest firmware updates?

---

### Post by genesis170 on 2024-07-19
Hey csae2608,


While you troubleshoot hibernation, have you considered looking into online jobs that offer more flexibility? It might be a good fit for you if you're looking to optimize your schedule. This could free up some time to tackle those tech issues at your own pace, or simply give you more control over your [essentials]("https://genesis17.com/").

---

### Post by csae2608 on 2024-07-19
> **genesis170 said:**
> Hey csae2608,


Hibernate is still there in Ubuntu, it just might not be enabled by default. You can definitely try enabling it and see if that helps with the battery drain during sleep.  There are guides online for enabling hibernation on Ubuntu with AMD GPUs.


it would be nice if the installer gave an option to enable it by default; also to handle the size of swapfile if one chooses (automatic install); it used to choose a swapfile 1.5x orso the size of installed RAM; could ask if it is enough or if wants to adjust the size of swapfile to take into account future ram changes.

always found it difficult to implement hibernate after debian/ubuntu was installed;


now for sleep:

lost around 28% of battery just in 1 day and some hours, which seems definitely excessive to me.
only ting is , have ethernet cable attached, but that should not make any difference; wlan/bluetooth/wwan is disabled in bios, no usb attached;
bit disappointing, to say, that moderrn laptop have difficulty sleeping.

---

### Post by csae2608 on 2024-07-19
> **currentshaft said:**
> Did you install the latest firmware updates?

well, yes, somehow, laptop has dual-boot so i have easy Windows Firmware updates,
but i have seen that Bios has gone from 1.36 (actual bios on laptop) to 1.37, so will install and see if this changes something.

I i would have only Ubuntu installed, it would be easy to miss those firmware updates, or how could i achieve them?


thanks

---

### Post by csae2608 on 2024-07-19
[HTML]fwupdmgr get-updates
Devices with no available firmware updates: 
 • Embedded Controller
 • SA400S37240G
 • System Firmware
 • UEFI Device Firmware
 • UEFI Device Firmware
 • UEFI Device Firmware
 • UEFI dbx
Devices with the latest available firmware version:
 • HFM512GDHTNG-8710B
No updates available
[/HTML]

the Linux Firmware updater does not offer the new BIOS update, probably because the E590 is an older laptop with middle/class/lower hardware.

So i need probably best Windows to get the updates in place?

downloading BIOS manually is also an option, if that is what you meant with the Firmware updates.

---

### Post by currentshaft on 2024-07-19
fwupdmgr requires the BIOS option to allow "Windows" BIOS updates to be enabled to work.

[https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh](https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh) is another tool you can also use to debug sleep issues.

---

### Post by csae2608 on 2024-07-19
> **currentshaft said:**
> fwupdmgr requires the BIOS option to allow "Windows" BIOS updates to be enabled to work.

[https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh](https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh) is another tool you can also use to debug sleep issues.



well , thanks, might look into this.

have updated now to latest bios 1.37 from lenovo, will see if it helps.


however, automatic installer has mad no swap-file available, so i wonder how i can enable hibernation?

the idea being, that the lptop after some time in suspend, say 2 hourse, does hibernate, which seems reasonable to me; also , the modern battery sometimes does not hold a charge that good / eg. depletes itself after fewer charging cycles.

remember that on older powerbook, even after long time in "suspend" it still would turn on and let do basic tasks.

--------
[HTML]rich@rich-ThinkPad-E590:~$ sudo blkid | grep swap
(no result)[/HTML]

---

### Post by currentshaft on 2024-07-19
> **csae2608 said:**
> well , thanks, might look into this.

have updated now to latest bios 1.37 from lenovo, will see if it helps.


however, automatic installer has mad no swap-file available, so i wonder how i can enable hibernation?

the idea being, that the lptop after some time in suspend, say 2 hourse, does hibernate, which seems reasonable to me; also , the modern battery sometimes does not hold a charge that good / eg. depletes itself after fewer charging cycles.

remember that on older powerbook, even after long time in "suspend" it still would turn on and let do basic tasks.

--------
[HTML]rich@rich-ThinkPad-E590:~$ sudo blkid | grep swap
(no result)[/HTML]

I wouldn't worry about the swap yet. Run the Intel script I linked to debug your sleep state first.

---

### Post by csae2608 on 2024-07-19
thank you, that was helpful.

[HTML]sudo ./s0ix-selftest-tool.sh -s

---Check S2idle path S0ix Residency---:

The system OS Kernel version is:
Linux rich-ThinkPad-E590 6.5.0-44-generic #44~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Jun 18 14:36:16 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

---Check whether your system supports S0ix or not---:

Low Power S0 Idle is:0
Your system does not support low power S0 idle capability.     
Isolation suggestion:     
Please check BIOS low power S0 idle capability setting.
[/HTML]


might have to ask @Lenovo if they can enable this function in BIOS update?
the laptop has i7-8565u cpu that should be able to save power efficiently?

---

### Post by ne29914 on 2024-07-19
Hibernate is disabled on (y)Ubuntu and needs to be actively enabled, which is not easy. There might be a little program to do this, I haven't checked.

Here's the recipe;

PS: I've never gotten it to work with a swapfile, you definitely need a swap partition.

---

### Post by csae2608 on 2024-07-19
i remember using debian and the installer would automatically present me with a swap partition when doing automatical install, around 1.5 size of ram;
Ubuntu has improved on installation routine somehow, but this seems a bit cleearly a regression if automatic install on a dedicated HDD/SSD does not give enough space for swappartition/hibernation.

EDIT: have checked and there is definitely no swap space; am i to blame that i did not "manually" partition the drive? would think not, this should be offered a standard, if the feature is useful (as it clearly seems).

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293994&stc=1[/IMG]

---

### Post by ne29914 on 2024-07-19
I can't comment on installing Ubuntu, as I run Lubuntu which uses a different installer.

But yes, I always choose manual partitioning, as I like to keep / and /home separate. This also includes defining a swap partition.

---

### Post by him610 on 2024-07-19
> lost around 28% of battery just in 1 day and some hours, which seems definitely excessive to me.
Why not just turn it off for anything longer than an hour?

---

### Post by csae2608 on 2024-07-20
> **him610 said:**
> Why not just turn it off for anything longer than an hour?

the idea is to pick where left , and therefore use hibernate;


how i tried this approach here

[https://www.wikihow.com/Attach-a-Swap-Partition-to-Linux](https://www.wikihow.com/Attach-a-Swap-Partition-to-Linux)


and it seems to function halfway;

with 

"sudo pm-hibernate" or "sudo systemctl hibernate" it effectively would "hibernate" , but instead of picking up where it left, it would not save the RAM state, instead just shutting down the machine; and upon clicking the power button, it would normally restart;

is this the wrong method to attach the swap to Ubuntu?

---

### Post by #&amp;thj^% on 2024-07-20
Ubuntu has made it much harder to hibernate from 22.04 thru 24.10
check with:
```
sudo dmesg|grep hibernation
```
> **csae2608 said:**
> 
I i would have only Ubuntu installed, it would be easy to miss those firmware updates, or how could i achieve them?
thanks
I use topgrade for all,  Topgrade: A single utility to take care of all kinds of updates: [https://itsfoss.com/topgrade/](https://itsfoss.com/topgrade/)
I've used that for a little over 2 yrs now, and not one mishap in that time. (This is needed "fwupd ")

---

### Post by csae2608 on 2024-07-20
> **ne29914 said:**
> Hibernate is disabled on (y)Ubuntu and needs to be actively enabled, which is not easy. There might be a little program to do this, I haven't checked.

Here's the recipe;

PS: I've never gotten it to work with a swapfile, you definitely need a swap partition.



Thank you very much!

This enabled the Hibernate after i manipulated the SSD by inserting a Swap partition via a Gparted Livesystem.

Still investigating the Battery drain , though

("_sudo pm-suspend" is much more effective than just closing the lid on the laptop_ | > wrong assertion, it is not so much more effective, sucks battery just as closing lid;)

---

### Post by ne29914 on 2024-07-20
> **csae2608 said:**
> Thank you very much!

This enabled the Hibernate after i manipulated the SSD by inserting a Swap partition via a Gparted Livesystem.

Still investigating the Battery drain , though

("sudo pm-suspend" is much more effective than just closing the lid on the laptop)

Dunno why you're mentioning "pm-suspend". It should be "pm-hibernate" if you're using pm-utils.

The basic command is:
```
sudo systemctl hibernate
```
Complete laptop status will be be stored to disk and the computer will turn off. No battery drain at all.

---

### Post by csae2608 on 2024-07-22
> **ne29914 said:**
> Dunno why you're mentioning "pm-suspend". It should be "pm-hibernate" if you're using pm-utils.

The basic command is:
```
sudo systemctl hibernate
```
Complete laptop status will be be stored to disk and the computer will turn off. No battery drain at all.

yeh, that seems to be about the only method of saving battery on newer laptops (besides shutdown or going into BIOS and "disable internal battery")
but to do that , you need to have hibernation partition / swapfile in place; quite cumbersome to do this, should be made optional by default even when automatic install;

wonder what the laptop is doing even when shutdown that it looses so much energy fast.

---

### Post by currentshaft on 2024-07-22
> **csae2608 said:**
> yeh, that seems to be about the only method of saving battery on newer laptops (besides shutdown or going into BIOS and "disable internal battery")
but to do that , you need to have hibernation partition / swapfile in place; quite cumbersome to do this, should be made optional by default even when automatic install;

wonder what the laptop is doing even when shutdown that it looses so much energy fast.

Has nothing to do with "newer laptops". I have several brand new ThinkPad running Ubuntu 24 which suspend fine on lid close and do not lose battery.

You need to check BIOS settings or ask Lenovo for help.

---

### Post by csae2608 on 2024-07-24
these are the options that Ubuntu 24.04 offers in "power" section, hibernate nowhere to be seen as an option.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294007&stc=1[/IMG]

---

### Post by ne29914 on 2024-07-24
Dunno about Ubuntu, I'm on Lubuntu.
But my options are:
1: slam the lid.
2: invoke the "Leave" menu where the following options are:
Hibernate
Leave
Logout
Reboot
Shutdown
Suspend

---

### Post by csae2608 on 2024-07-24
used Lubuntu in the past, always liked very much, but htis surprise me> should Lubuntu do better on General options.
Maybe the issue is also just Laptop specific, and Ubuntu does not offer the hibernate beccause if have DualBoot with Windows, or this sleep state S0 is not available on this laptop< 
wiill checck on Lubuntu, thanks for the tip. Only issue could be that the AMDGPU driver are tailored specifically to Ubuntu LTS versions, that could be troublesome installing those on Lubuntu then.

---

