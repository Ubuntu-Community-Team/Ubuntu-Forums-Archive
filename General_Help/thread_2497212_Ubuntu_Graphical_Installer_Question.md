---
title: "Ubuntu Graphical Installer Question"
date: 2024-04-27
forum: General Help
---

### Post by Rubi1200 on 2024-04-27
Hi,

I would like to install 24.04 but without the bootloader.

I do not see that option when starting Ubiquity and selecting Manual Installation. Only options are either sda or sdb. I was hoping to see do not install bootloader but perhaps I missed something?

Would this work from the terminal?

```
ubiquity --no-bootloader
```

I do not see the option on the manpage:
[https://manpages.ubuntu.com/manpages/noble/en/man8/ubiquity.8.html](https://manpages.ubuntu.com/manpages/noble/en/man8/ubiquity.8.html)

Looking forward to clarifications.

Thanks!

---

### Post by ajgreeny on 2024-04-27
Ubuntu 24.04 does not use ubiquity so I not sure of the reasoning behind your query. 

Give us as much detail as possible and perhaps we can move forward on this subject.

---

### Post by Rubi1200 on 2024-04-27
My mistake then. Which installer is currently being used?

The situation is like this:
I want to install 24.04 to sda6.

I have another install on sda5 with a custom GRUB configuration that I really would rather not have to redo.

That is why I prefer that Ubuntu not install its bootloader.

Thanks.

---

### Post by ajgreeny on 2024-04-27
Sorry but I've installed 24.04 using the new bootstrap installer in KVM/QEMU where I allow it to install as default onto the virtual disk.

I have never looked into changing the bootloader site using this new installer but in the old ubiquity version a bug meant it ignored any choice you made and put grub into it's default location.
Maybe the new one behaves itself; wait for other replies before going any further.

---

### Post by Dennis N on 2024-04-27
I would allow the new OS to install bootloader to sda, and after installation is complete, restart and edit:
/boot/efi/EFI/ubuntu/grub.cfg

it looks like this:
```
search.fs_uuid 77e5c27d-4818-4b8f-b38a-597dcd57bb7e root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

```
Change the uuid in the **search.fs_uuid** line to the uuid of the root partition of the older install. Save the file and restart. System will boot to the older sda5 install. Run sudo update-grub to add the new OS to the grub menu of the older OS.

---

### Post by Rubi1200 on 2024-04-27
In other words, there is no way to tell subiquity to NOT install the bootloader? Even using cli parameters?

---

### Post by dragonfly41 on 2024-04-27
Without understanding the full context of requirements ..
(a) you might install rEFInd, set that as priority boot order in BIOS and customise UI in the rEFInd config file
or
(b) install grub-customizer

[https://launchpad.net/%7Edanielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/%7Edanielrichter2007/+archive/ubuntu/grub-customizer)

But note here .. [https://askubuntu.com/questions/1404445/grub-customizer-missing-from-ubuntu-22-04](https://askubuntu.com/questions/1404445/grub-customizer-missing-from-ubuntu-22-04)

---

### Post by Rubi1200 on 2024-04-27
Appreciate the response but I have always been one of the users who recommends against using Grub Customizer.

The question is whether or not it is possible to install Ubuntu 24.04 without a bootloader and if so how.

Thanks.

---

### Post by #&amp;thj^% on 2024-04-27
> **dragonfly41 said:**
> Without understanding the full context of requirements ..
(a) you might install rEFInd, set that as priority boot order in BIOS and customise UI in the rEFInd config file
or


+1 for rEFInd, it's very adaptable, and will show all bootable drives even swapping them out.

You still need a bootloader though....More on this later I have meeting ATM

---

### Post by tea for one on 2024-04-27
> **Rubi1200 said:**
> The question is whether or not it is possible to install Ubuntu 24.04 without a bootloader and if so how..
I think that you've stumbled upon a feature or a reportable bug.
There doesn't seem to be an option for "no-bootloader"

The installer for 24.04 is called snap:ubuntu-desktop-bootstrap	(stable/ubuntu-24.04	114)
If you try this in the terminal, you'll see that few options are available:-
```
ubuntu-desktop-bootstrap --help
```

---

### Post by Rubi1200 on 2024-04-27
> **1fallen said:**
> +1 for rEFInd, it's very adaptable, and will show all bootable drives even swapping them out.

I understand why users would find this an attractive option. However, I am used to my custom GRUB configurations and prefer to keep it that way.

Once you get the hang of the syntax, writing custom GRUB files or modifying existing files with customizations is actually not that hard.

---

### Post by Dennis N on 2024-04-27
> **Rubi1200 said:**
> In other words, there is no way to tell subiquity to NOT install the bootloader? Even using cli parameters?
Do you see that the end result of the edit will be the same as not installing a boot loader for the 2nd OS?

---

### Post by Rubi1200 on 2024-04-27
> **Dennis N said:**
> Do you see that the end result of the edit will be the same as not installing a boot loader for the 2nd OS?
You are right of course. Either way I will be editing in some way or another.

I do find it odd that the installer does not offer the option but I guess there must be good reasons for this.

My solution was to install Ubuntu normally and then chroot into the other OS to reinstall GRUB with all my custom settings.

Appreciate all the input.

---

