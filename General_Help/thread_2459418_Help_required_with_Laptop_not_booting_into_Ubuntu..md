---
title: "Help required with Laptop not booting into Ubuntu."
date: 2021-03-18
forum: General Help
---

### Post by panasonic57 on 2021-03-18
Hi,
I am having trouble getting my Laptop to boot, it has Ubuntu 18 ????? installed ( Cant' give exact info on version as have not used laptop for quite a while)

OK this is what happens...
I press the power on button on my Compaq Presario CQ57 Laptop and wait, it goes from a purple screen into a greyish screen. For a split second  i see it asking for my password then its gone. I can see the cursor and can move it round the screen but that's all that happens.

Incase it was just doing something i left it for an hour, when i came back it was still just the same. Can anyone help in very simple terms as to how i fix this please.

Regards
Keith

---

### Post by yancek on 2021-03-18
Was Ubuntu functional the last time you booted it, prior to this problem?
Were any changes made and if so, what?  
Do you have Ubuntu 'live' on a USB/DVD drive?  If you do, try booting it and if you can connect to the internet, go to the site below and download and run boot repair.  Use the 2nd option described on the page and select the Create Bootinfo Summary option and post the link you get when it finishes.  This will give enough information so someone should be able to help.

Do you have another OS on this machine and does it boot?  This might help to eliminate hardware problems.

---

### Post by panasonic57 on 2021-03-18
Hi,

Yes the laptop was working fine the last time i used it which was about 4 months ago.
i have made no changes to it other than let it do updates as per normal.

I don't have a ubuntu live USB/DVD drive

There is only Ubuntu 18. ???? on this laptop

All i have at the moment is a grey screen and a white cursor that i can move round the screen.

Every now and then there is some white text that shows "recovering Journal ?????, only shows for a few seconds, then gone for a few minutes then shows again.

---

### Post by CelticWarrior on 2021-03-18
You will need a USB live media to troubleshoot.

---

### Post by panasonic57 on 2021-03-18
how do i require a USB live media ?

---

### Post by CelticWarrior on 2021-03-18
You can make one with any 4GB USB stick in any computer, regardless of the OS.
[https://ubuntu.com/#download](https://ubuntu.com/#download) has tutorials. Scroll down to "Create a bootable USB stick on Ubuntu, macOS or Windows".

---

### Post by panasonic57 on 2021-03-18
ok many thanks, i will try that.

---

### Post by grahammechanical on 2021-03-18
If Ubuntu is the only OS on that machine you will not see a Grub boot menu. It is there but it does not show on the screen. You can try to bring the Grub boot menu on the screen by press and hold Shift as the motherboard runs its Power On Self Test (POST). That is if your motherboard has a BIOS settings utility. If the motherboard has a UEFI settings utility then press and hold ESC.

When the Grub boot menu appears select Advanced Options for Ubuntu and then select a Linux kernel with recovery mode. At the recovery menu select Resume. That should load to the login screen using an open source video driver. It will be low resolution. If this gets you to a working desktop then you may have a video driver problem. Open Software & Updates>Additional Drivers tab. Then either activate or de-activate the proprietary video driver as the case may be. You need to be connected to the internet at this time.

Regards

---

### Post by panasonic57 on 2021-03-18
Ok i have tried what you suggested above, all i can see is a grey screen with my mouse cursor

---

### Post by panasonic57 on 2021-03-18
it keeps showing "Recovering Journal every minute or so, nothing else ?????

---

### Post by ActionParsnip on 2021-03-18
Does using Ubuntu 20.04 help?

---

### Post by CelticWarrior on 2021-03-18
> **panasonic57 said:**
> Ok i have tried what you suggested above, all i can see is a grey screen with my mouse cursor
The suggestion was to to boot in recovery mode.
For such you need to use either SHIFT (BIOS) or ESC (UEFI) to show the Grub menu. It must be powering on and immediately press and hold the respective key.

And yes, this is a valid and excellent suggestion that may eventually avoid booting external media to troubleshoot as I mentioned before this suggestion came up. You should try this first.

---

### Post by panasonic57 on 2021-03-18
it is using 20.04, I can get into the Grub menu, i did what was explained but still only see a grey screen after re-booting.
I am at a loss as to try next, i have been at this for hours today and yet still i can't solve it. It's bound to be a simple fix, but i don't have the technical savvy to fix it.

---

### Post by panasonic57 on 2021-03-18
> **CelticWarrior said:**
> The suggestion was to to boot in recovery mode.
For such you need to use either SHIFT (BIOS) or ESC (UEFI) to show the Grub menu. It must be powering on and immediately press and hold the respective key.

And yes, this is a valid and excellent suggestion that may eventually avoid booting external media to troubleshoot as I mentioned before this suggestion came up. You should try this first.

I did as your instructions yet still not getting any results, getting to the point where i think it may be time to toss this laptop in the bin and purchase a new one.

---

### Post by Impavidus on 2021-03-18
> **panasonic57 said:**
> I did as your instructions yet still not getting any results, getting to the point where i think it may be time to toss this laptop in the bin and purchase a new one.

Before you do that, you may consider a fresh install of 20.04. As you don't use this computer frequently, it doesn't look like there's a lot of stuff on that you might lose.

Anyway, the "recovering journal" may suggest a hard drive problem. Hard drives shouldn't really suffer bitrot if you leave them unpowered for a few months, but you never know. It may be broken. On the other hand, this may simply be the result of pressing the power button without proper shutdown.

---

### Post by panasonic57 on 2021-03-18
Without sounding stupid, how do i do a fresh install of 20.04 if i can't see anything on screen except a grey background and the cursor.
Could you give me step by step instructions as to what i need to do please.
Thank you

---

### Post by CelticWarrior on 2021-03-18
> **panasonic57 said:**
> Without sounding stupid, how do i do a fresh install of 20.04 if i can't see anything on screen except a grey background and the cursor.
Could you give me step by step instructions as to what i need to do please.
Thank you

That's what the Ubuntu live USB is for. As mentioned above it can be also used to run a live session and troubleshoot in cases when the OS doesn't boot or doesn't run properly but its main usage is, obviously to install the OS.
Either usage implies booting the media. The boot order is changed in the firmware settings, BIOS or UEFI, or preferably in the one-time boot menu, if available. This exact step vary depending on the brand/model. Once in a live session and running the installer (or running the installer directly) it's pretty much the same for all.

---

### Post by panasonic57 on 2021-03-18
Ok obviously i am on a windows Desktop replying to you, so just so i understand correctly, you are saying create a live bootable usb on my windows pc, then use that to boot into my laptop ? then i should be able to access what i need from there.

---

### Post by CelticWarrior on 2021-03-18
Yes, once you're in a live session you should be able to access the files in the internal drive and backup if it isn't encrypted, of course. And once you run the installer it should be self-explanatory. Just select the option to "erase and install.." and it'll do everything automatically for you. Also recommended (but optional) to have an active internet connection to download updates during installation and strongly recommended to select the option to install third-party drivers, firmware, etc. Other than that all should be smooth and automatic.

However...
As mentioned above the internal drive can be defective.

---

### Post by panasonic57 on 2021-03-19
Thank You to everyone who helped, The live session did the trick and enabled me to install a fresh install of Ubuntu.
Am now up and running again.

---

