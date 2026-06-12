---
title: "Botched Grub edits, error 'cannot read linux header' and no boot"
date: 2013-05-07
forum: General Help
---

### Post by merclurker on 2013-05-07
Thanks for your help- 

Background- Using ubuntu 11.10, not the first version I've used on this machine- on boot would not load current kernel 3.0.0-32-generic, but would boot after selecting 3.0.0-12-generic and ran great. Downloaded Startup-Manager thinking it would clean all that up and I could get it to automatically boot on 3.0.0-12-generic. After setting that as the default version in Startup-Manager and rebooting, i get the following-


GNU GRUB version 1.99-12ubuntu5.1 

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

Also, I worked through the following, but as soon as i got to grub> linux /vmlinuz ro root=/dev/sda1  it hung and said 'error: cannot read linux header' 


-[http://tuxers.com/main/instigating-a-manual-boot-from-the-grub-prompt/](http://tuxers.com/main/instigating-a-manual-boot-from-the-grub-prompt/)

I'm pretty new to Ubuntu, and pretty lost from here. Thanks again

---

### Post by oldfred on 2013-05-07
You can install into your current liveCD or download a repairCD to use.

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by merclurker on 2013-05-08
Cool- I'll burn a disk and see if the optical still works. Thanks for the help!

---

### Post by merclurker on 2013-05-08
Fantastic! 

I made a Boot-Repair livedisk, asked BIOS to boot from CD, selected the recomended option after the os started up and it was a done deal! I no longer get the GRUB> prompt, but instead the GRUB menu with previous versions of Ubuntu to boot. Now to back everything up before I change anything else. Thanks again Oldfred.

if you were wondering, the boot-repair log is at [http://paste.ubuntu.com/5645868](http://paste.ubuntu.com/5645868)

---

