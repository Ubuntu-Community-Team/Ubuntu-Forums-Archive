---
title: "Iso image directly on laptop harddrive."
date: 2013-03-16
forum: General Help
---

### Post by LawaBoy on 2013-03-16
Greetings,

Anyone knows if its possible for me to just copy everything from a Ubuntu ISO image to a laptop harddrive so that he computer will start up the harddrive with the so called "cd"? The laptop I have is locked down by the damned TPM chip and it seems I cant get into BIOS as long as the TPM chip is active. Have no clue if I can just take out the chip but I will continue to search :D

---

### Post by TheFu on 2013-03-16
If you cannot control the boot media used, then I don't see how you can alter which OS gets booted.
However, you might be able to load VirtualBox and boot a virtual machine as a liveCD from the ISO.  This does require a "more capable laptop", so anything with a Core2Duo CPU or better AND 2G of RAM should be able to get acceptable performance for an Ubuntu virtual machine - provided you do not run Unity.

---

### Post by sudodus on 2013-03-16
I don't understand. Please describe with more details to make it easier to help.

- How the computer works now (how it can boot, and how it cannot boot)
- What you want to do and why

---

### Post by LawaBoy on 2013-03-16
Well what I am trying to do really is install an OS to it, so I though Ubuntu might work since I got it on another laptop.

The laptop is a HP ProBook 4330s which seems to been owned by a school before the client of mine bought it from the school, but after he somehow managed to remove or delete the previous OS on it he now cannot boot it since the BIOS is locked and cannot be unlocked because of the TPM chip. And if I can get a OS to run I can reset the TPM with some software I belive from what I have read on other websites.

Now the only bootable devices I am able to selct from are the Harddrive and Ethernet.

Since I can connect the harddrive to a docking station I can copy everything over. So thats why I wonder if I can just copy everything over from the ubuntu cd / ISO?

---

