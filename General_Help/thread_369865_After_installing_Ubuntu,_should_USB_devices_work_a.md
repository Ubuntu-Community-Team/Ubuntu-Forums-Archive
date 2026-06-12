---
title: "After installing Ubuntu, should USB devices work automatically?"
date: 2007-02-25
forum: General Help
---

### Post by wersdaluv on 2007-02-25
Until now, I cannot get my USB devices to work with Ubuntu/Kubuntu Edgy.

I want to know if there are some configurations or something like that that one has to do with Edgy for USB devices to work with it.

---

### Post by yabbadabbadont on 2007-02-25
Which devices?  What error messages (if any)?  What happens when they are plugged in?

---

### Post by wersdaluv on 2007-02-25
> **yabbadabbadont said:**
> Which devices?  What error messages (if any)?  What happens when they are plugged in?


I have posted every information that I think are relevant to my problem in [this thread]("http://ubuntuforums.org/showthread.php?t=356269").

One question.. should USB devices automatically work with Ubuntu?

---

### Post by Soulxlight on 2007-02-25
Well...my usb mp3 player is auto mounted, and works perfectly. No problem at all.

---

### Post by chewearn on 2007-02-25
Yes, many usb devices should work automatically.  I have usb mouses and keyboards working in a few PCs without problem.  Also, many different usb flash drives and harddisks (mass storage class).

One question though, do your problem occurred on all usb ports of your PC, or just one?

I'm not an expert here, but looking at your dmesg output, I see some ACPI errors immediately after usb hub detected.  Maybe you could try changing ACPI (disabling it, or change any available setting)  in your BIOS.

---

### Post by wersdaluv on 2007-02-25
> **AstalaVista said:**
> Yes, many usb devices should work automatically.  I have usb mouses and keyboards working in a few PCs without problem.  Also, many different usb flash drives and harddisks (mass storage class).

One question though, do your problem occurred on all usb ports of your PC, or just one?

I'm not an expert here, but looking at your dmesg output, I see some ACPI errors immediately after usb hub detected.  Maybe you could try changing ACPI (disabling it, or change any available setting)  in your BIOS.

Okay. I'll try to do that. 

But first... I'll figure out what ACPI and BIOS are. I'm a beginner.

Thanks for the advice!

I'm so desperate with this.

---

### Post by wersdaluv on 2007-02-25
I forgot to answer the question...

Every USB slot do not work

---

### Post by chewearn on 2007-02-25
As you boot up the computer, at the boot screen (a bunch of text messages; or for recent PC, a logo of the manufacturer), press <DEL> or <F2> a few times; you should enter a text menu will many options.  This is your BIOS setup screen.

Don't play around with the settings if you don't know what you are doing; but the ACPI should be under "Power Management" or similar.  It should be quite safe to turn it off.  But if things got worse, just reboot and change it back.

---

### Post by wersdaluv on 2007-02-25
Do you think it will really solve the problem considering that in my windows partition in this laptop, USB devices work well?

---

### Post by chewearn on 2007-02-25
Well, it might take a bug fix to solve via bug report, so it's up to you ;)

---

