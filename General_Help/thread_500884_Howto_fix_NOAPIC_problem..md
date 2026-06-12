---
title: "Howto fix NOAPIC problem."
date: 2007-07-14
forum: General Help
---

### Post by masteryurez on 2007-07-14
I have a conclusion of the noapic problem. Just follow the steps and it should work just fine. 

1, Start you computer and boot from CD.
2, Press F6 to get the command-line
3, Write noapic after quiet splash like this: 
```
quite splash noapic --
```4, Your system should now boot like normally.
5, Install Ubuntu and reboot.
6, When Grub count down from 3, 2, 1, 0 press "Esc" to get into GRUB.
7, Mark the kernel you usually boot from and press "e" to edit option of your kernel.
8, Mark kernel and press "e" to edit.
9, You should now get a text that says this: ```
<b-7056-4774-aa87-d94cfb40011c ro quiet splash locale=sv_SE
```(note that I have swedish language so sv_SE is just for swedish language. If you have english language it says en_GB)
10, After the text locale=sv_SE do a space then write noapic like this: 
```
<b-7056-4774-aa87-d94cfb40011c ro quiet splash locale=sv_SE noapic
```and press enter.
11, Press "b" to boot and your system would now boot. (Note that this option is only for this time you start your computer so now I'm going to learn you how to do this for everytime you boot. 
12, After your new Ubuntu installation has started up. Start a terminal and write this:
```
sudo gedit /boot/grub/menu.lst
```13, Go down to the selection that says: ## ## End Default Options ##
14, You would now see some text like this: 
```
title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet
```15, After the text that says ro quite splash write noapic and do this for every kernel but don't after /boot/memtest86+.bin
16, Save the file and restart your computer. You should now start Ubuntu without any problem. 

(Just note that you must do this everytime you update your kernel.)

I hope this guide was helpful. 

Good luck Ubuntu users.

// Masteryurez

---

### Post by TheExplorer on 2007-07-15
Good manual. I've come across this problem a few months ago and fortunately googled out the 'noapic' solution. An interesting fact to point out that x64 distribution worked fine without any additional parameters and x86 didn't. I still believe it's an ubuntu bug really.

---

### Post by Bob63 on 2007-07-16
> **TheExplorer said:**
> Good manual. I've come across this problem a few months ago and fortunately googled out the 'noapic' solution. An interesting fact to point out that x64 distribution worked fine without any additional parameters and x86 didn't. I still believe it's an ubuntu bug really.

I tend to agree that it's a bug, either with Ubuntu or with the installer. I might be a noob to Ubuntu/Linux, but I have quite a bit of experience installing windows and its software. Something in the installer for the LiveCD doesn't seem to be detecting the hardware and/or bios settings very well (especially since the Alternate i86 CD seems to get it right).

---

### Post by masteryurez on 2007-07-16
> **TheExplorer said:**
> Good manual. I've come across this problem a few months ago and fortunately googled out the 'noapic' solution. An interesting fact to point out that x64 distribution worked fine without any additional parameters and x86 didn't. I still believe it's an ubuntu bug really.

I tried the 64bit version of Ubuntu Feisty 7.04 and I got the same result as with the standard x86 version. It seems that it doesn't matter what version you have of Ubuntu..
I have tried both x86 and 64bit with the same guide.. works for both of them..

---

### Post by bennettg on 2007-12-20
thanks

> **masteryurez said:**
> I have a conclusion of the noapic problem. Just follow the steps and it should work just fine. 

1, Start you computer and boot from CD.
2, Press F6 to get the command-line
3, Write noapic after quiet splash like this: 
```
quite splash noapic --
```4, Your system should now boot like normally.
5, Install Ubuntu and reboot.
6, When Grub count down from 3, 2, 1, 0 press "Esc" to get into GRUB.
7, Mark the kernel you usually boot from and press "e" to edit option of your kernel.
8, Mark kernel and press "e" to edit.
9, You should now get a text that says this: ```
<b-7056-4774-aa87-d94cfb40011c ro quiet splash locale=sv_SE
```(note that I have swedish language so sv_SE is just for swedish language. If you have english language it says en_GB)
10, After the text locale=sv_SE do a space then write noapic like this: 
```
<b-7056-4774-aa87-d94cfb40011c ro quiet splash locale=sv_SE noapic
```and press enter.
11, Press "b" to boot and your system would now boot. (Note that this option is only for this time you start your computer so now I'm going to learn you how to do this for everytime you boot. 
12, After your new Ubuntu installation has started up. Start a terminal and write this:
```
sudo gedit /boot/grub/menu.lst
```13, Go down to the selection that says: ## ## End Default Options ##
14, You would now see some text like this: 
```
title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet
```15, After the text that says ro quite splash write noapic and do this for every kernel but don't after /boot/memtest86+.bin
16, Save the file and restart your computer. You should now start Ubuntu without any problem. 

(Just note that you must do this everytime you update your kernel.)

I hope this guide was helpful. 

Good luck Ubuntu users.

// Masteryurez

---

