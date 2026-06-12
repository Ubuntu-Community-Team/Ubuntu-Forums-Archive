---
title: "Grub menu disappears to black screen after ~2 seconds"
date: 2020-04-15
forum: General Help
---

### Post by ogola89 on 2020-04-15
Hi all,

I have a HP laptop with windows 10 installed on a 225gb SSD, but have an external 4TB hard drive with Ubuntu 19.10 installed. My current boot settings are UEFI and to boot to the Ubuntu HD first which then shows the grub menu to allow me to choose which path I would like to go down.

It was working fine, but about a month and a half ago, I had issues with everything, had to reinstall Windows and I migrated by Ubuntu installation (at that time it was on a USB) to my hard drive, and everything started working fine. However, the grub menu stopped coming up and it would only boot to windows or to Ubuntu depending on the boot order i selected in the BIOS.

After a few boot-repairs, it started working fine. However, now about 8/10 times the menu will appear for about 2 seconds before disappearing into black, leaving me stuck without any options and having to do a hard power down and restart, and then only 2/10 times will the menu be stable. So alot of times I have to hit the enter button to boot to Ubuntu very quickly, or use the BIOS to boot to windows. The settings in my grub config file are fine, and I even used grub customizer.

A video of what I am talking about can be seen in this link:
[https://1drv.ms/v/s!Apy05OOWRAfQjYZs4rkHOpuBcT5BFA?e=T82Ivw](https://1drv.ms/v/s!Apy05OOWRAfQjYZs4rkHOpuBcT5BFA?e=T82Ivw)

Sometimes it will throw the following error before as shown in the image:

```
Failed to open \EFI\BOOT\grubx64.efi - Not Found  
Failed to load image \EFI\BOOT\grubx64.efi: Not Found    
start_image() returned Not Found  
```



But not always, as the video above did not show this.

Please let me know what I can do to resolve this.

Thanks!

EDIT: Boot info summary
[https://gist.github.com/ogola89/f046aa04cc1d43daa218dcf5ad01e9b3/raw/3a6de7d2b31dfafa406740bf0f79bda7edc72861/Boot-info-summary](https://gist.github.com/ogola89/f046aa04cc1d43daa218dcf5ad01e9b3/raw/3a6de7d2b31dfafa406740bf0f79bda7edc72861/Boot-info-summary)

---

### Post by Impavidus on 2020-04-15
You already found boot-repair. Can you use it to create a boot info summary and show us the link?

---

### Post by yancek on 2020-04-15
Posting a link of the output of boot repair after running it with the Create BootInfo Summary option would be best to provide information.  The error is very specific so you might try mounting your EFI partition (wherever that might be?) and taking a look at it to see if there is indeed a grubx64.efi file at that location.  The standard location for that file would be under the /EFI/ubuntu/ directory so I don't know why it is looking for it in the location you posted..  /EFI/BOOt would contain windows files.

---

### Post by ogola89 on 2020-04-16
Hi guys, thanks for the responses.

I created the bootinfo summary and it is attached to the main post as an edit and link.

I think I mentioned though, that message does not appear all the time, maybe 50% of the time.

The main issue is having grub disappear after 2 seconds which leaves me with no boot options and a power off is required. If I am fast enough I can hit enter before the screen goes black and it will boot to Ubuntu as normal

---

### Post by dragonfly41 on 2020-04-16
[COLOR=#000000]> I created the bootinfo summary and it is attached to the main post as an edit and link.

The contributors here are suggesting that you postthe boot-repair pastebin url not a screenshot in your video.

Meanwhile you might try this.  Immediately the boot menu appears (it seems to timeout after a second) hit the down arrow to select Ubuntu advanced options then hit Enter and possibly you might find some further options to try.[/COLOR]

---

### Post by CelticWarrior on 2020-04-16
@dragonfly41 - The OP added the link to the summary info: [https://gist.githubusercontent.com/ogola89/f046aa04cc1d43daa218dcf5ad01e9b3/raw/3a6de7d2b31dfafa406740bf0f79bda7edc72861/Boot-info-summary](https://gist.githubusercontent.com/ogola89/f046aa04cc1d43daa218dcf5ad01e9b3/raw/3a6de7d2b31dfafa406740bf0f79bda7edc72861/Boot-info-summary)

Not surprisingly, when the OP reinstalled Windows they did it in Legacy mode. That's why the dual-boot doesn't work.

---

### Post by ogola89 on 2020-04-16
> **CelticWarrior said:**
> @dragonfly41 - The OP added the link to the summary info: [https://gist.githubusercontent.com/ogola89/f046aa04cc1d43daa218dcf5ad01e9b3/raw/3a6de7d2b31dfafa406740bf0f79bda7edc72861/Boot-info-summary](https://gist.githubusercontent.com/ogola89/f046aa04cc1d43daa218dcf5ad01e9b3/raw/3a6de7d2b31dfafa406740bf0f79bda7edc72861/Boot-info-summary)  Not surprisingly, when the OP reinstalled Windows they did it in Legacy mode. That's why the dual-boot doesn't work.  That's very surprising, as I formated my windows disk to GPT before reinstalling and made sure I installed UEFI. Furthermore I turned off legacy in the BIOS.   It's surprising as I don't know how it could have been installed that way. When I installed ubuntu originally in 18.04, I think it was on legacy as I could dual boot to Windows fine. However, since upgrading to 19.04, I was unable to dual boot - windows would give me an error and I would never even be able to see the grub menu. Hence why I formatted windows and reinstalled everything in uefi, turned off legacy in BIOS and even the grub menu shows Uefi windows boot manager, and the BIOS boot options shows windows as UEFI. I am very confused about that   The problem is not being unable to boot to either OS, I can do that, but the problem is the grub menu disappearing shortly and not giving me enough time and letting me choose what to boot to before blacking out. It doesn't always do this and sometimes it's fine.   I am also unable to prolong the time by moving the arrows

---

### Post by dragonfly41 on 2020-04-16
I am guessing here .. but perhaps Grub Customizer package might shed some light on timeout?

---

### Post by ogola89 on 2020-04-16
> **dragonfly41 said:**
> I am guessing here .. but perhaps Grub Customizer package might shed some light on timeout?  Grub customizer, as well as grub config is set to timeout at 10 seconds.  Besides, shouldn't the timeout lead to automatically boot to whatever is the default entry, rather than just throw a black screen?  Besides, the moving of arrows should stop the timer (which it doesn't).  I'm so perplexed.  I checked the bootinfo summary and can't actually see where it's pointing to my windows installation as legacy, maybe someone could help me point it out by showing the text?

---

