---
title: "Can't boot in Ubuntu, after installation."
date: 2007-10-15
forum: General Help
---

### Post by Elf Wizard on 2007-10-15
[COLOR=Navy][B]Hi!:D

[/B]I just installed wubi under xp. My problem is that I can't boot in ubuntu.

I can see the "Ubuntu" entry in ntldr, but it seems to be empty, so nothing happens. The boot.ini entry is "[COLOR=DarkGreen]c:\wubildr.mbr="Ubuntu"[/COLOR]".

Any possibility to edit manually [/COLOR][COLOR=Navy][COLOR=DarkGreen]wubildr.mbr, [COLOR=Navy]or any other workarround?


[B]THANKS!!!
[/B]Giorgos.:cool:[/COLOR][/COLOR][/COLOR]

---

### Post by ago on 2007-10-15
> **Elf Wizard said:**
> 
I can see the "Ubuntu" entry in ntldr

Do you mean the ubuntu entry in boot.ini ??? What do you exactly mean by looks "empty"?

---

### Post by anandanbu on 2007-10-15
Would be better to answer if you could provide with some more details :)

---

### Post by Elf Wizard on 2007-10-15
> **ago said:**
> Do you mean the ubuntu entry in boot.ini ??? What do you exactly mean by looks "empty"?
[COLOR=Navy]Ooops! **SORRY **guys!:(
Seems like my posting was pretty confusing!:confused:
So, I'm trying again.

When I rebooting, ntldr is launching. I can see there, the "Ubuntu" entry.
But when I'm pressing "enter", nothing happens (black screen returned and absolutely no disk activity).
[/COLOR][COLOR=Navy]
I was wondering, if there is a way, to do something,  so that [/COLOR][COLOR=Navy]ubuntu [/COLOR][COLOR=Navy]can [/COLOR][COLOR=Navy]be launched .

I hope this post is better understandable now! Thanks for your patience!:)

My boot.ini entry is [/COLOR][COLOR=Navy][COLOR=DarkGreen]c:\wubildr.mbr="Ubuntu
My disk is IDE, Windows are xp sp2.
[/COLOR][/COLOR]

---

### Post by ago on 2007-10-15
Do you see wubildr.mbr and wubildr in C:\?

---

### Post by Elf Wizard on 2007-10-15
> **ago said:**
> Do you see wubildr.mbr and wubildr in C:\?
[COLOR=Navy]Yes, they're both there:

[COLOR=DarkGreen]wubildr.mbr 8KB[/COLOR][/COLOR]
[COLOR=DarkGreen]wubildr 176KB

[COLOR=Navy](I checked also my disk with chkdsk/f . Nothing bad found).[/COLOR]
[/COLOR]

---

### Post by ago on 2007-10-15
Is your drive compressed?
Also try to rapidly press inf during boot (as soon as you select "Ubuntu")

---

### Post by Elf Wizard on 2007-10-15
> **ago said:**
> Is your drive compressed?
[COLOR=Navy]No. I checked again wubi and ubuntu files. Nothing is compressed. (there are only some compressed folders here, that windows autocompressed them in other disk locations (eg. sp2 installation files).).[/COLOR]
> **ago said:**
>  Also try to rapidly press inf during boot (as soon as you select "Ubuntu")
[COLOR=Navy]Sorry for asking that, sounds silly, but I can't see an inf key.
Maybe have I to type inf (pressing i, n, f one after another)?[/COLOR]

---

### Post by ago on 2007-10-15
> **Elf Wizard said:**
> No. I checked again wubi and ubuntu files. Nothing is compressed. (there are only some compressed folders here, that windows autocompressed them in other disk locations (eg. sp2 installation files).).What I mean is that windows allows you to compress a full drive, this may create problems if that is the drive used to install wubi.

> Sorry for asking that, sounds silly, but I can't see an inf key.
Typo I meant INS

---

### Post by Elf Wizard on 2007-10-15
> **ago said:**
> What I mean is that windows allows you to compress a full drive, this may create problems if that is the drive used to install wubi.
[COLOR=Navy]Oh! I see.
Well, no it isn't compressed.[/COLOR]

> **ago said:**
>  Typo I meant INS
[COLOR=Navy]Thanks!
Please give me 5min, so I can check it![/COLOR]

---

### Post by Elf Wizard on 2007-10-15
> **ago said:**
> 
Typo I meant INS

[COLOR=Navy][B] Done!
[/B]and [B]gotsa!:)

[/B]Seems it be a (known) bios bug. My bios is 6 yo. and elite has abandoned it. There is no possibility to  boot from my disk more than 1 OS (except from freedos).
That was the reason that I installed KUbuntu on my 2nd drive (but I was forgot it).
Seems like I have to buy a new motherboard (or a new hd controller).
I'm thinking to install wubi at my 2nd drive (changing bios boot settings).

**THANKS** for your help!!!;-)
[/COLOR]

---

### Post by tinybit on 2007-10-15
According to this line:

Reseting the boot drive ... Success.

You are using an early GRUB4DOS. Please try the latest one, and report problems if it still hangs.

---

### Post by Elf Wizard on 2007-10-16
[COLOR=Navy]Hi tinybit!
**THANKS **for helping!;)[/COLOR]
> **tinybit said:**
> According to this line:

Reseting the boot drive ... Success.

You are using an early GRUB4DOS. Please try the latest one, and report problems if it still hangs.
:confused:
[COLOR=Navy]How's that?
I just downloaded wubi and ubuntu text based installer! They're the latest versions!

Where can I find GRUB4DOS latest version?
Is it the latest version (so I can install it): [http://download.gna.org/grub4dos/grub4dos-0.4.3.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3.zip)
[/COLOR][COLOR=Navy]
[B]
Thanks again![/B][/COLOR] ;)
[COLOR=Navy]Giorgos.[/COLOR]

---

### Post by ago on 2007-10-16
Wubi 7.10 should have the latest grub4dos

---

### Post by Elf Wizard on 2007-10-16
> **ago said:**
> Wubi 7.10 should have the latest grub4dos
[COLOR=Navy]Then (since I'm a bit lazy nowadays), I think I would stick with my kubuntu installation for a while and I'll install wubi 7.10, when it will be available for downloading.:D[/COLOR]

---

### Post by tinybit on 2007-10-16
> 
Where can I find GRUB4DOS latest version?
Is it the latest version (so I can install it): [http://download.gna.org/grub4dos/grub4dos-0.4.3.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3.zip)


Yes. Or you may try the coming wubi 7.10.

---

### Post by Elf Wizard on 2007-10-16
> **tinybit said:**
> Yes. Or you may try the coming wubi 7.10.
[COLOR=Navy]I'll give it a try, waiting for wubi's new version.

**THANKS **tinybit!;)
[/COLOR]

---

