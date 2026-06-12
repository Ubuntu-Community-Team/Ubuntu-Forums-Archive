---
title: "Recovering from a grub rescue crash query"
date: 2012-12-02
forum: General Help
---

### Post by felinoel on 2012-12-02
Ok so I found [this](http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash), but I worry that it won't fix my issue maybe?

I dual boot Windows and the second to latest update of Ubuntu, I was just updating to the latest update of Ubuntu when I got this crash.
If I follow these steps, will this fix my issue or is it for a different situation and will not work?

---

### Post by felinoel on 2012-12-03
I think it might not work in my situation because I dual boot.

---

### Post by oldfred on 2012-12-03
Lets see where you are at:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by felinoel on 2012-12-04
> **oldfred said:**
> Lets see where you are at:

       Post the link to the BootInfo report that this creates.

[SIZE="1"]Sorry it took me so long, could NOT get it to connect to the wireless, gave up and am now inches away from wifi box connected with a tiny cord on the ground, lol wow where are my longer cords.[/SIZE]
[SIZE="2"]
Anyways, [http://paste.ubuntu.com/1411627/](http://paste.ubuntu.com/1411627/)[/SIZE]

---

### Post by oldfred on 2012-12-04
The grub in the MBR is looking for the rest of its files in sda4 but your install is in sda3. I would run the Boot-Repair suggested updates.

Is the Windows Vista? It looks like sda2 is main install and sda1 is recovery. Grub2's os-prober usually reversed the descriptions for some reason with Vista. Or Vista is not clear on which is which. Often best to run Grub-Customizer to change descriptions it the reinstall does not sort it out.

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by felinoel on 2012-12-05
> **oldfred said:**
> The grub in the MBR is looking for the rest of its files in sda4 but your install is in sda3. I would run the Boot-Repair suggested updates.

Is the Windows Vista? It looks like sda2 is main install and sda1 is recovery. Grub2's os-prober usually reversed the descriptions for some reason with Vista. Or Vista is not clear on which is which. Often best to run Grub-Customizer to change descriptions it the reinstall does not sort it out.

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)I am at work atm and am not near my laptop, but I *think *it is Win7.
Don't remember, I only ever use it when I need PhotoShop...


So you say to run the Boot-Repair suggested updates and if that doesn't work then run Grub-Customizer to change descriptions?
Will do once I get home, thanks!

---

### Post by felinoel on 2012-12-05
> **felinoel said:**
> I am at work atm and am not near my laptop, but I *think *it is Win7.
Don't remember, I only ever use it when I need PhotoShop...


So you say to run the Boot-Repair suggested updates and if that doesn't work then run Grub-Customizer to change descriptions?
Will do once I get home, thanks! [http://paste.ubuntu.com/1413710/](http://paste.ubuntu.com/1413710/)

[http://paste.ubuntu.com/1413710/](http://paste.ubuntu.com/1413710/)

Ok well I got Ubuntu back on my laptop, except Windows is gone.
Also my Firefox has no URL input spots..?

---

### Post by oldfred on 2012-12-06
Run this:
sudo update-grub

You show a Windows boot/repair in sda1 and an install in sda2. Boot repair usually copies the essential boot files from sda1 to sda2, so you can boot from either. But grub should find them.
How did you resize your Windows partition? 

It also says you have flexnet. Grub used to have issues or correctly flexnet wrote into grub and damaged it. But grub created a work around. You must have some expensive DRM 'ed software installed.

---

### Post by YannBuntu on 2012-12-06
> **oldfred said:**
> Run this:
sudo update-grub

+1

**@OldFred:** in the log sda1 and sda2 appear in os-prober output, but not in update-grub output. That's strange.

---

### Post by felinoel on 2012-12-06
> **oldfred said:**
> Run this:
sudo update-grub```
me@me-Notbook-PC:~$ sudo update-grub
[sudo] password for me: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-34-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-34-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-33-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-33-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda4
done
me@me-Notbook-PC:~$ 
```

> You show a Windows boot/repair in sda1 and an install in sda2. Boot repair usually copies the essential boot files from sda1 to sda2, so you can boot from either. But grub should find them.
How did you resize your Windows partition? 

It also says you have flexnet. Grub used to have issues or correctly flexnet wrote into grub and damaged it. But grub created a work around. You must have some expensive DRM 'ed software installed.I used the partitioner that comes with installing Ubuntu if I recall.

Expensive DRM? I just have the Windows that came with the laptop and PhotoShop, I guess PhotoShop was expensive but I bought it severely outdated so it would be cheap.

---

### Post by oldfred on 2012-12-06
It found a standard boot loader in sda1. Not sure why the one in sda2 says recovery, but I expect it to also boot your install in sda2, unless BCD is not set for correct partition. We cannot see BCD from Linux for boot details.

Photoshop uses flexnet.

---

### Post by felinoel on 2012-12-07
> **oldfred said:**
> It found a standard boot loader in sda1. Not sure why the one in sda2 says recovery, but I expect it to also boot your install in sda2, unless BCD is not set for correct partition. We cannot see BCD from Linux for boot details.Hmm, well if I recall the laptop used up all partitions for Windows, but I deleted the HP Tools partition and put Ubuntu there, so Recovery likely was 2 originally.

> Photoshop uses flexnet.
Damn. So that is the cause?
I need PhotoShop, I claim to be a digital artist.


EDIT:
Ugh, I hate it when it goes to the second page, made me miss your response SEVEN hours ago?!

---

### Post by oldfred on 2012-12-07
I cheat and use Autopager in Firefox. That gives me full scrolling of all the posts. But when lots of pages I still have to jump to end or else scroll takes forever.

---

### Post by felinoel on 2012-12-08
> **oldfred said:**
> I cheat and use Autopager in Firefox. That gives me full scrolling of all the posts. But when lots of pages I still have to jump to end or else scroll takes forever.

Huzzah! Am on Windows again, now to finish a web site.

So Adobe Creative Suites is capable of breaking my computer... is there a way to prevent it from happening again or should I just keep that boot repair disc in my cd drive for future occurrences?

---

### Post by oldfred on 2012-12-08
Grub2 has the work around for flexnet so it should be ok. It may be other Windows tools. Some virus software sees grub as a boot virus and restores Windows, some HP or Dell tools do something like flexnet in writing into the sectors after the MBR where grub has its core.img. Most turn those off if a continuing issue. 
I do not normally suggest neosmart's EasyBCD but a few do use it that are primarily Windows users. I prefer grub.
You also can have grub directly installed to a flash drive and manually add a boot stanza to boot Ubuntu as another way to boot. Then from inside Ubuntu it is easy to reinstall grub to the MBR.

       Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
    
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
I use this type of boot stanza to boot from my USB to my installs as a backup way to boot.

---

### Post by felinoel on 2012-12-10
> **oldfred said:**
> Grub2 has the work around for flexnet so it should be ok. It may be other Windows tools. Some virus software sees grub as a boot virus and restores Windows, some HP or Dell tools do something like flexnet in writing into the sectors after the MBR where grub has its core.img. Most turn those off if a continuing issue. 
I do not normally suggest neosmart's EasyBCD but a few do use it that are primarily Windows users. I prefer grub.
You also can have grub directly installed to a flash drive and manually add a boot stanza to boot Ubuntu as another way to boot. Then from inside Ubuntu it is easy to reinstall grub to the MBR.

       Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
    
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
I use this type of boot stanza to boot from my USB to my installs as a backup way to boot.
Ugh it is probably that super annoying HP Tools, I've been meaning to turn that off...

---

