---
title: "Questions about EFI-boot-files"
date: 2017-01-21
forum: General Help
---

### Post by clowncombat on 2017-01-21
Hello, all! :)

I am relatively new to Ubuntu and have it installed on an acer laptop.
I could not boot, until I selected an EFI-File in the bootMenu. (I choose grubx64 everytime and it worked)

Now, I had to do this again, and I always feel a little unsecure about it. So, my question is:
What should I search / google for to inform me about it, or what are some general advises? (Except being careful, cause its the bootmenu^^*')
Where can I delete previous created EFi-Bootfiles? Is there a limit to the amount of EFI-Files on can create  / assign?

My problem was I had to create / assign one, after an update-manager reboot and fear that I have to do this everytime now, the update-manager is needing to reboot.


Dear regards,
ClownCombat

---

### Post by Dennis N on 2017-01-21
This may help (or maybe not):

In the UEFI boot manager menu (if that is the boot menu you refer to), you need to change the boot order.

The universal way to do that is boot to an OS, then use the terminal command **efibootmgr**.

**sudo efibootmgr -v** lists the current boot order, and also the boot manager entries (not all shown here):

```
[dmn@Sydney ~]$ sudo efibootmgr -v
[sudo] password for dmn: 
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0003,0004,0005,0002
Boot0000* ubuntu	HD(1,GPT,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Manjaro	HD(1,GPT,8e6dba8f-5bdf-4b99-b7a4-2730717b1dba,0x800,0x64000)/File(\EFI\MANJARO\GRUBX64.EFI)
Boot0002* ubuntu	HD(1,GPT,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1,0x800,0x100000)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO
Boot0003* UEFI OS	HD(1,GPT,8e6dba8f-5bdf-4b99-b7a4-2730717b1dba,0x800,0x64


```According to BootOrder line, my system currently boots entry 0001 by default (Manjaro). The order of booting is defined by BootOrder line, not by the order of the detailed entries shown. To have 0000 boot by default, and 0001 be the next to try, the command is:

**sudo efibootmgr -o 0000,0001**

Here the first two I want in the boot order are specified - the system will fill in the rest of the boot order.

Reboot, and the new boot order should be in effect.

---

### Post by clowncombat on 2017-01-21
Thank you for the answer :),

the thing that bothers me, is that I had already changed the boot order once, to ubuntu first, and then after the reboot for the update-manager I had to set an EFI-file again.
Well for now, the problems seems solved.

---

### Post by oldfred on 2017-01-21
Acers are unique in that the require you to enable a supervisory password in UEFI and then set trust on the .efi boot files in the ESP - efi system partition from with in UEFI.

You can add & delete entries in UEFI with efibootmgr.
See 
man efibootmgr

Some more examples buried somewhere in the link in my signature.

---

### Post by Dennis N on 2017-01-21
> **clowncombat said:**
> Thank you for the answer :),

the thing that bothers me, is that I had already changed the boot order once, to ubuntu first, and then after the reboot for the update-manager I had to set an EFI-file again.
Well for now, the problems seems solved.

Do you have Windows on there? There are reports it can change the boot order itself:

[http://askubuntu.com/questions/838780/windows-10-changes-uefi-boot-order-every-time](http://askubuntu.com/questions/838780/windows-10-changes-uefi-boot-order-every-time)

---

