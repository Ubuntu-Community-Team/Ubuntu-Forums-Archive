---
title: "Dual boot with vista; want to get rid of ubuntu and grub"
date: 2008-02-24
forum: General Help
---

### Post by Redrazor39 on 2008-02-24
This laptop has hardware problems with ubuntu and I may consider removing it from this particular machine. Don't worry, I'm not giving up on ubuntu completely. I dual boot Windows Vista Business and Ubuntu 7.10. I dual booted with Vista's disk management tool and I was wondering if I destroyed the partition and then expanded the Vista one, would GRUB still remain? How would I get rid of GRUB so it skips that and just goes straight into normally booting Vista, well, what I mean is, how do I COMPLETELY get my computer back to the way it was before I even put in the live CD for ubuntu in the first place.

Please help. I'm still on the ubuntu side, so don't go against me or anything. You guys seem great so far, so hopefully you can help. Thank you so much.

---

### Post by danwood76 on 2008-02-24
Yes you can delete the ubuntu partition and expand the vista partition into that space.
You will however need to reinstall the vista MBR for it to boot your vista partition up.

If you have a vista install disk then its very simple.
Boot the CD, choose recovery and firx boot problems (or fixmbr)

---

### Post by Redrazor39 on 2008-02-24
I bought this laptop with Vista preinstalled, so idk.

---

### Post by L815 on 2008-02-24
Fixing the boot record (removing grub) with vista is a bit different than XP.

What you have to do is get the Vista install disk, and choose the "Command Prompt" option.

Type "bootsec.exe /fixmbr" (without quotes)
 (I think that's the exact command)

That is the equivalent to fixmbr with XP.

After that, just format the Partition that Ubuntu is on, and Expand it with Computer Management > Disk management.

---

### Post by Redrazor39 on 2008-02-25
Is there a way to do this without a disc?

And I'm not sure, but I MAY have the recovery discs Geek Squad at Best Buy made. Will those/that work the same way?

---

### Post by L815 on 2008-02-25
I'm not sure. The recovery disks I made from my Laptop has the command prompt option. 
Your best bet is to check for yourself and see if it's there.

Although, I haven't tried fixing the mbr with the recovery disk command prompt, so if it works for you , post the results :D

---

### Post by Redrazor39 on 2008-02-25
But first, before I say goodbye and try all that stuff out, what is the point of using ubuntu over vista or leopard besides the fact it's free and it's open source (I couldn't code a triangle if I tried- I don't know a line of code)?

---

### Post by danwood76 on 2008-02-26
Well its an ever evolving operating system which is as customisable as you like.
Obviosuly it helps a little if you know some programming as it means you can change/hack something if it doesnt work how you like.
But ive found it to be far more stable than any windows ive tried.
I used to find vista would get unstable after 24 hours of being on but ubuntu is stable all the time.

Btw the super grub disk (search google for it) has the option to restore winows MBR I think.

good luck,
Danny

---

