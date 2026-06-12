---
title: "I/O Error While Trying To Install Ubuntu 24.04."
date: 2024-04-25
forum: General Help
---

### Post by daniell59 on 2024-04-25
I installed the iso using Rufus. When booting off of the flash drive, an I/O error was displayed on the screen. After a short time, the error went away and I could have gone further. I don't want to install Ubuntu 24.04  until I can resolve this error. Any insight would be appreciated.

---

### Post by #&amp;thj^% on 2024-04-25
A good  insight would need some more info...otherwise we would all be guessing.
Like this, possible bad flash drive.

---

### Post by daniell59 on 2024-04-25
> **1fallen said:**
> A good  insight would need some more info...otherwise we would all be guessing.
Like this, possible bad flash drive.

Thanks, I'll try a different flash drive.

---

### Post by #&amp;thj^% on 2024-04-25
let us know please how that goes.
Other things related corrupt .iso, bad burn tool on and on.
I'm not familiar with Rufus so I can't comment on that tool, but [Etcher]("https://appimage.github.io/Etcher/") and [mkusb]("https://help.ubuntu.com/community/mkusb") has always worked for me

---

### Post by Rubi1200 on 2024-04-25
Errors often appear during the boot process, whether from a live media or a regular install. For the most part, they are just warnings and can be ignored.

What makes you think this is more serious?

Did you go to the stage of Try Ubuntu to see if everything works?

---

### Post by daniell59 on 2024-04-26
> **Rubi1200 said:**
> Errors often appear during the boot process, whether from a live media or a regular install. For the most part, they are just warnings and can be ignored.

What makes you think this is more serious?

Did you go to the stage of Try Ubuntu to see if everything works?

It was quite a long error message. After I let it run, it went a way and I was able to run Ubuntu 24.04 off of the flash drive. There did not appear to be any problems. I still don't have a clue of what the message means.

---

### Post by Rubi1200 on 2024-04-26
> **daniell59 said:**
> I still don't have a clue of what the message means.

Neither do we.

If you are somehow able to take a photo of at least the start of the error message with your phone and upload the picture...it might tell us something.

But then again, you were able to get to the desktop and try Ubuntu so my gut feeling says there is nothing to be concerned about.

---

### Post by daniell59 on 2024-04-26
After several attempts with my phone, this is the best that I can get.

---

### Post by Rubi1200 on 2024-04-26
I don't recognize that particular error but as I said booting often has errors that are really not that consequential. They only become problematic if you cannot reach the desktop or boot at all.

Next step is up to you whether you want to do a full install or wait a few months.

---

### Post by daniell59 on 2024-04-26
> **Rubi1200 said:**
> I don't recognize that particular error but as I said booting often has errors that are really not that consequential. They only become problematic if you cannot reach the desktop or boot at all.

Next step is up to you whether you want to do a full install or wait a few months.
Thanks for the input. What I would like to know is if the error is on my end.

---

### Post by oldfred on 2024-04-26
I thought fd0 was floppy drive?
Some may have floppy drive configured in UEFI/BIOS even when it does not exist. So error is that UEFI/BIOS said you have floppy, but installer cannot find it to know it is there.
Check UEFI/BIOS settings.

---

### Post by daniell59 on 2024-04-26
> **oldfred said:**
> I thought fd0 was floppy drive?
Some may have floppy drive configured in UEFI/BIOS even when it does not exist. So error is that UEFI/BIOS said you have floppy, but installer cannot find it to know it is there.
Check UEFI/BIOS settings.
The BIOS does list a Floppy drive. I have not been able to remove it. Good observation!

---

### Post by #&amp;thj^% on 2024-04-26
> **daniell59 said:**
> After several attempts with my phone, this is the best that I can get.

I've seen that error, just before Noble went Beta, How current is your Downloaded .iso?

I also think oldfred has a good suggestion in checking your settings in "Check UEFI/BIOS settings". 

However though if you can proceed from that error, i would have to believe that it would sort itself out with full updates after a successful install.

Can you try that?

---

### Post by #&amp;thj^% on 2024-04-26
> **daniell59 said:**
> The BIOS does list a Floppy drive. I have not been able to remove it. Good observation!

To move past that, can you push a key F1 to proceed?

---

### Post by daniell59 on 2024-04-26
The iso was downloaded April 25. I will try to  disable the floppy drive from the BIOS. For the time being, I will stick with Ubuntu 22.04.

---

