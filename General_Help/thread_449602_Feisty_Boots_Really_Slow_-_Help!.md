---
title: "Feisty Boots Really Slow - Help!"
date: 2007-05-20
forum: General Help
---

### Post by LukeCarrier on 2007-05-20
I'm absolutely sick to death of Ubuntu, its problem after problem after another ruddy problem. To fix loads of other issues, I wiped my PC and installed Ubuntu 7.04, and it is absolutely awful. Ubuntu now takes about three minutes to boot, nearly five times longer than Windows on an identical machine. Please help me, I'm losing my rag and am seriously considering abandoning all hope on Ubuntu and going back to Windows XP.
Sorry about this, I've had enough of this.
Please reply, thanks in advance.

**EDIT:** the problem disappears when I disconnect the power cables from both my DVD-RW and CD-RW drives. The boot time goes back to the normal 40 seconds. PLEASE HELP, I NEED THIS FIXED OR I'M GOING TO INSTALL WINDOWS. I MAY HATE IT BUT IF UBUNTU WON'T WORK I'M GOING TO INSTALL IT ANYWAY.

---

### Post by patrickfromspain on 2007-05-20
What motherboard do you have? What DVD-RW and CD-RW? This could help.. seems that you hardware isn't well supported.

EDIT: just that you know, don't use capital letters in a forum, it is unpolite, as you were shouting.

---

### Post by LukeCarrier on 2007-05-20
Thank you very much for replying, I'm really frustrated (as you can tell) from trying to sort this. My system specs are:
Asus A7S8X-MX Motherboard
AMD Sempron 2400+ Processor
512MiB RAM
160GiB IDE HD (Samsung)
DVD-RW Drive (BenQ)
CD-RW Drive (Sony CyberDrv?)
I found I can get he boot time down to 50 seconds (including BIOS) without the CD drives plugged in, I hope this helps.
Thanks again, Luke.

---

### Post by bobplano on 2007-05-20
it could be trying to read off them or taking awhile to load the drivers for them. when you get to grub there should be a boot options button you can press and after you press that somewhere there should be boot "quiet". just remove quiet and it will show all the processes it is going through. if you could tell us what it is taking so long on that would be useful. i have dapper so it already does that, so sorry if the instructions are vague.
EDIT: here's how to show the processes in fiesty fawn [http://ubuntuforums.org/showthread.php?t=449657](http://ubuntuforums.org/showthread.php?t=449657)

---

### Post by LukeCarrier on 2007-05-21
Thanks,
I already have taken out the word 'quiet' from the /boot/grub/menu.lst, and it takes ages when it gets to the point 'loading hardware drivers'. It waits for about a minute and a half when it gets here, and the progress bar stops moving. I don't know whether this would have anything to do with it, but I did have the 'GRUB Error 18' problem when I first installed Feisty, which I worked around by changing my BIOS so the access mode for the hard disk was CHS. This allowed me to boot the PC as normal.
Thanks again, Luke

EDIT: I might go back to  Dapper, its the only version I never had problems with :lolflag:

---

### Post by hessiess on 2007-05-21
3 munites isant that bad!

---

### Post by LukeCarrier on 2007-05-21
> **hessiess said:**
> 3 munites isant that bad!

My PC boots Windows XP in 25 seconds, and Dapper in about 30. Yes, it is that bad.

---

### Post by hessiess on 2007-05-21
> **LukeCarrier said:**
> My PC boots Windows XP in 25 seconds, and Dapper in about 30. Yes, it is that bad.

windows on my computer takes 2 munites to boot, 1 munit to log on, then 10 munites to become usable. ubuntu  now boots completly in about 1.5 munites. it origanaly booted in under a munit. i dont rilly care about boot times as its hardly ever rebooted.

see, 3 munites isant bad!

---

### Post by LukeCarrier on 2007-05-22
Well...I was hoping somebody might help but this is stupid, its turning into an argument about boot times. Please can I have a hand, I'm not sticking with Ubuntu if I have to wait 5-10 minutes for it to boot.

---

### Post by hessiess on 2007-05-22
> the problem disappears when I disconnect the power cables from both my DVD-RW and CD-RW drives. The boot time goes back to the normal 40 seconds. PLEASE HELP, I NEED THIS FIXED OR I'M GOING TO INSTALL WINDOWS. I MAY HATE IT BUT IF UBUNTU WON'T WORK I'M GOING TO INSTALL IT ANYWAY.

then theres obvisaly somthing with your cd drive that ubuntu dosant like, try googling for problems (make of your drive) in linux/ubuntu

if its rilly problamatic then just make a dual boot. try a difarent kernal and or a older verson of ubuntu, or a difarent dist.

---

### Post by LukeCarrier on 2007-05-22
As I have said previously, I have used the exact same box, no upgrades at all with Dapper with absolutley no problems. Please hear me out, I want to use Feisty not Dapper, I want help with the boot problem, not a work-around.:(

---

### Post by patrickfromspain on 2007-05-22
hi there...

maybe you could try to add this to your grub (after quiet splash). Try one or another:

irqpoll
noapic
pci=noapic

---

### Post by LukeCarrier on 2007-06-11
I've got some bad news,

I've gone back to Windows XP, which I'm going to use until Ubuntu becomes a little more stable, and Wine (or VMware) become a little more stable and work better. Trust me I'd love to use this OS, but it just doesn't work for me, and I don't have the knowledge to solve the problems. I'm thirteen, I've got way better things to do than sit scratching my head over some stupid command at a terminal, or sitting there editing text files myself, written in some cryptic language.

I'll come back when Ubuntu works out the box, until then sorry but I'm not prepared to put up with this, it's just well and truly ridiculous.

Luke

---

### Post by deadlikeoscar on 2007-06-11
I think that you made everything way too complicated. You said you unplugged your drives. Did you unplug one? Did it work? If not, did you plug it back in and unplug the other one? You know there is a conflict with your drives but you never found out which one. Is one master and the other slave? Both cable select? One master and one cable select? If your DVD-RW drive works with the other drive unplugged (does it?) why do you need the CD-RW drive installed then? Burning directly from drive to drive increases your risk of burning coasters--just use the DVD-RW one if you can. Whether you use Windows or Linux, this is the kind of hardware troubleshooting you need to learn. I know you said you are only 13; and we all know that you don't need to be a mechanic to drive a car, but you should at least know how to check your oil. Best of luck to you no matter what OS you end up with in the future.:D

---

