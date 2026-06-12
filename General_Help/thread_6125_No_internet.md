---
title: "No internet"
date: 2004-11-25
forum: General Help
---

### Post by Fintan on 2004-11-25
Hi, I wrote about this a while ago.

I have various dists installed and they all boot from a kanotix grub.

When i boot ubuntu everything is fine exept i cannot get an internet connesctio.
Neither with DCHP or manual card config. The eht card is active.
If i install ubuntu to boot from mbr it works, so why does it refuse 
when i boot from a different grub.

Any ideas would be helpfull
cheers
Fintan

---

### Post by spirospr on 2004-11-25
You don't mention how you try to connect to internet. You mention eth card so i asume you are trying to connect through a router or sth to pernament connection or a sherd connection to another pc.

Well what worked for me is setting as DNS the default gateway where the pc is assumed to connect to internet. 

Be more specific so that we can help you

---

### Post by Fintan on 2004-11-25
Hi spirospr,
Yes i am connecting through a ASDL router and i can configure DHCP or manual.
The question still remains why i can connect with an install with grub in mbr(hda1) and not with an install with a diferent boot manager in mbr(hda1).

[QUOTE=spirospr]You don't mention how you try to connect to internet. You mention eth card so i asume you are trying to connect through a router or sth to pernament connection or a sherd connection to another pc.

Well what worked for me is setting as DNS the default gateway where the pc is assumed to connect to internet. 

Be more specific so that we can help you[/QUOTE]

I love your dist but i need winfud for macromedia and adobe stuff.
I use linux for everything else, like intenet communications.

By the way i have had the same prob. the other way around with kanotix, yoper, suse. 
For some reason no dist likes the other bootmanager on this point.
It is not logical because as an os i don't care what or where i am booted from unless i am wnfud.
Can you help?
Cheers
Fintan

---

### Post by wallijonn on 2004-11-25
[QUOTE=Fintan] why does it refuse when i boot from a different grub?[/QUOTE]

Because the other distro (the one that has control over GRUB) is not set up correctly.

You have to add the usual Ubuntu lines to it's GRUB or LILO, like ```

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu, kernel 2.6.8.1-3-686 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-686
savedefault
boot

```

---

