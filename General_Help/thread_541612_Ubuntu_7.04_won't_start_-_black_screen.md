---
title: "Ubuntu 7.04 won't start - black screen"
date: 2007-09-03
forum: General Help
---

### Post by jamiepane on 2007-09-03
Hello all,

I've searched the forum, and read several threads with people who are having an issue similar to mine, but I really didn't read any direct answers. I'm hoping some one can help.

I installed Ubuntu 7.04 onto my external hard drive at a friend's house. Installation went fine, and it worked perfectly on my friend's computer.

I get home, plug in my external hard drive into my computer, and Ubuntu wont boot. I get the following:

--[GRUB Loads]--

"Starting Up...
Loading, please wait..."

Following about 10 or so seconds of that, the screen goes blank. No writing, no nothing. Just blank.

I wait about 10-15 minutes, and nothing happens.

I also tried it on a laptop in my house, and it works perfectly on that. Therefore, it's only an issue on MY computer.

BUT... I have a Virtual Machine running off of my external hard drive, so I can use Ubuntu on top of Windows XP and it works fine -- I just can't boot it directly off of my external hard drive (by going to BIOS and booting from "USB Device.")

Also - My computer, for some odd reason, won't boot the Live CD. Or any boot-able CD, for that matter. So "try booting from the Live CD" suggestions wont work. 

Is this a video card problem? If so, how can I fix it?

Any replies are appreciated! :)

---

### Post by kesman on 2007-09-03
I'm not sure if you can, but you should try to access the boot parameters of the kernel during the grub load and disable the splash image during the boot process to see what's the problem.
I'm not on my own pc right now so I cannot tell you how to edit those parameters on boot-up, but I think it's possible to do so.

---

### Post by jamiepane on 2007-09-03
> **kesman said:**
> I'm not sure if you can, but you should try to access the boot parameters of the kernel during the grub load and disable the splash image during the boot process to see what's the problem.
I'm not on my own pc right now so I cannot tell you how to edit those parameters on boot-up, but I think it's possible to do so.

I'd love to try this, but I don't know how. If you can tell me when you get on your PC, please let me know!

---

### Post by kesman on 2007-09-03
check out
[http://ubuntuforums.org/showthread.php?t=448204&highlight=edit+boot+parameters](http://ubuntuforums.org/showthread.php?t=448204&highlight=edit+boot+parameters)

there's similar problems. Hope it helps!

---

### Post by Milky The Brown Cow on 2007-09-03
> **kesman said:**
> I'm not sure if you can, but you should try to access the boot parameters of the kernel during the grub load and disable the splash image during the boot process to see what's the problem.
I'm not on my own pc right now so I cannot tell you how to edit those parameters on boot-up, but I think it's possible to do so.

Hey Jamie,

ok, im assuming that you get the choices of "ubuntu blah blah blah" and "ubuntu blah blah blah safemode" and "ubuntu memtest blah", and if so, try safemode. if you [I]dont[I] have it (and you should) then under the boot options, hit "e" and then hit "e" again for the option that says " kernel 2.60. blah blah blah" its really long. at the end, where it says "ro spash quiet" change it to "ro single" adn that should boot safe mode, without the splash image. if that boots ubuntu for you, go to the terminal (i put it on your desktop when you were at my place, so it should be right there) and type "sudo gedit /boot/grub/menu.lst" and find towards the bottom where it says "kernel 2.6 and so on" and do the change outlined above to the one there. if this doesnt work, try putting LILO on a floppy and using that to boot ubuntu. if you need to do that, email me and ill email you the specifics. GL!
                                              ~max

---

### Post by jamiepane on 2007-09-03
> **kesman said:**
> check out
[http://ubuntuforums.org/showthread.php?t=448204&highlight=edit+boot+parameters](http://ubuntuforums.org/showthread.php?t=448204&highlight=edit+boot+parameters)

there's similar problems. Hope it helps!

I read that thread, and it seems that the problem is with the Server Edition. I'm trying to access Ubuntu 7.04 FF Home. Not server.

If they're off any relavence, heres my computer info:

Dell Dimension 2400
Intel Celeron CPU 2.40 GHZ
640 MB of RAM

I've tried booting with recovery mode, and making sure to configure it and make it "ro single", so that it has the scrolling text, but no luck. It gives me a ton of errors, and ends with "Boot I/O" errors (something like that..) before basically freezing and not doing anything at all.

Any other solutions? Like I said, this is the only computer that this does not work on.

---

### Post by jamiepane on 2007-09-03
Wow, this thread has been covered by three pages already!

Any ideas of what the problem could be?

Does it take a looooong time to boot from recovery mode with "ro single"?

---

