---
title: "Trouble booting into Ubuntu"
date: 2023-12-24
forum: General Help
---

### Post by dorasmith24 on 2023-12-24
I am using Ubutntu 20.00.   I also had Windows 10 installed on its own hard drive.   If I didn't push F10 on my keyboard fast enough it automatically booted into Windows 10.

Then it stopped getting past the boot screen.   In troubleshooting it wouldn't boot until I unplugged my webcam, my headphones, and my fairly new dvd player specifically supposed to work with Linux - all USB, then it booted into Windows 10.

I took the Windows 10 drive out of my computer, and it booted to the Ubuntu choose how you want to boot into Ubuntu screen.   Then I plugged in my peripherals.

The next time I booted up my computer, it booted to the boot screen, until I unplugged the peripherals, then it booted to the screen that lets you select how you want to boot into Ubuntu.

It occurs to me that if the system tried to boot from the dvd player I would likely see what I'm seeing - next time I boot my machine I will check my boot options as if that is the problem it will be simple to correct.   

Other than that, should I run boot-repair to restore GRUB that Windows 10 did away with?

I ran Boot-Repair, and the default repair would reinstall the grub2 of sda5 into the MBR of sda.   And also unhide-bootmenu-10s.

Should I do this - and is it likely to solve my problem, or is something the matter with one of my peripherals?   I'm perfectly fine with booting from the menu that lets me choose how to boot into Ubuntu, as long as I can get that far.

---

### Post by MAFoElffen on 2023-12-25
Maybe when you boot into Ubuntu. like you have... During that, force the menu to show, and add a "longer wait" into the /etc/default/grub file until you get that worked out...

---

### Post by yancek on 2023-12-25
Why don't you do what boot repair suggests on their web site, post the link to the output from boot repair when you select the Create BootInfo Summary option.  That way, members here who are more familiar with boot problems will be able to view it and make suggestions.

---

### Post by dorasmith24 on 2023-12-25
Thanks!   I've actually got an idea that fixing my boot order in BIOS will fix the problem, especially as it did the same thing when it was booting into Windows, but if that doesn't work, I will try these things.   

Fixing the boot order in BIOS is a matter of unplugging the DVD player so it doesn't HANG at the boot screen, then going into bIOS and changing the boot order.   If it is set to boot from the cd/ dvd drive and can't, that will cause problems trying to boot.  Since I've not used a cd/ dvd drive wtih this computer in a long time I might not be aware of that setting.

---

