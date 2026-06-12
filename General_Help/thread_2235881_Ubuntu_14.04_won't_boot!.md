---
title: "Ubuntu 14.04 won't boot!"
date: 2014-07-23
forum: General Help
---

### Post by Ricardo_Raimundo on 2014-07-23
[B]....................................................
EDIT: [/B]Check post #16 for the answer.
[B]....................................................
[/B]
Hello.

I have a serious (I think) issue at hands.

Yesterday my Ubuntu 14.04 crashed. Nothing new here. Sometimes this happens.

The problem is I can't boot the machine anymore.
This happened once before and my "fix" was insist on booting on safe mode. It took several tries but it worked.

Now nothing seems to work!
The boot freezes in any of the normal or safe modes. Even the Ubuntu CD won't boot!

What can I do?
I have some work on my HD I can't afford to loose.

Thank you for your help!

Here's a photo of my screen at the moment the boot freezes in safe mode.
[IMG]https://dl.dropboxusercontent.com/u/120382798/Forum/UbuForum/BootFailScreenPhoto01.jpeg[/IMG]

---

### Post by sudodus on 2014-07-23
Some questions might help you get started searching for the problem.

- Please describe your computer, particularly the graphics card.

- Are you running in BIOS or UEFI mode?
- Are you dual booting with Windows?

- What did you run before the crash? Try to describe it, and remember if there was something unusual! Was there are an update?

- How far does the boot reach? Different output to screen from disk and DVD? Try to run memtest from that early menu (grub, syslinux).

Maybe there is problem with the graphics, either software (because of an update/upgrade), but in the worst case a hardware error. The DVD (if it is OK) should work, unless you need a boot option for it.

- Do you remember if you have used some boot option for example nomodeset or acpi off or nolapic?

- Did you use a proprietary driver for graphics or wifi?

---

### Post by Ricardo_Raimundo on 2014-07-23
Hi Sudodus. Thank you for your reply!

Ubuntu 14.04 (no Windows)

ASUS P8B75-M LX motherboard
Intel i5-3330 @ 3.00gHz processor
1 x 8gb DDR3 @ 1333mHz

I believe this can have something to do with the graphics card.
It's a ASUS GeForce GTX 660 ti DirectCU II 2gb ddr5 and I'm using the proprietary drivers. It's the only proprietary drivers on my system.

Every time Ubuntu crashes I'm using Blender but, I'm ***always*** using Blender on this computer. It's my workstation.
There's nothing unusual before the crashes. Everything goes smooth and suddenly.. CRASH!!

