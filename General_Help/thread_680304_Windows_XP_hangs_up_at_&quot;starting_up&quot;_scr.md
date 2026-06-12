---
title: "Windows XP hangs up at &quot;starting up&quot; screen"
date: 2008-01-27
forum: General Help
---

### Post by cantri on 2008-01-27
I just installed ubuntu 7.10. I am able to boot into ubuntu but not windows xp. However the first time I tried I did get into xp windows ran through a scan of some sort. However now It loads the boot menu and when I pick XP it just hangs at the "starting up" screen. I am very new to this and don't know what to do. here is my grub menu.lst file, aslo there is a similar file menu.lst~ ( should this be here)

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=71c1dfc1-2763-4b27-acf0-2750745b31fe ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=71c1dfc1-2763-4b27-acf0-2750745b31fe ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by kerry_s on 2008-01-27
i hope you defragged xp before you resized it. try getting into safemode, when it's starting up start tapping the F8 key. then just set it to error check at startup and reboot.

---

### Post by cantri on 2008-01-27
I did defragment windows. I ran super grub to try to get back into windows but this did not work. Now super grub has taken over my boot and I have to have the cd in or I get a an error message and am forced to restart. Should I reinstall ubuntu? Will this put back the original boot loader? I can access all my old windows files still, is there anyway to run those programs, I suppose I don't really need windows if I can do that. And I tried f8 but super grub instantly takes over. any ideas, help is much appreciated

---

### Post by kerry_s on 2008-01-28
> **cantri said:**
> I did defragment windows. I ran super grub to try to get back into windows but this did not work. Now super grub has taken over my boot and I have to have the cd in or I get a an error message and am forced to restart. Should I reinstall ubuntu? Will this put back the original boot loader? I can access all my old windows files still, is there anyway to run those programs, I suppose I don't really need windows if I can do that. And I tried f8 but super grub instantly takes over. any ideas, help is much appreciated


yeah, that would probably be the easiest way to get the loader back, there is a repair function with the live cd but i've never used it so i wouldn't even know how to talk you through it.

---

### Post by tubunu on 2008-01-28
Try reinstalling grub first. Search these forums. Or try this:
> 
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

