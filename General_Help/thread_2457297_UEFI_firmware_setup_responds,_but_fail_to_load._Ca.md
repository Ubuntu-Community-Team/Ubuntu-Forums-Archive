---
title: "UEFI firmware setup responds, but fail to load. Cannot enter setup."
date: 2021-01-29
forum: General Help
---

### Post by Vidar30 on 2021-01-29
I'm using an UEFI menu for my dual-boot system. 
Windows 8.1 and Ubuntu 21.04. Lenovo ideapad. Secure Boot enabled.

UEFI firmware setup fails to load whether it's called by **F2 **during boot, or if it is called from **Windows 8.1** - whereas I select for the option to reboot into UEFI setup. In addition, I have installed an utility (**EasyUEFI**) for windows, which also got an option for reboot into UEFI setup. I have also tried to access setup through **windows installation usb-stick**, without result.

The strange thing is, the system reacts when I for instance press F2 during boot. I don't know, but it could be setup begins loading, but aborts. Visually, the screen gets a quick and temporary 'blank-out' effect and if I press F2 repeatedly, the system halts - it seems a workload appears which has to be completed. After failing to load UEFI firmware setup, the system enters boot menu. The **boot menu** also got a entry for 'setup' which should load setup, but needless to say it doesn't.

I don't know which questions I should be asking. The software which produce the firmware setup menu, does it reside in nvram or at the uefi partition? Should I expect to be able to reset the system using a windows installer usb-stick? If I reinstall, will I still be able to install ubuntu or is there a chance for Secure Boot will block?

Strange situation. I will appreciate suggestions and comments.

---

### Post by CelticWarrior on 2021-01-29
UEFI is firmware just like the old BIOS was. It resides in a chip somewhere in the motherboard.
If you can't access the UEFI settings then you have a problem indeed. Typically, in a desktop, the first thing to try would be a reset and that could achieved either by shortening a specific jumper, if available, or by removing the battery for some seconds. How to do it in a Lenovo Ideapad I don't know, better to contact your tech support.

---

