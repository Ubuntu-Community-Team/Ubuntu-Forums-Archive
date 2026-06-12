---
title: "ACPI and reboot issues"
date: 2007-06-12
forum: General Help
---

### Post by egilfoy on 2007-06-12
So, I decided to revive an old laptop with some motherboard problems. It's a hodgepodge old Vaio that has had parts changed and added over the years. Due to an issue with the board, it reports false CPU overheat errors almost constantly, which leads to some issues with ACPI and makes running windows impossible

Luckily, i had an old version of hoary installed on the machine and using that I was able to fix the reboot errors with no cpu overheating issues with "acpi=off noapic"

But I decided to get with the times and upgrade to Feisty(using alternative cd). Now, no matter what I do, I cant seem to disable ACPI during boot up. I've read through a ton of old posts and cant seem to find a solution that fits.

ACPI has been disabled through the bios and will stay powered on for prolonged periods during grub editing, so I know the machine is still functioning. The moment  ubuntu starts booting up, it's countdown to random shutoff.

I'm pretty desperate for some help on how to fix this problem (a well placed hammer is starting to look like a good fix :d). Please note that I can only change boot options through grub editing, since the machine doesnt stay powered long enough to actually enter ubuntu. Any suggestions would be very, very appreciated.

---

### Post by DagMan on 2007-06-13
I do not know if this could be part of the problem and what the consequences of it would be, but perhaps if you booted into a live cd that your computer can handle such as DSL then moved or changed permissions to non-exectutable on /etc/init.d/acpid and /etc/init.d/acpi-support it would make a differance.  Perhaps also /etc/init.d/apmd
I don't know if any of those would help or just be harmful or do nothing at all.

The other thing that might work would be a kernel recompile disabling support for thermal zone in the power management part and whatever other options might be related, acpi or just normal options, to the kernel reporting an overheated cpu to the bios.

It sort of sounds though like maybe it's a coincidence and that maybe the processor is getting hot.

Hey I just rethought that maybe DSL won't let you boot either but I guess it would be worth a try.  If you have an old Warty live cd maybe...

---

### Post by egilfoy on 2007-06-18
Thanks for the reply. I tried the Live CD of fiesty and edgy. Fiesty wouldnt load at all live style (probably due to the sysem, not the cd) and while edgy would load through  live cd, with acpi disabled it was still shutting down. I finally pulled out an old hoary cd and just reloaded that. It's running without problems now, but I'm still hoping to update. I've been monitoring temps and it's definitely running cool (it's frankenstein'd at the moment and completely out of the plastic casing until the final pieces come in to finish off my project).  I've had no problems with the system during stress tests, so I'm pretty confident that it's not actually overheating. If your curious, my ultimate goal is to move the stripped down system(no cd drive, battery, modem, etc.) into a shadow box with a touchscreen to sit in our kitchen, since I'm tired of crumbs and near-miss spills around my proper laptop. 

I've got another viao, that's virtually the same machine starting to develop the same problems. I'm going to try your suggestions out on that machine and see if anything sticks. I should be able to get edgy up with live and try out the permissions and kernel suggestions. I'll let you know how it goes.

---

