---
title: "Failed to allocate memory resource?"
date: 2007-04-22
forum: General Help
---

### Post by talcite on 2007-04-22
Hi guys,

I just recently upgraded to feisty and after the grub selection , a brief error flashes on the screen. 
It goes something like this:

Failed to allocate memory resource (hex code)

The computer continues to boot normally, but I'm wondering if there is a larger underlying problem that I should address.

Thanks,
Talcite

---

### Post by Ocxic on 2007-04-22
I got a simmilar error concerning my video card, ATI 9200 SE  could never figure out y, seemed to work fine,  I;ve never found out why it does that

---

### Post by Cable on 2007-04-22
I get the same thing on my Xubuntu box, and it's never had problems.  It's run 6.06, 6.10, and now 7.04 and has had the error every version, but never any problems.

---

### Post by talcite on 2007-04-23
bump? A lot of problems but no solutions =/

---

### Post by eternalwolfman on 2007-04-29
im having this problem as well! it says failed to allocate memory resource #6. everything seems to work fine, except ive been having alot of problems getting games to run such as ut, games that typically should run fine under cedega or wine. also, i tried a couple other distros and had the same issue. it must be a hardware incompatibility issue, maybe related to video cards?

-greg.

---

### Post by silkstone on 2007-04-29
There are many posts about this - PCI: Failed to allocate mem resource #6 etc. A lot of people have the same error message on startup, especially on dual-core laptops. I've not seen an explanation or a solution, unfortunately.

---

### Post by eternalwolfman on 2007-04-29
do you think it is is what is causing certain applications, such as cedega to not work properly?

-greg

---

### Post by silkstone on 2007-04-29
Can't say for sure - I'm not running cedega and everything I have installed so far seems to be OK, but I'm not running anything that uses 3-D graphics.

---

### Post by eternalwolfman on 2007-04-29
hm. ill try poking over in a wine forum. wine seems to be able to emulate so many great programs very well, yet i have had no such luck. thanks for your help thus far!

-greg

---

### Post by Ocxic on 2007-04-29
i could never get my ATI 9200 SE workign with 3D in cedega, even with the fglrx drivers, both from the repos and the propertary one

---

### Post by eternalwolfman on 2007-04-30
ive heard of much more problems with ati than with nvidia though. i believe there are drivers/patches for cedega now to fix the ati issue. did you have any problems running 3d applications under wine?

-greg.

---

### Post by xmux on 2007-05-09
I have the same problem with Failed to Allocate Memory but i have no idea how to solve it!!

---

### Post by 4KvRMU7Nnv on 2007-05-12
here is something interesting...I had this problem with dapper but not with Edgy, then with feisty, I have it again.

---

### Post by MikeDK on 2007-05-15
cant understand this, have the same problem with a HP Pavilion dv9232eu |fujitsu HD 120gb| h&#361;gi 1024 mb DDR2 SDram| Geforce 7600 GO 256 mb | AMD Turion 64 X2 TL-52 1.6ghz|

Kind Regards MikeDK

have installed feisty, but simply cant get to Login Prompt to login, it wont start up.

gave around 1333 Dollars for the laptop just bought it on the 14th. thats the price for the laptop, here in Denmark

---

### Post by snitramc on 2007-05-15
This ever get resolved? I just bought an HP dv2315nr AMD athlon 64 and  want to put feisty on it in dual boot. But I am afraid to open the box and try this until I have a decent level of confidence. I can install on old Dells, why not newer laptops. I returned my Everex since nothing installs with the 8139 NIC. Hopefully I'll have better luck here? Appreciate any  feedback, even from this older thread.

---

### Post by MikeDK on 2007-05-15
well lets see, maybe it gets resolved, in the future some where :-P i meen its a problem there's been around for long time, so why not get it solved, it might not be that easy for devs to get it solved, you follow me??

Kind Regards MikeDK

---

### Post by MikeDK on 2007-05-15
BTW got my problem fixed with the logind prompt, some firmware was still in from HP. used the fwcutter from repo running feisty now on the lap.

MikeDK

---

### Post by snitramc on 2007-05-15
I guess my question was about how the install on the HP Pavilion went. Was it pretty clean? Was there any hardware incompatibilities you experienced that I need to anticipate before installing this? I know its a different machine, so you can't predict precisely, but I am looking for a random sampling of experience with HP Pavilions.
Thanks!

---

### Post by MikeDK on 2007-05-15
yes, installed 7.04 but could'nt get to login screen, so i bootet the recovery kernel, and went thru xorg.conf, installed nvidia-glx and configured xorg.conf and bootet up in normal-mode. but it took me nearly a whole night, just to search the net and the forum here to figure out what was wrong.
it seems like when you have installed ubuntu, some firmware are still left on Harddisk, probably some HP firmware, so i got a hint from our Danish irc channel called #ubuntu-dk under freenode, that i had to use the fwcutter to extract the firmware from Harddrive, an so i did.
Now the sytem only pops upwith the small message with the "failed to allocate mem recources" on bootup but that's another story. as i see it its a kernelbug or something like that.

kind Regards MikeDK

---

### Post by WryNot on 2007-10-15
Hi All,

Yeah, I get this error too -- but it's worse for me.  I'm trying to install Feisty on my new dual core thinkpad and during the install it displays the "failed to allocate memory resource" but then stops installing and says:  "/bin/sh: can't access tty; job control off
(initramfs)"

Any thoughts?  Hints?  

Thanks

---

### Post by d4rkkn16ht on 2007-10-17
I have the same problem.
**PCI : Failed to allocate mem resource** error message on the very beginning of boot process right after GRUB boot menu.
But Ubuntu running well on my system.

My System is :
[B]Acer Aspire 5585
Core 2 Duo T7200
RAM 1 GB[/B]

Is it a bug?
If it is,why no other problem seems to occur?

---

### Post by MikeDK on 2007-10-26
Hi! WryNot, try installing the new version of ubuntu called gutsy, 7.10

---

### Post by boojah on 2007-11-22
same, compal IFL90+

---

### Post by outkasted on 2007-12-06
yeah i've been running gutsy on my HP Dv6315ea laptop and though gives the same memory resource error but the OS and even the Nvidia card run flawlessly....

though would like to know why that error message creeps in....
i think it is due to some PCI slot on the motherboard

---

### Post by mistman123 on 2008-01-09
Isn't there a way to at least "quiet" the memory allocation error message? I just don't like to see it! Everything else works fine.

[HP Pavilion dv6500t]+[Intel Core2Duo]+[2GB RAM]+[Dual Boot: gfxgrub]+[Vista]+[Gutsy]+[nVidia GeForce 8400M GS]

---

### Post by Redrazor39 on 2008-02-21
I also get this stupid message. I would like to get rid of it. I also see a flash of green lines just before it says "ubuntu" and the loading starts. IT'S SO ANNOYING!!! When I start Vista from GRUB then it just says Starting up... and Vista boots perfectly! I hate this so much! It's little things like this that may make me give up ubuntu and maybe linux completely!!! HELP ME!!! I LOVE LINUX!!! UBUNTU FTW!!! HELP!!!

I have:
Vaio VGN-SZ430N
Intel Core 2 Duo Centrino Duo Processor @ 2.00 GHZ
Nvidia Geforce Go 7400
2GB DDR2 RAM


How do I fix this?

---

