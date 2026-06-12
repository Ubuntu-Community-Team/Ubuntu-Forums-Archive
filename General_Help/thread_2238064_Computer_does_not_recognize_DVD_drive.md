---
title: "Computer does not recognize DVD drive"
date: 2014-08-05
forum: General Help
---

### Post by eipapp on 2014-08-05
I have a HP desktop which came with Win 8 installed. I deleted it and loaded Ubuntu 14.04 in it's place. Now, however, when I load a disk into the DVD
drive my computer doesn't recognize it. Even tapping the F11 key for boot options it continues to load Ubuntu. What can I do for my system to see the 
DVD drive?

Thanks,

---

### Post by sudodus on 2014-08-05
At that early stage, the operating system should not be involved. Try some other key than F11 (the other Function keys ...) Some HPs use other than F11 for a boot menu. You might also try to change the boot order in a BIOS/UEFI menu (usually with another Function key).

Are you running the computer in UEFI mode or BIOS mode?

---

### Post by eipapp on 2014-08-05
Open Gparted and this is what it shows: SDA1 - Fat32 - /boot/efi

When running Windows F11 always worked for me and is even labeled as such on the key itself but will try other F' keys to see what happens. 

Thanks for your reply...........

---

### Post by MartyBuntu on 2014-08-05
Did you disable UEFI in the BIOS prior to installing Ubuntu?

Is it just one particular disk that won't boot? Have you tried others?

---

### Post by sudodus on 2014-08-05
You can also boot into Ubuntu and run these commands and see if you find the DVD drive (at that late stage). If the drive works properly, you should get some output.

```
sudo lsblk
```

One line should contain **sr0** or similar and **rom** and a boot CD should also be mounted, for example at **/media/Ubuntu 12.04 amd64**

You can also try these commands

```
dvd+rw-mediainfo /dev/sr0
```
which prints a line simlar to (but depending on the drive's model number)
```
INQUIRY:                [HL-DT-ST][DVD+-RW GSA-H21L][W516]
```
and some information about the inserted DVD (if found).

or

```
cdde -b
```
Prints the line (if a data CD or data DVD is inserted).
```
A data cd was inserted.
```

If the drive works, it should also be possible to boot from it.

Is it possible that there is something wrong with the DVD disk? How did you make it? Have you got another DCD install disk, that you can test?

---

### Post by eipapp on 2014-08-05
When I load a DVD into the drive while running Ubuntu a box comes up showing the contents of the DVD and all it's files. I know the DVD is good as I've used it to load a OS on my laptop. 
Is there a way to change the boot order on my machine so that it looks for the DVD drive first and finding nothing continues to boot from the hard drive?
If so, how do I do that?
I knew how to change the boot order in Windows but not Ubuntu.

---

### Post by sudodus on 2014-08-06
You must tell us more about your particular model of HP. Otherwise we can only guess. Please specify your computer

- HP *model* including link to a specification, if you can find one. 
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

At least in older versions, the boot order is set before starting any operating system, so before starting Windows. It may have changed in your computer. But typically HP computers will be set to boot from CD/DVD by default.  Otherwise change the boot order in the UEFI/BIOS menu to try booting  from CD/DVD first. Since you have deleted Windows, I think it would be easier to boot the computer in BIOS (alias CSM) mode instead of UEFI, if that is possible.

I have an HP server, my son has an HP laptop and my brother has an HP laptop and an HP desktop. Those are not brand new, but I have been able to install linux in them. If you have problems with the DVD drive, you can try booting from USB. See this link (and links from it)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by eipapp on 2014-08-06
I purchased this model in February of this year. It would not boot into CD/DVD until I went in and change it under Windows. This allowed me to then run live versions of Linux.
When installing Ubuntu I loaded it from a DVD I burned and had sampled on this machine. Now that I have Ubuntu Linux up and running I thought it would be just as
easy to sample other Linux distrubutions but as I stated in my initial post I can't seem to make that happen. 
The only thing I can tell you is that it is a HP Pavilion 23 all-in-one desktop Model 23-b010 with 6Gb of ram with 500Gb HD.
If that helps...........

---

### Post by sudodus on 2014-08-06
Try to press the Escape key in UEFI to boot linux. To boot in BIOS (legacy) mode, disable secure boot and UEFI. Then you can change boot order.

It seems to be the solution according to the following link, described by an HP employee (two posts).

[http://h30434.www3.hp.com/t5/Other-Desktop-PC-Questions/HP-Pavilion-23-b010-Can-t-Change-Boot-Order/td-p/2276909](http://h30434.www3.hp.com/t5/Other-Desktop-PC-Questions/HP-Pavilion-23-b010-Can-t-Change-Boot-Order/td-p/2276909)

---

### Post by eipapp on 2014-08-07
sudodus,

Tapping the ESC key solved the problem, thank you so much.
Am currently running live version of Gnome 3.12 while I write this.
Appreciate your help !!
Thanks again,
Bruce

---

### Post by sudodus on 2014-08-08
Congratulations :KS

Please help other users at the Ubuntu Forums by marking this thread as SOLVED. Click on **Thread Tools** at the top of the page ...

---

