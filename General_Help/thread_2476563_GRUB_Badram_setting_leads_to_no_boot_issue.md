---
title: "GRUB Badram setting leads to no boot issue"
date: 2022-06-29
forum: General Help
---

### Post by hugepickle on 2022-06-29
I ran memtester86+ on my 256GB RAM server running Ubuntu 20.04 and received the below result:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290675&stc=1[/IMG]

I added this value into [COLOR=#333333][FONT=Ubuntu]/etc/default/grub:

[/FONT][/COLOR][COLOR=#333333][FONT=inherit]GRUB_BADRAM="[/FONT][/COLOR]0x00000000935c89c0,0xfffffffffffffff8[COLOR=#333333][FONT=inherit]"[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]
Then, I ran [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]sudo update-grub2 and rebooted. After that, the machine wouldn't boot and just showed the bios logo for my motherboard forever. I used a Live Linux USB drive to repair GRUB, which removed the badram value, and was able to boot again. I repeated the steps above and had the same problem again. I'd love help to understand what I'm doing wrong. 

Also, I understand replacing the RAM is the ideal choice and that's the plan. For now, I'm looking to work around it temporarily. [/FONT][/COLOR]

---