### Post by tea for one on 2021-01-29
Do you have the Novo button? [https://support.lenovo.com/gb/en/solutions/HT500216](https://support.lenovo.com/gb/en/solutions/HT500216)

Secondly, when you are using Ubuntu, open a terminal and enter:-
```
sudo systemctl reboot --firmware-setup

```

---

### Post by CelticWarrior on 2021-01-29
If the above doesn't work either, contact tech support.

---

### Post by Vidar30 on 2021-01-30
Yes, got a novo button. 

Pressing it gets me to a menu where I can choose setup, but instead of setup it give me boot menu.
Setup is basically not loading.

---

### Post by tea for one on 2021-01-30
Have you tried to access UEFI firmware via Ubuntu as I suggested in post 3?

Have you tried to access UEFI firmware via Windows as detailed in the Lenovo link?

---

### Post by oldfred on 2021-01-30
Microsoft has required UEFI fast start.
That is a setting to speed boot, by skipping the normal  BIOS/UEFI scan of system for what hardware you have.
If no change then it does save a bit of time booting making Windows (and Ubuntu) seem like it boots faster.
But it often is so quick you do not have time to press f2 to get into UEFI. That is why both Windows & Ubuntu have menu items to boot into UEFI.

Or a full cold boot normally works. That is full system shutdown, remove all power and then boot. If battery not removeable, vendors usuually have a tiny pin hole for reset. Or you have to remove coin battery on motherboard, or jumper two pins on motherboard to reset UEFI. If you have to reset UEFI, you probably need to review settings as it will revert to defaults.

---

### Post by Vidar30 on 2021-02-03
Yes, I have tried all the described alternatives. 

The problem doesn't seem to be about selecting 'setup' but what happens after it is selected, when it's supposed to load.
My laptop got a 'novo' button which is the tiny pin hole described by oldfred.

Setup simply won't load. It is as if clicking a broken link. 

Pure speculation, but I wonder if it can have anything with Secure Boot to do. Perhaps the system got something messed up, per association I imagine setup is designed to only be accessible by signed software. It's like access to setup is being blocked.

---

### Post by CelticWarrior on 2021-02-03
No, nothing to do with Secure Boot. How would users be able to re-enable Secure Boot once disabled then? I'm sure you understand it's nonsense.
Your problem is somehow unique as in I've never seen such.

Having tried all the alternatives and if it behaves like you say and having no possibility to reset please contact the manufacturer's tech support.

---

### Post by Vidar30 on 2021-02-03
Here is a link to a video of me attempting to enter BIOS setup in what I suppose should be the 'safest' alternative: the 'novo' button, which in lenovo-speek is a failsafe alternative, should work when nothing else does. 

[https://www.youtube.com/watch?v=gKRM8FbFshU](https://www.youtube.com/watch?v=gKRM8FbFshU)

The reason I associate the behavior with Secure Boot is because it seems like access is blocked. 
Furthermore, and I am of course unsure, since I don't access Setup regularly, but it seem to me the problem may be have arose with Virtualbox interacting with Secure Boot settings. Maybe it triggered a switch which is stored or similar? As far as I am aware it is the only software I have ever installed which interacted with Secure Boot or UEFI at all.

---

### Post by CelticWarrior on 2021-02-03
Everything interacts with the firmware with or without Secure Boot.
Indeed, Virtualbox installs at least one virtual driver (unsigned) that won't load with Secure Boot enabled. So, either Secure Boot is disable - the usual solution - or users have to manually sign/authorize the driver with the mokutil tool.
Either way and even if unsuccessful using the tool, the firmware settings are (should be) always accessible. But please describe what happened around the installation of Virtualbox, maybe there's some clue I'm overlooking, but again I've never seen such a thing. That said and whatever the cause was I'm afraid we won't be able to help you.

---

### Post by tea for one on 2021-02-03
I agree with CelticWarrior, it looks like the Lenovo UEFI firmware is misbehaving and I reckon that you will have to seek help via Lenovo forums or Tech support.

5 shots in the dark:-

Boot menu and Bios set up somehow swapped - try novo button and Boot menu?
Did you try System Recovery?
Boot menu > Lenovo Recovery System?
Do you have the latest UEFI firmware from Lenovo?
Boot up a live session using 20.04 and try the command to reach the UEFI set up (I noticed that you were using 21.04, which is in development)

---

### Post by Vidar30 on 2021-02-03
Thanks for response.

I have tried all the options available on the 'novo-menu' - system recovery don't work. The recovery partition is deleted (small hard drive system). Not sure if the bios version I have is the most recent or not. Unsure how it will work if I try to boot another OS.

**Digression**. This sounds silly, sure - upon booting a usb stick with another linux on, 'MOK management' screen appears, which I so far have decline exploring further. I think all it wants is for me to enter a password or something and have the usb included on a list of secure systems, a list of software with 'okay' from me. However, fear of digging myself into a even deeper hole has got me to avoid the whole situation. But I suppose I can reasonably 'enroll a key from disk' and use an usb-stick without fear of consequences or complications. It's generally unknown territory in a special situation. But as said, I think the MOK interaction screen is about adding the usb stick to the MOK database or something similar.

**Regarding Virtualbox.**
As far as I can tell, nothing unusual has explicitly happened while using VB. From what I recall, upon attempting to use VB for booting a guest system, the system prompted a MOK screen which wanted me to create a password which I had - for some reason - to repeat upon next (host system) reboot. Nothing unusual, but I might not have noticed anyway being unfamiliar with Secure Boot. It has usually been disabled.

I had a **noteworthy event** when following direction from someone helping me on IRC. The guy suggested I should try to load BIOS setup from grub command shell. Without remembering all details, I did an **update-grub**. And - surprise - the boot-menu now didn't load any longer. I almost bricked the system. Luckily, 'novo-menu' -> 'system recovery' alter boot order, making Ubuntu boot first instead of boot-menu (which wouldn't load). When I select 'system recovery' I get a screen telling me something about recovery not available and system being reset to default values. Something like that.

The boot-menu works fine now. Unsure why. First I tried it as a single boot selection without changing permanent boot order. It worked fine, so I changed boot order back to boot-menu first, which is what you see at the video (sorry about the garbage entries, ignore). I have contacted Lenovo and awaiting answer, but I doubt there is hardware malfunctioning. Everything works fine. So I doubt Lenovo will be able to tell me any much more than anyone else.

I think the effect update-grub had on the boot process is interesting. As far as I understand, update-grub shouldn't have effect outside of the ubuntu partition. Since I use an UEFI generated boot menu, I assume it's only the EFI-partition is accessed at such an early stage of boot. Or could it be the NVRAM which was affected? It seem unreasonable the EFI partition to be affected by grub-update. I'm not sure if those are good questions, but the effect by update-grub was interesting. I could try to check for repeatability if desirable.

---

### Post by oldfred on 2021-02-03
While this sounds like a bit older system, Lenovo is now adding systems to fwupd, so Linux can update its UEFI.
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)
Looks like mostly Thinkpads.

Also Lenovo has announced its new systems will be UEFI only or UEFI class 3, no CSM.
It means a new UEFI, and then whatever changes that makes, hopefully dual boot still works.
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

And request for MOK key is related to UEFI Secure Boot.
Ubuntu cannot provide key for proprietary software. A user who believes software is secure and then takes responsibility can provide his own key. This is usually required for proprietary video drivers like nVidia or WiFi drivers that are proprietary.

Machine-Owner Key (MOK) management
[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

---

