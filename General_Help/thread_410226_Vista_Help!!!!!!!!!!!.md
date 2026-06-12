---
title: "Vista Help!!!!!!!!!!!"
date: 2007-04-15
forum: General Help
---

### Post by UltraM4n on 2007-04-15
AIEEEE!!!
SOMBODY HELP ME!!
I just installed ubuntu on my computer...and now vista wont boot T_________T
When i try to boot it, i get to the loader screen, the little status bar freezes at some points, and wont boot. PLEASE HELP ME QUICKLY!!

---

### Post by zenwalker on 2007-04-15
I read some where that VISTA (The crap software ever) has some problems with the linux in dual boot situation.

---

### Post by UltraM4n on 2007-04-15
Vista it self is pretty nice..but i need help fast!

---

### Post by Wim Sturkenboom on 2007-04-15
Quite sure that the Vista disk has a recover option to reinstall its bootloader (in WinXP it's fixmbr if I remember correctly). You will no longer be able to boot Ubuntu.

---

### Post by Quillz on 2007-04-15
Vista doesn't work with with Linux dual-booting at the moment.

---

### Post by raffytaffy on 2007-04-15
guys ,..name calling is not very nice...now as to your problem this is what i was able to find.
[http://desktoplinux.com/articles/AT2094892904.html](http://desktoplinux.com/articles/AT2094892904.html)

---

### Post by UltraM4n on 2007-04-15
> **zenwalker said:**
> Also try to give some respect.....Thats humanity and manners!! :x

Look, I'm sorry about that. I'm just tense. Anyway i dont think my computer can boot from a DVD.

---

### Post by rsambuca on 2007-04-15
> **Quillz said:**
> Vista doesn't work with with Linux dual-booting at the moment.

Uh, sorry but you are mistaken on this one.  There are definite problems when you re-size an existing Vista partition, but if the partitions are set-up prior to installation of the OS's, Vista and linux will dual boot quite easily.

---

### Post by diatribe on 2007-04-15
just put in the vista cd that came with your computer and it should work, if not you're about ****** in the game

---

### Post by Hendrixski on 2007-04-15
Help forums are not a bash other operating systems forum.  If you want to see how bad it looks when someone bashes operating systems check out [www.linuxsucks.org](www.linuxsucks.org)... do you want us to look like that?

Anyway, I haven't heard about the Vista not playing with Linux thing (but the again, I have only one OS on my computer).  I know that there were some issues with specific programs like Samba having to catch up to the new specs from Microsoft for Vista, but bootloading?  Doesn't Dell sell dual boot laptops with Fedora and Vista?

---

### Post by m0eman on 2007-04-15
I tried vista a week ago and I installed it, and then I fixed the mbr so grub would take it over again and everything worked fine for me. I could boot my feisty, my xp, and vista. I ended up deleting vista anyway because everything about it annoys me.

---

### Post by UltraM4n on 2007-04-15
Well i can see the vista selection in Grub, i select it, it goes to the booter...but it never boots! What i mean by booter is the little status bar. It will like move...then freeze for a few seconds...then freeze again. I tryed booting into safe mode and it stops at like cydisk.sys or something like that.

---

### Post by m0eman on 2007-04-15
did you try the link that raffytaffy posted?
[http://desktoplinux.com/articles/AT2094892904.html](http://desktoplinux.com/articles/AT2094892904.html)

near the middle there's a section to help you dualboot with vista

---

### Post by silverglade00 on 2007-04-15
> **Quillz said:**
> Vista doesn't work with with Linux dual-booting at the moment.

That's funny, I've been doing it for 2 months now. The trick is you cannot use Linux to resize the Vista partition. You have to go into Vista and use the parition manager in there to resize it. Freakin Microsoft changed NTFS on us.

---

### Post by UltraM4n on 2007-04-15
> **silverglade00 said:**
> That's funny, I've been doing it for 2 months now. The trick is you cannot use Linux to resize the Vista partition. You have to go into Vista and use the parition manager in there to resize it. Freakin Microsoft changed NTFS on us.

o_____o....i think that might be the problem...i used Ubuntu's Partition manger to create it...am i screwed!?

---

### Post by Espreon on 2007-04-17
Ugh... Linuxsucks.org is a horrible site! It is just like a hate site, now I think Hendrixi is right lets's not bash other OSes otherwise we are no better than them. (Eventhough I really don;t like Winblows that much).

---

### Post by Doug11 on 2007-04-18
> **Quillz said:**
> Vista doesn't work with with Linux dual-booting at the moment.

Vista does work with dual booting Linux. I had that same problem when I tried to get both going. Here's what I had to do to solve it. Get your hands on an old XP disc,(the vista didn't work) boot it as if you were doing a fresh install, let it install all the files until you get to the point where it wants to format your drives. Cancel out of everything from there and reboot. This should bring your vista back to life, but without the grub menu. To get your grub menu back, just boot from your Ubuntu Live CD and follow these instructions

[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

Good luck!

---

### Post by zeekay on 2007-04-18
That's one of the reasons why you should install linux AFTER installing any other OS, if you wish a dual boot. Ubuntu on it's installation WILL detect the other systems you got and it will most likely automatically configure grub to boot them.

I'll only know that 100% once I download my feisty and install it from scratch, but at the moment I'm 99% sure and that seems to be enough :P

---