### Post by sandyd on 2013-03-16
You need to contact HP, and follow the instructions below
[http://breakstuffmajorly.blogspot.ca/2012/04/remove-bios-password-on-probook-6560b.html](http://breakstuffmajorly.blogspot.ca/2012/04/remove-bios-password-on-probook-6560b.html)

---

### Post by squire on 2013-03-16
You could dock the drive in other puter install Ubuntu on it and put it back in to the problem laptop when done (could be done in a VM*aswell)

---

### Post by sudodus on 2013-03-17
> **LawaBoy said:**
> Well what I am trying to do really is install an OS to it, so I though Ubuntu might work since I got it on another laptop.

The laptop is a HP ProBook 4330s which seems to been owned by a school before the client of mine bought it from the school, but after he somehow managed to remove or delete the previous OS on it he now cannot boot it since the BIOS is locked and cannot be unlocked because of the TPM chip. And if I can get a OS to run I can reset the TPM with some software I belive from what I have read on other websites.

Now the only bootable devices I am able to selct from are the Harddrive and Ethernet.

Since I can connect the harddrive to a docking station I can copy everything over. So thats why I wonder if I can just copy everything over from the ubuntu cd / ISO?

> **sandyd said:**
> You need to contact HP, and follow the instructions below
[http://breakstuffmajorly.blogspot.ca/2012/04/remove-bios-password-on-probook-6560b.html](http://breakstuffmajorly.blogspot.ca/2012/04/remove-bios-password-on-probook-6560b.html)
+1
If that helpful guy is answering when you call , the problem will be solved.
--
A friend of mine had a similar story with a Toshiba laptop. It was never solved, so that computer turned into spare parts. (It was too expensive to get it unlocked/repaired, and nothing useful was found on the internet).
--
If the computer will boot from an internal drive in general, you will solve the problem with Ubuntu desktop, because it is portable if you don't install any proprietary drivers. So you can connect the HDD to another computer via eSATA, USB or open up a desktop computer and connect directly via SATA. Then install Ubuntu to that HDD as if it were a normal internal drive. Be sure to install grub to the head of that HDD and not to any other drive and not to any partition. And you can test it after installation, that it runs on that other computer (but do *not* accept any offer to install a proprietary graphics driver).
[COLOR=#808080]
But I'm afraid that the TPM chip might be smart enough to feel that the OS has changed and deny access.[/COLOR]

---

### Post by varunendra on 2013-03-17
> **LawaBoy said:**
> ...if I can get a OS to run I can reset the TPM with some software I belive from what I have read on other websites.

Now the only bootable devices I am able to selct from are the Harddrive and Ethernet.

FWIW, Slax live cd can work as a PXE server, so you can run it in that mode (just select the 'PXE' option in the boot menu) on another computer, connect it to the laptop using a cross cable and boot the laptop from ethernet. Within a couple of minutes you should have Slax GUI running on it. Try whatever you wish to from there.

---

### Post by LawaBoy on 2013-03-17
Greetings all :D

I downloaded Ubuntu and installed it directly on the laptops harddrive via my other computer using the windows installer for it, placed it back into the laptop and tada it works. Now to get TPM-tools to work :D thanks for all help so far :D loves and kisses for all who wants.. :P

---

### Post by sudodus on 2013-03-18
> **LawaBoy said:**
> Greetings all :D

I downloaded Ubuntu and installed it directly on the laptops harddrive via my other computer using the windows installer for it, placed it back into the laptop and tada it works. Now to get TPM-tools to work :D thanks for all help so far :D loves and kisses for all who wants.. :P

Congratulations :KS

What you mean by windows installer? Did you clone the iso to the HDD? Or did you make a normal installation of Ubuntu?

---

### Post by TheFu on 2013-03-18
> **sudodus said:**
> Congratulations :KS

What you mean by windows installer? Did you clone the iso to the HDD? Or did you make a normal installation of Ubuntu?

Sounds like a WUBI install to me.  

Note to OP - whenever you ask for help here, please, please, please always say "wubi install" in the question unless you are positive it is NOT a WUBI install.  Many solutions around backups, partitions and booting are different for wubi.  Bad advice is likely if "wubi" is not declared.

---

### Post by sudodus on 2013-03-18
> **TheFu said:**
> Sounds like a WUBI install to me.  

Note to OP - whenever you ask for help here, please, please, please always say "wubi install" in the question unless you are positive it is NOT a WUBI install.  Many solutions around backups, partitions and booting are different for wubi.  Bad advice is likely if "wubi" is not declared.
Some evidence indicates wubi, but some does not.
> ..., but after he  somehow managed to remove or delete the previous OS on it he now cannot  boot it since the BIOS is locked and cannot be unlocked because of the  TPM chip. So maybe the OP reinstalled Windows and made a wubi install from that ... but Windows wouldn't work on a different computer, would it? Maybe Ubuntu in wubi does not need a working windows to boot, but ...

I would install Ubuntu directly to that HDD.

---

### Post by LawaBoy on 2013-03-18
Hey again, what I did was take the laptop HDD, insert it into a dockingstaion connected to my stationary computer, started the universal usb installer and installed a so called cd/dv/usb launcher from the hdd itself. So ubuntu isnt really installed its just a so called run from CD/DVD/USB verison of it. Re plugged the Laptop HDD into the Laptop and hey it works.

Allso when I try out these TPM commands I get the same message on everything I try.

 - Tspi_Context_Connect failed: 0x00003011 | layer=tsp, code=0011 (17), Communication failure.

Now how to fix this.. well good question, need to do some more searching  :D

---

### Post by sudodus on 2013-03-18
As I wrote in post #7: ... you will  solve the problem with Ubuntu desktop, because [COLOR=#008000]it is portable if you  don't install any proprietary drivers[/COLOR]. So you can connect the HDD to  another computer via eSATA, USB or open up a desktop computer and  connect directly via SATA. Then install Ubuntu to that HDD as if it were  a normal internal drive. Be sure to install grub to the head of that  HDD and not to any other drive and not to any partition. And you can  test it after installation, that it runs on that other computer (but do *not* accept any offer to install a proprietary graphics driver).

You can actually ***[COLOR=#008000]install[/COLOR]*** a full Ubuntu when the drive is connected to the other computer (sitting in the docking station). It is portable, so it will work also after moving it behind the TPM chip. This is an important advantage with free software: it is not locked to the hardware where you install it. You need not make 'only an Ubuntu boot drive' but a full installation, and you can move it to another computer :KS
--
I don't know anything about the TPM commands.

---

### Post by sudodus on 2013-03-18
You have a good tutorial by *C.S.Cameron* how to install a full Ubuntu system to USB here

[[COLOR=#006400]http://ubuntuforums.org/showthread.php?t=2118207&p=12521458#post12521458[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2118207&p=12521458#post12521458")

and once you have moved the drive into it's permanent place, you can install any program package into it, including proprietary drivers for graphics and or wifi :-)[COLOR=#006400]
[/COLOR]

---

### Post by LawaBoy on 2013-03-20
Hey again,

Thanks for all the help here sudodus, it looks like I'll make it work somehow :D

Hugs for all who wants :D

---

### Post by sudodus on 2013-03-20
Good luck :-)

---

