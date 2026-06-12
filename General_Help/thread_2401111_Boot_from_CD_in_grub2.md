---
title: "Boot from CD in grub2"
date: 2018-09-13
forum: General Help
---

### Post by kaleidos2 on 2018-09-13
Hi everyone, 
I have a dual boot configuration, with grub2 prompting the boot list when I switch on the PC.
The systems installed are Ubuntu 16.04 and windows 10.  
My PC went off while windows was installing the automatic updates. 
When I restarted, I logged-in Ubuntu and upgraded it from 14.04 to 16.04 (this was planned since weeks..). 
Now booting windows does not work any longer and the system freezes with the windows logo on the screen. 
I need to recover windows from a bootable windows cd, which I have. 
However when setting in the BIOS to boot the DVD drive first, this command is ignored and grub2 keeps appearing.

I did the following:

```
gksu gedit /etc/grub.d/40_custom
```

and added these lines to the file: 

```
menuentry "CD on (cdrom/dvd)" {
    set root=(cd0)
    insmod part_gpt
    insmod chain
    chainloader /boot/efi/EFI/ubuntu/grubx64.efi    
}

```

and finally

```
sudo update-grub
```

After that, grub2 correctly shows the option "CD on (cdrom/dvd)".
However when I select it, I get an error message showing that /boot/efi/EFI/ubuntu/grubx64.efi cannot be found (although the path is existing). 

Any idea on how to solve this is greatly appreciated!
Thanks!

---

### Post by oldfred on 2018-09-14
You do not normally boot CD/DVD from grub. You boot from BIOS/UEFI directly.
If it does not boot, then there may be a configuration issue on CD/DVD. And Windows does not use grub to boot.

I have this in my notes from years ago. I only use flash drives now as I have so many coasters (bad burns).
      ```
 #BIOS Boot whatever is in the CD drive
menuentry "CD on (cd0)" {

 insmod udf
set root=(cd0)
chainloader +1 
 }     
```

Is Windows 10 really UEFI, then boot would be different. 
How you boot install media is how it installs or will repair, so you must then boot in UEFI boot mode. And then you need to directly boot from UEFI boot menu in UEFI mode. If not shown, then Windows DVD is not correct.

---

### Post by kaleidos2 on 2018-09-14
Thanks for your answer, I actually could solve it from the BIOS.
I noticed that in the BIOS boot menu there was an option called "Boot menu" that was disabled. 
I had to enable it and place it as first option. When restarting, the default boot menu allowed me to boot from DVD. 
Cheers.

---

