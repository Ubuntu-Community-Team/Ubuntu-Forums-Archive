---
title: "Which GRUB?"
date: 2024-07-23
forum: General Help
---

### Post by ubername on 2024-07-23
Hi. I have two partitions on one drive. One has 24.04 on it and one has 24.10 on it. I have forgotten how to change the configuration so that the machine shows the grub menu  from the instance which has most recently been updated. I know how to update each grub, but I can not get the machine to boot showing the most recently updated grub menu. It would, of course, be great if both installations updated the same grub menu, but for now, I can live with manually switching between one grub and the other, if only I knew how! Any help is gratefully received!

---

### Post by deadflowr on 2024-07-23
The solution is to use a customized menu
See
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

caveat new version of Ubuntu use /boot/initrd.imd and /boot/vmlinuz instead of /initrd.img and /vmlinuz
so the entries should be  as such

```
initrd /boot/initrd.img other stuff
linux /boot/vmlinuz other stuff
```

Remove other stuff and replace with whatever the wiki says goes in there at that placement.
I'm being rather generic-ish.

But when successful anytime either systems kernel is updated the new kernel is automatically linked to those files.
And since grub is loading those files it'll load whatever new or old kernel is linked to it.

fwiw, I used this method for 10 years and so far have only needed to mess/play with it 3 times for new hardware, new installation reasons.
It's quite reliable.

---

### Post by ubername on 2024-07-23
Thanks! Your helpful answer has reminded me of the importance of asking the right question. In time I will, no doubt, use the technique you describe - I already have a reasonably customized grub on both instances. My real question should have been "How do I make the machine reboot using the grub menu of whichever partition I want?". In other words, I want to know the process from bios to grub menu and how to alter that to suit my particular circumstances.

---

### Post by dragonfly41 on 2024-07-23
I suggest that rEFInd installation might help you. I use it to multi boot across partitions (internal and external). It is in Synaptic.

---

### Post by ubername on 2024-07-23
Thanks again. I was kinda hoping to find the answer was "sudo grub-reinstall /dev/sda2" or "sudo  dpkg --reconfigure grub-pc" or similar. I still want to know how my machine knows which grub menu to display. My google-fu is letting me down! Refind looks very interesting - I will try it when I am on the affected machine. (p.s. I think you mean "Synaptic" as the front end to the various apt/dpkg/repositories)

---

### Post by oldfred on 2024-07-23
Last install is the default.
Ubuntu, official flavors and many others use "ubuntu" as UEFI boot entry and the folder in the ESP - efi system partition.
If you primarily boot one install, you just need to boot into that install & reinstall grub.
Note that major grub update will overwrite that and you have to update again.

You can also manually edit the ESP. But the esp you have booted from has very limited permissions in the fstab mount. You have to mount & edit from another install or change mount options. Boot-Repair still changes options, but it may be a bit of a security issues as then it is more open. I still change, but later my revert to more secure settings.

> [FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /boot/efi/EFI/ubuntu/grub.cfg [/COLOR]
search.fs_uuid 811e6de9-cd5e-4983-9f45-5e72e73cb578 root  
set prefix=($root)'/boot/grub' 
configfile $prefix/grub.cfg
[/FONT]

Boot will be to the UUID of / (root) or /boot (if using separate /boot partition where full grub.cfg is. And then grub in that install should offer to boot all other installs.
I have a lot of old test installs that are now obsolete, so use 40_custom for only those installs that I may want to boot. And turn off os-prober which improves grub's menu update as it does not have to search for all my installs.

---

### Post by dragonfly41 on 2024-07-24
> [COLOR=#000000](p.s. I think you mean "Synaptic" as the front end to the various apt/dpkg/repositories)

[/COLOR][COLOR=#000000]To err is human
[/COLOR][COLOR=#000000]

Yes, sorry, but I posted just before closing down after a tiring day.[/COLOR]

---

