---
title: "How to lock Ubuntu installation to specific hardware?"
date: 2022-09-06
forum: General Help
---

### Post by apostolostpm on 2022-09-06
Hello,

I am trying to tie specific hardware to an Ubuntu installation and I can't seem to find anything useful on how this is done. 
Main goal is if anyone tries to move the nvme (hardware) to another computer, it won't boot, it won't be detected, it can't work.

---

### Post by miguel001 on 2022-09-06
> **apostolostpm said:**
> can't seem to find anything useful on how this is done.

That's probably because of what you're trying to do :)

Can't boot when placed in another computer? That's more of a drive controller itself thing. You can't really stop that.

You could write a script and use cron as probably a horrible way and just cause it to shutdown or whatever. But the user would still have OS access in certain ways.

Whole drive encryption would keep the OS from being booted but even on another computer if the user has the encryption password then they can boot in anyway. I would think this would be the best option if you can do it in a way that the user doesn't need that password and you deal with those problem times where its needed directly.

I understand the desire here. But, to achieve it I would think encryption of the drive is the likeliest way and dealing with that. The software for that would have to do the rest. Otherwise I think it might get a lot harder to achieve in the way you're wanting. But, I don't do this so there could be something else possible that I'm not aware of. I just think that's not terribly likely but possible.

---

### Post by SeijiSensei on 2022-09-06
Indeed. One of the things I like about Linux is the ability to move a disk drive with the OS to a new system and have it boot correctly. Done that a couple of times now.

---

### Post by MAFoElffen on 2022-09-06
I understand what you "ARE" trying to do security wise.

In my thoughts and expereince, I believe what may be your answer is to use LUKS to encrypted your partitions. That way, if someone does not know the passphrase, it won't matter if they leave it in your hardware or move it to another computer, the data cannot be accessed and it will not boot. (full luks-on-boot)

But... If someone takes your drive and repartitions the drive, they still have a usable drive.

To make that harder to access, there are Enterprize NVMe drives that are self-encrypting (some retail drives also have this feature) where the drive itself does the encryption, and if the wrong passkey is entered, it's locked. 

That said, there are still drive level / low-level ways to get around that, and to use the drive. Just makes that kind of thing harder...

So the answer to this is that it would be harder for someone else to use, but not impossible.

---

