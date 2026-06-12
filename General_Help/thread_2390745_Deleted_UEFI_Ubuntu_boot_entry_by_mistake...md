---
title: "Deleted UEFI Ubuntu boot entry by mistake.."
date: 2018-05-02
forum: General Help
---

### Post by Godspell on 2018-05-02
Hi Guys/Girls,

Okay, amateur hour now...
I've got Ubuntu 18.04 LTS installed on my Dell laptop with full-disk encryption. Everything was working as intended and I was really enjoying it...except I've just removed its UEFI boot entry from BIOS by mistake and now I can't get back into it :-|

You see Ubuntu is the only OS on my laptop now but when I first got it, there was Win 10 pre-installed. However, after being stuck at 99% update overnight, I decided enough was enough and installed Ubuntu 17.10..and never looked back since then. When 18.04 came out, I did a fresh install and added the full-disk encryption to it. All was well..
Then, earlier when I was leisurely browsing the UEFI BIOS, (to my shock) I discovered the old *Windows Boot Manager* entry. The thing is I _despise_ leftover boot entries so in a moment of rage, I ticked and deleted it...except I choose the wrong one and deleted the Ubuntu entry ](*,)

Please, kind sirs and ladies, can you please help me unscrew this screw-up?? I don't wanna start messing about with the Grub restore without knowing what I'm doing as there's disk encryption involved..(and I'd rather not re-install the OS if at all possible).

Thank you.

---

### Post by Dennis N on 2018-05-02
You can probably run a command from the Ubuntu installer terminal in live mode to create a UEFI boot menu entry labeled "Ubuntu". 
Sample command, with Ubuntu EFI system partition on drive sda, partition #1:
```
sudo efibootmgr -c -d /dev/sda -p 1 -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi"
```
For more information on options, see man page of efibootmgr
Good luck.

---

### Post by dino99 on 2018-05-02
seen reports about such a problem, and users got satisfaction using boot-repair script

---

### Post by Godspell on 2018-05-02
> **Dennis N said:**
> You can probably run a command from the Ubuntu installer terminal in live mode to create a UEFI boot menu entry labeled "Ubuntu". 
Sample command, with Ubuntu EFI system partition on drive sda, partition #1:
```
sudo efibootmgr -c -d /dev/sda -p 1 -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi"
```
For more information on options, see man page of efibootmgr
Good luck.

That's done it!! Thank you so much :guitar:

---

### Post by Godspell on 2018-05-02
> **dino99 said:**
> seen reports about such a problem, and users got satisfaction using boot-repair script

Yeah, this was the first thing I tried but didn't work. All it did was added a Windows boot entry lol.
Thanks for the reply.

---