> [COLOR=#000000]Are you running in BIOS or UEFI mode?[/COLOR]
I have no idea! How can I check that?

> [COLOR=#000000]How far does the boot reach? Different output to screen from disk and DVD? [/COLOR]
I believe it's always the same.

> [COLOR=#000000]Try to run memtest from that early menu[/COLOR]
It gets nowhere.. only a purple empty screen..

> [COLOR=#000000]Do you remember if you have used some boot option for example nomodeset or acpi off or nolapic?[/COLOR]
hugh! Don't even know what that is! Sorry! 


A side question: Can I install a Windows copy parallel to Ubuntu and use it to get my HD content? If this is possible I can make a backup and format the whole thing and re-install Ubuntu. What do you think?

Thank you for your help man! I appreciate it!

---

### Post by oldfred on 2014-07-23
Windows does not read Linux without some special drivers. You should be able to copy data using Live installer from a flash drive.

If you only have Ubuntu you do not normally get grub menu. IF BIOS you have to hold shift key until menu appears. With UEFI it often is escape key to get menu to appear.

You can then try booting in recovery mode.

You have a new enough system that is will boot in BIOS or UEFI mode. And how you booted installer is how it installed.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Ricardo_Raimundo on 2014-07-23
Hey Oldfred!

Do you think the flash drive installer will do the trick?
Both HD and CD stops booting halfway.

I will try to check what kind of boot I have tomorrow (2AM here..) but it may be difficult because, since Ubuntu is not booting, the grub menu is always there.

If I understood correctly, my problem can be caused by using a GeForce card on a UEFI installation?
And if this is the case, if I convert it to non-UEFI/legacy it will prevent this from happening again?

Thank you for your help Oldfred!

---

### Post by oldfred on 2014-07-23
Every since about 10.10 I have had to use nomodeset with every live installer boot and first boot after install. I have a 9600GT nVidia card.

UEFI or first boot after install:
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Ricardo_Raimundo on 2014-07-24
ok.. here's the news..

I tried removing quiet splash (nomodeset was already there) and the boot stops at:

* starting system V initialisation compatibility

Sometimes (rarely) it stops at:

* starting configure network device



Then I've found that I can turn APCI off, so I changed the line to:

"linux     /boot/vmlinuz-3.13.0-32-generic root=UUID=d27f2f33-4aea-4dcf-9353-00a3c3e5777b ro nomodeset $vt_handoff acpi=off"

This makes the boot stop latter at:

* starting bridge file events into upstart



I can't start Ubuntu from neither the CD nor the USB. They both stops booting.

I even tried to install 13.10 but it stops too!

I don't know what else to do..

I really can't afford to loose my HD content. Please help me!



EDIT: the strangest thing is that the first time I removed the quiet splash thing, Ubuntu did start but, because I thought the problem was solved I reboot it again. I feel so stupid!!

---

### Post by sudodus on 2014-07-24
Maybe there is a problem with the graphics chip/card, maybe with the wifi chip/card, or RAM (memory). Maybe some hardware is failing. Anyway there are several alternatives.

1. Can you work from ***another computer?*** In that case you can connect the hard disk drive to that other computer (use an external casing or a 'USB to IDE & SATA cable' to connect it via USB). Boot that other computer from linux, for example an Ubuntu desktop install DVD or USB drive, and copy the files you need to another drive.

2. You can also run the linux distro ***Knoppix***, which is good at recognizing hardware. If it works, you can use it to copy the files you need to another drive.

3. You can try to run Ubuntu in ***text mode***. Enter the boot option **text** instead of of alongside the other boot options you have tried already. You can do this live from the DVD as well as with the installed system. It is possible to mount an external drive and copy the files you need to another drive also in text mode.

---

### Post by Ricardo_Raimundo on 2014-07-24
Do you know how can I tell it to boot using the onboard graphics card?

I actually have a little netbook with a Ubuntu system in parallel with WIn7 and a external 3.5 HDD.
Maybe I can open it and put my desktop HD into it?

I just hope this won't brake anything!

---

### Post by sudodus on 2014-07-24
If the hardware is OK, not damaged:

If there is an onboard graphics chip, you can unplug the separate graphics card, and boot the computer from CD/DVD/USB (with an Ubuntu desktop installer). If you remove the proprietary driver, you can also boot the installed system.

Try Ubuntu, do not install anything, and the internal drives will be untouched. If you mount a partition on the internal drive, you can read files from it (and if you wish also write files to it).

If the hardware is not working, it can be hard to know if it is damaged, or if the hardware drivers do not work with that particular hardware. This is why it is worthwhile to try different linux distros.

---

### Post by oldfred on 2014-07-24
Some others with different Asus motherboards. May be similar issues?

 ASUS Rampage IV Extreme motherboard
[http://ubuntuforums.org/showthread.php?t=2063073](http://ubuntuforums.org/showthread.php?t=2063073)

 [SOLVED] UEFI Boot Problems Asus P8P67
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

You should have UEFI/BIOS settings on which video mode you use. But Intel chips seem to need boot parameters also:
      
 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

I would not try to much with 13.10 as it now is obsolete.

---

### Post by Ricardo_Raimundo on 2014-07-24
uuuuufff.. 

The important files are already getting into my wife's mini laptop.

Next step: format HD and re install Ubuntu. I will try the Legacy mode this time.. and.. very important: Make backups!!

Thank you both for your help!
I'm truly grateful!

---

### Post by Ricardo_Raimundo on 2014-07-24
oh.. I missed your post Oldfred!

I will take a careful look at those link latter. Now I'm going to work at the call center (freelance 3D work is not paying all the bill at the moment!).

The 13.10 thing was just a desperate try to access my HD to save my files.
I'm so relieved right now!

Thank you!

---

### Post by sudodus on 2014-07-24
I'm glad you are backing up the important files :KS

Good luck with the next steps, and feel welcome to ask if there will be more questions!

Finally, it is very valuable for the community (other linux users at the Ubuntu Forums) that you share your results. Please tell us* not only **that*** you manage to perform the tasks, *but also **how*** you do it :-)

---

### Post by Ricardo_Raimundo on 2014-07-26
weeeeeeellllll..

The important files are backed up but.. I found that my hard drive is corrupted!! Oh god!! The humanity!!

Now I'm going to try to recover the most important stuff (two .blend files) with PhotoRec: [http://www.cgsecurity.org/wiki/PhotoRec]("http://[URL")

I will keep my fingers crossed!

---

### Post by Ricardo_Raimundo on 2014-08-02
So.. it looks like, after all, my problem was all due to my crappy wireless card.
Don't buy smcwpci-g2! It's not even a Ubuntu compatibility thing only. There are reports of crashed systems also for Windows users.

Here's the little bitch!
[IMG]http://www.smc-asia.com/thai/productpic/1222052301.JPG[/IMG]

---

### Post by sudodus on 2014-08-02
Thanks for sharing this information :-)

This shows that bad co-operation with a wifi card can cause errors, that are not easy to understand.

---

### Post by Ricardo_Raimundo on 2014-08-05
> **sudodus said:**
> Thanks for sharing this information :-)
You're welcome Sudodus.. and thank you very much for your help.

---

### Post by sudodus on 2014-08-05
Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Ricardo_Raimundo on 2014-08-05
Done!

---

