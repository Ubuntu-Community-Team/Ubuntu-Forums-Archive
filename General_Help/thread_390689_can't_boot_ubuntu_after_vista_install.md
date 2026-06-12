---
title: "can't boot ubuntu after vista install"
date: 2007-03-22
forum: General Help
---

### Post by Doug11 on 2007-03-22
OK, curiosity got the best of me. I had a 10gb partition with XP on it. Heard alot of hype about vista so I decided to try it. I wiped out and formatted my xp partiton and installed vista. Now when i boot, i dont get the bootup options anymore, it boots straight into vista, and I can't  get back into my Feisty. I seen this somewhere quite earlier but I couldnt find it. Any suggestions on what i have to do to get back to the boot option???????

---

### Post by mouseboyx on 2007-03-22
DONT: resize the part with vista on it (unless you don't want it to keep working) with gpart.

You just have to reinstall it and it will overwrite the boot with grub or something else that will probably allow you to dual boot.

---

### Post by raul_ on 2007-03-22
[http://www.sorgonet.com/linux/grubrestore/]("http://www.sorgonet.com/linux/grubrestore/")

You can follow those instructions using the ubuntu live cd

---

### Post by leeley on 2007-03-22
> **Doug11 said:**
> OK, curiosity got the best of me. I had a 10gb partition with XP on it. Heard alot of hype about vista so I decided to try it. I wiped out and formatted my xp partiton and installed vista. Now when i boot, i dont get the bootup options anymore, it boots straight into vista, and I can't  get back into my Feisty. I seen this somewhere quite earlier but I couldnt find it. Any suggestions on what i have to do to get back to the boot option???????

I do not know what you know about Linux or vista for that matter, but it really does not matter the reason that you lost you boot options is that you MUST install Vista then Linux(Ubuntu) as when you install ANY MICROSOFT VERSION it over writes the mbr where where the boot options are stored. You might be able to get your boot options back by booting from thje install disk a running in repair mode. I do not guarantee that this will work but it just might save you from doing a complete install. One question did you install Ubuntu on it&#347; own partition? if so what partition? All may not be lost if you ask the right questions with the right info.

You can e-mail me direct at [email]leewen@primus.ca[/email] if you do not get any more responces.

Lee

---

### Post by hikaricore on 2007-03-22
Questions like this make me really miss the old grub boot floppies linux
installations made for you in back then.  :P

If we had boot floppies as an option when installing ubuntu this would never happen.

*edit* well it WOULD happen, but it wouldn't be a major event when people
overwrote their MBR, they could just boot from a damn floppy.

---

### Post by Doug11 on 2007-03-22
> **hikaricore said:**
> Questions like this make me really miss the old grub boot floppies linux
installations made for you in back then.  :P

If we had boot floppies as an option when installing ubuntu this would never happen.

*edit* well it WOULD happen, but it wouldn't be a major event when people
overwrote their MBR, they could just boot from a damn floppy.


These days they don't even make machines with floppies anymore. But all said, I am back to the dual boot stage, everyting is back to normal. Found a couple of good wikis. OH, and am definately not overimpressed with Vista. It took over half an hour to get my logitech quickcam working, and that's with the install disc. Go figure.

---

### Post by raul_ on 2007-03-22
It's not a nightmare...just a couple of commands with the live cd. You can also use the Super Grub disk (floppy) to restore Grub.

---

### Post by hikaricore on 2007-03-22
> **Doug11 said:**
> These days they don't even make machines with floppies anymore.

Yea I noticed this when I needed to make a boot floppy for something on my girl's system, I was a little pissed to say the least.  Luckily I have a box in the closet with about 8 floppy drives in it.  =)

---

### Post by Doug11 on 2007-03-23
> **hikaricore said:**
> Yea I noticed this when I needed to make a boot floppy for something on my girl's system, I was a little pissed to say the least.  Luckily I have a box in the closet with about 8 floppy drives in it.  =)


Yes, I have to blow the dust off an old pII I have in the closet everynow and then as well. they are crap to use, but it would be the day after you give it away that you would need it the most.

---

