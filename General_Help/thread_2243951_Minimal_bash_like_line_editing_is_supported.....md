---
title: "Minimal bash like line editing is supported...."
date: 2014-09-12
forum: General Help
---

### Post by johnnie1 on 2014-09-12
Hi,
a few weeks ago I tried to update ubuntu from 13.10 to 14.04.. There was an error somewhere in the updating process and when I rebooted I received a message "error: symbol 'grub_term_highlight_color' not found", seemingly the same problem as described here - [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
i made a bootable flash drive and retrieved all of my files. The I tried to follow some of the instructions (including the "boot repair tool, which didn't work although I can't remember why) in the link above to fix it. Obviously I made a hash of it as now when I try to boot without the flash drive I get a message "minimal bash like line is supported... ...
grub>
"
and when I try to boot from usb it just hangs on a blank screen with a flashing underscore.
can anyone help? I've been using ubuntu for a while but I'm not familiar with any of the commands etc.
my laptop is Lenovo with windows 7 64bit and ubuntu.
i don't know what other information could be helpful
thanks

---

### Post by yancek on 2014-09-12
Getting output from the bootinfoscript or boot repair script would give us information on your drives/partition. Boot files, etc. which should provide enough information for someone to make suggestions.  Otheriwise, it just guessing.  The bootinfoscript can be downloaded from the site below, instructions on the page.  Post the output which is a resultsx.txt file.

Just read over your post.  Apparently you can't boot the flash drive either.  The bootinfoscript needs to be run from Linux, do you have any other Linux CD/flash drive you could use?
I don't use the Boot Repair disk, but according to the Ubuntu site below, you can use unetbootin from windows to create a bootable flash drive of Boot Repair and use that to get the information. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by johnnie1 on 2014-09-12
Thanks for the reply. I made a bootable flash drive of boot repair using another computer but it comes down to the same problem when I try to boot from usb I don't get anywhere - just a blank screen with an underscore flashing in the top left..

---

### Post by johnnie1 on 2014-09-12
I'll try and get someone to make me a cd and see if that works any better...

---

