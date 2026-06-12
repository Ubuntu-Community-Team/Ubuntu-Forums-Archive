---
title: "Toshiba Satellite L70A, UEFI"
date: 2014-02-27
forum: General Help
---

### Post by g.wiebe84 on 2014-02-27
I seem to have a similar problem. I'm attempting to install Ubuntu 13.10 from a usb on a Toshiba Satellite L70A. It's brand new and has Windows 8 (awful excuse for an OS). 

After selecting the usb boot priority from the bios, the ubuntu install menu pops up and gives me the options to try or install. Everything looks good at this point. When choosing any choice whether try or install, the next screen is so dark that I can barely make anything out. 

I have no idea what to do. Why would it go almost completely black?

---

### Post by mörgæs on 2014-03-02
Your post is about different hardware, so it has been moved to a new thread. 

Please begin with posting a complete hardware description.

---

### Post by amjjawad on 2014-03-02
Hi,

> **g.wiebe84 said:**
> I seem to have a similar problem. I'm attempting to install Ubuntu 13.10 from a usb on a Toshiba Satellite L70A. It's brand new and has Windows 8 (awful excuse for an OS). 

Have a read at:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


> After selecting the usb boot priority from the bios, the ubuntu install menu pops up and gives me the options to try or install. Everything looks good at this point. When choosing any choice whether try or install, the next screen is so dark that I can barely make anything out. 

I have no idea what to do. Why would it go almost completely black?

Have you checked MD5SUM before creating the Live USB?

What approach have you used to create the Live USB?

On the first screen, there is an option called "Check disc for errors/defects" before anything else. It saves a lot from your time!

Thank you!

---

### Post by g.wiebe84 on 2014-03-03
> **amjjawad said:**
> Hi,

Have a read at:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you checked MD5SUM before creating the Live USB?

What approach have you used to create the Live USB?

On the first screen, there is an option called "Check disc for errors/defects" before anything else. It saves a lot from your time!

Thank you!

The checksum checked out. I used the Ubuntu 13.10 Startup Disk Creator on my home laptop. I did check the disc for errors/defects. Having read the above link regarding UEFI, (which I do not claim to understand at all) I did disable the Secure Boot from the bios. I could not find anything like FastBoot.

If I tilt the screen at an oblique angle I can vaguely see what's on the screen. I managed to get to screen where you're to choose the formatting options. However, right at the top of the box it says that, "This computer currently has no detected operating system what would you like to do."

So, from my perspective, there seem to be two upfront issues: 

1. Windows 8 is not recognized. This being a work computer, I cannot install over windows 8.

2. Upon making a choice from the live usb, either Try Ubuntu or Install Ubuntu, the screen is almost completely black.

I'm at a loss. Any help is appreciated.

---

### Post by g.wiebe84 on 2014-03-06
Bump....... bumpity...... bump bump

---

### Post by oldfred on 2014-03-08
Is this an Ultrabook? That uses Intel SRT which has RAID. You can turn that off and change drive to AHCI.

Also have you turned off the always on hibernation or fast boot. Best to re-review the link as posted above.

Several more good links in link in my signature. Every detail is important, but depends on how system is configured, so it can be a bit difficult.

---

