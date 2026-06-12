---
title: "Grub Hangs on &quot;Starting Up . . . &quot;"
date: 2007-04-10
forum: General Help
---

### Post by Beatsake on 2007-04-10
Hello, I have 3 operating systems installed on 3 HDDs they all boot except one of them hangs on the " Starting Up . . .  "  screen just after selecting it from the grub boot menu. The operating system I'm trying to boot is Windows XP the the other drive is windows vista and it boots fine. 


The stanza for windows XP is as follows:

title             Windows XP Pro 
root           (hd1,0)
make active
chainloader        +1



That is the end
the one for vista "which boots with out hanging" is the same with the exception of title and the hd3 instead of hd1


I also tried adding the word  "boot"  on the line following "chainloader   + 1"




Because of my work I have to use windows as my primary OS and it would be Much more convenient for it to boot with out hanging that's all

Thank you in advance,
Beatsake

---

### Post by m.musashi on 2007-04-10
I had a similar problem but it was my Ubuntu partition that wouldn't boot. In my case it was because I had changed my HD order in the BIOS and it was looking for drives that no longer existed and just hung. I had to edit fstab to look for the partitions in the right location.

Have you made any BIOS changes? Was this working before and then suddenly doesn't? What changed?

If you are just setting this up it's possible that XP and Vista are competing. Windows has always been problematic if you had more than one copy. Vista is supposed to address this with some new boot loader, but I think you have to have ultimate (or maybe business). I don't know how it will go if you are using GRUB to manage two versions of windows. You may need to point GRUB at the vista boot loader. I remember reading something about this. I'll try and find it but it might be a while. I'm on my way out.

Can you post your menu.lst file? It might help to narrow down the problem.

---

### Post by Pisi-Deff on 2007-04-10
I'm not sure, but I think it should look something like this:
title Windows XP Pro
root (hd0,0)
map (hd1) (hd0)
map (hd0) (hd1)
make active
chainloader +1

Maybe it was the other way around tho :P

---

### Post by m.musashi on 2007-04-10
> **Pisi-Deff said:**
> I'm not sure, but I think it should look something like this:
title Windows XP Pro
root (hd0,0)
map (hd1) (hd0)
map (hd0) (hd1)
make active
chainloader +1

Maybe it was the other way around tho :P

What happens if he has 3 drives? I've never worked with three but would the map have to reflect that?

---

### Post by Beatsake on 2007-04-10
This is the pertenant of my Grub File:



title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot



title		Windows XP Pro 
root		(hd1,0)
makeactive
chainloader	+1


title		Windows XP Pro   chainloader	+1   boot
root		(hd1,0)
makeactive
chainloader	+1
boot


title		HD 2
root		(hd2,0)
makeactive
chainloader	+1


title		Windows Vista RC2
root		(hd3,0)
makeactive
chainloader	+1



title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot



Vista boots fine

Xp boots it I hit enter at the screen that says " Starting Up. . .  "

---

### Post by Pisi-Deff on 2007-04-10
> **m.musashi said:**
> What happens if he has 3 drives? I've never worked with three but would the map have to reflect that?
Well, that would change something only if windows would be on the third hd (hd2)
Anyway, I found some new info you might try.
```
title Windows
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
I'm not sure it'll work, but you can try, right?

---

### Post by Beatsake on 2007-04-10
Case Closed

Thank you Very much

Now to put some eye candy on the splash screen and I'll be done

BTW I like the GrubED Script for editing the Grub menu it works well :)

---

