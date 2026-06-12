---
title: "Having Trouble adding UEFI entry using efibootmgr"
date: 2013-11-29
forum: General Help
---

### Post by ggaub1 on 2013-11-29
I am trying to rename the boot label of ubuntu. In order to rename the label, I have to delete the entry and create it again. How ever efibootmgr seem to not recognize the correct partitionhere is what I do to create the entry
```
sudo efibootmgr -c -w -l \\EFI\\ubuntu\\shimx64.efi -L "Lubuntu" -p 2 -d /dev/sdb2
```
This works, however right after I reboot this entry is deleted. When I do efibootmgr -v I get this
```
Boot0003* Lubuntu   HD(2,0,0,500a0dff)File(\EFI\ubuntu\shimx64.efi)
Boot0007* Ubuntu    HD(2,1f4800,82000,adcf2808-6afb-47fc-be64-5ce73ca83859)File(\EFI\ubuntu\grubx64.efi)RC
Boot00A5* Windows Boot Manager  HD(2,1f4800,82000,adcf2808-6afb-47fc-be64-5ce73ca83859)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...s................
```
"Ubuntu" is the working entry. As you can clearly see, they are pointing to totally different places, yet the files are in the same place.Any ideas?

---

### Post by oldfred on 2013-11-29
UEFI remembers in its memory settings. Sometimes manual changes or several reboots required to reset.

One user posted this. But I think his UEFI directly worked as efibootmgr.
 Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
And to remove entries as UEFI remembers them.
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.

I would backup efi partition before changes. What happens if you just copy your ubuntu folder to Lubuntu? Do you then get two entries in UEFI (that are really identical)?

---

### Post by ggaub1 on 2013-11-29
Turns out the problem was that I wasn't using the comman properly 
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)

---

