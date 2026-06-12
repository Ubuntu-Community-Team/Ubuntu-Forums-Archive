---
title: "I Think this is Right? Help"
date: 2008-03-17
forum: General Help
---

### Post by OllyNewport on 2008-03-17
Ok, right I did what *ago* said and use the 8.04 Wubi install, but the problem is I am having problems booting up, and it gives me lots of different errors each time about /temp files or the boot won't load, so I just want plain sailing, and just want a OS that isn't in beta and is stable, as the last time I installed Ubuntu wrong it re-formatted my whole HDD and I lost 100GB worth of very important files, so insted what I am going to do is this:

[LIST]
[*]Download and install Wubi 7.04
[*]Install Ubuntu 7.04
[*]Upgrade via the Ubuntu Upgrade Manager to 7.10, as I have a dedicated partiton.
[/LIST]

Now, the thing I would like to know is

[LIST=1]
[*]Would installing 7.10 muck up the bootloader from Wubi
[*]Should I even bother anyway
[/LIST]

So do you think that after install of Wubi 7.04 it would mean upgrading = the highway to disaster? So just upgrading will still keep the bootloader and I can use both XP and Ubuntu on startup of the computer.

Sorry if I sound n00bish but I need to ask these questions, as I am not huge techie and I need to clarify that what I am about to do won't cause my PC to fall to it's knees.

-Olly
Thanks for all peoples help

---

### Post by ago on 2008-03-17
> **OllyNewport said:**
> 
[*]Upgrade via the Ubuntu Upgrade Manager to 7.10, as I have a dedicated partiton.

If you have a dedicated partition it is easier to do a full installation of Ubuntu directly from LiveCD.

On wubi you cannot dist-upgrade from 7.04 to 7.10 unless you use LVPM to migrate to a dedicated partition BEFORE upgrading. As mentioned you might just as well install directly to a dedicated partition

---

### Post by uberlube on 2008-03-17
> **ago said:**
> If you have a dedicated partition it is easier to do a full installation of Ubuntu directly from LiveCD.

On wubi you cannot dist-upgrade from 7.04 to 7.10 unless you use LVPM to migrate to a dedicated partition BEFORE upgrading. As mentioned you might just as well install directly to a dedicated partition

Agreed. Your best bet is to do the install directly from the liveCD.

---

### Post by OllyNewport on 2008-03-17
> **ago said:**
> If you have a dedicated partition it is easier to do a full installation of Ubuntu directly from LiveCD.

On wubi you cannot dist-upgrade from 7.04 to 7.10 unless you use LVPM to migrate to a dedicated partition BEFORE upgrading. As mentioned you might just as well install directly to a dedicated partition

> **uberlube said:**
> Agreed. Your best bet is to do the install directly from the liveCD.

Ok, last time I don't know if it was right or not, but does the GRUB bootloader overright the MBR, and would GRUB automatically add XP to the list of bootable OS's? Last time I installed Ubuntu GRUB overwrote XP's MBR and I couldn't boot XP.

-Olly

---

### Post by ago on 2008-03-18
> **OllyNewport said:**
>  does the GRUB bootloader overright the MBR

Yes, it has too

> and would GRUB automatically add XP to the list of bootable OS's?
Yes

---

### Post by garferi on 2008-03-18
> **OllyNewport said:**
> ...as the last time I installed Ubuntu wrong it re-formatted my whole HDD and I lost 100GB worth of very important files...
When it happened did you use Wubi or normal Ubuntu install?
Thx!

---

### Post by OllyNewport on 2008-03-18
> **garferi said:**
> When it happened did you use Wubi or normal Ubuntu install?
Thx!

I used the LiveCD for Ubuntu 7.10, but I think it killed the partitions so I couldn't boot XP. Anyway I have it restored now, I will do what you all advise and thanks for the help everyone! :guitar:

---

