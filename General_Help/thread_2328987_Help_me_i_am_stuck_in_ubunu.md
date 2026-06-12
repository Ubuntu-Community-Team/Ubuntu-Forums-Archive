---
title: "Help me i am stuck in ubunu"
date: 2016-06-26
forum: General Help
---

### Post by arik5 on 2016-06-26
hello i done a dual boot with windows 10 and ubuntu, i hav[SIZE=2]e[/SIZE][SIZE=1] [SIZE=2]managed to boot into ubuntu and when i wanted to return to windows and restarted the computer there was'nt any menu to select operating. I don't know what to do and i need my windows badlly[/SIZE][/SIZE]

---

### Post by yancek on 2016-06-26
Is your windows 10 system one that was pre-installed when you purchased the computer?  If it was, then you are almost certainly using UEFI and if that is the case, you would need to have booted Ubuntu UEFI and installed UEFI.  If I understand correctly, you are able to boot Ubuntu but not windows, correct?  If that is the case, boot Ubuntu and go  to the site below and get boot repair and run it.  Make sure you select the option to Create BootInfo Summary and do not try to make any repairs.  You can post a link to the boot repair output here and someone should be able to advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by arik5 on 2016-06-27
> **yancek said:**
> Is your windows 10 system one that was pre-installed when you purchased the computer?  If it was, then you are almost certainly using UEFI and if that is the case, you would need to have booted Ubuntu UEFI and installed UEFI.  If I understand correctly, you are able to boot Ubuntu but not windows, correct?  If that is the case, boot Ubuntu and go  to the site below and get boot repair and run it.  Make sure you select the option to Create BootInfo Summary and do not try to make any repairs.  You can post a link to the boot repair output here and someone should be able to advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

every thing that you assumed is right, i done the BootInfo Summary and here is the link: [http://paste2.org/78zDy0Wn](http://paste2.org/78zDy0Wn) .  [SIZE=4]please help me it is very urgent[/SIZE]

---

### Post by banceu_sergiu_ione on 2016-06-27
What happen if you press ESC or Shift after UEFI louded? Does you get the grub menu ? 

if not work can you put the output of 

```
cat /etc/default/grub
```

---

### Post by arik5 on 2016-06-27
i used the boot repair tool and selected to repair the problem and it worked now the widows 10 option is exist. [COLOR=#212121][FONT=inherit]Thanks[/FONT][/COLOR]

---

### Post by banceu_sergiu_ione on 2016-06-27
OK, mark as solved. 

You can hide/show grub if press ESC after UEFI/bios is loaded. So you not need to run the boot-repair only to show the grub menu.

---

