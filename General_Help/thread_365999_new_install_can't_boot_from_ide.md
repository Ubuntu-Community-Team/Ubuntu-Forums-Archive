---
title: "new install can't boot from ide?"
date: 2007-02-20
forum: General Help
---

### Post by TheShadow99 on 2007-02-20
Hello,

I'm a network admin for a school and we are looking at starting to run some Linux boxen and since ubuntu is probably the most popular form of linux these days I decided to test it on a couple boxes and see what the result is like.

Well the LiveCD works fine and I move on to doing an install. For test purposes I left windows installed on the primary HDD (ide0), and installed a second HDD (ide1). I installed Ubuntu to ide1 and noted in the confirmation that grub was going to be installed to ide0. That all seemed fine until I restarted the system and then the bios reported 'no operating system'. The thing that makes less sense is that I can boot from the LiveCD and select 'boot from first disk' and things work just fine (can even access Windows XP Pro still).

Any suggestions on what is going on with this box? I've used linux before, but that was Mandrake and Red Hat on my personal machine a few years ago. Since then I've only really run Linux via LiveCD's of various types and so I have no idea where to start to fix the issue. For the moment simply running the LiveCD until it's booted is workable, but I can't do that for every system in the lab so this is holding off any further adoption of Linux in the building.

Thank you for any help.

---

### Post by logos34 on 2007-02-20
Maybe your BIOS hard disk boot priority is set to boot the ubuntu drive (primary slave) first, but Grub is on the primary master...Or maybe the mbr got borked...If it's set to boot hda, then try reinstalling grub to the mbr of hda (hd0).  Follow these steps:

> 
    * type sudo grub
    * When at the grub prompt, type find /boot/grub/stage2
    * This will return something like (hd0,2)
    * To setup the boot partition boot type root (hd0,2). This is the harddrive and the partition your linux is installed on...
    * And then to configure grub type setup (hd0)
    * Now you're done, so exit with quit  
[http://easylinux.info/wiki/Ubuntu:Edgy](http://easylinux.info/wiki/Ubuntu:Edgy)

You can also try SuperGrub if that doesn't work.

---

### Post by TheShadow99 on 2007-02-21
Thank you a version of that seems to have fixed the issue...

Didn't have sudo last time I was using linux from an HDD... So it's been a good while... ^_^

---

