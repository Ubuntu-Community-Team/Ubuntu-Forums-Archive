---
title: "Updating bios on HP Compaq dc5800 desktop running Ubuntu 12.04 lts"
date: 2015-02-14
forum: General Help
---

### Post by michael-piziak on 2015-02-14
Using Ubuntu 12.04 LTS.

My hp-compaq computer is 100% Ubuntu.  I want to update the bios.  I'm hoping I can do this without MS Windows, as I don't have Windows installed.

I have downloaded 3 folders from HP that relate to my bios update.

Is there a way to update the bios by hitting a key on boot up before Ubuntu takes over.  I see one option is to "flash the Rom," is that the same as flashing/updating the bios ?

Also, I am not sure which file to select if I can get to a point to update the bios.  What does the file look like or which extension doe it end with ?

I've attached 4 images.  One of my bios in terminal, and the other 3 images are folders I extracted from the HP website concerning bios and my computer.

---

### Post by gifford on 2015-02-14
What is the HP computer? 
As I recall when flashing mine, there is an msdos file you can use on start up. I burned it to disc and then restarted the computer and flashed the new bios.
Give a little more information and maybe Google can help us.

---

### Post by michael-piziak on 2015-02-14
Thanks for your reply.

This is computer is the HP-Compaq-dc5800-Small-Form-Factor.

I have blank CD's I can use, and I also have usb thumb drives.

Additional question:  If one is running a 64 bit version of Ubuntu, shouldn't they seek out a 64 bit bios (like a Windows 7 64 bit bios) - or does that not matter.

---

### Post by michael-piziak on 2015-02-14
Update:  I'm not sure a bios update would solve my problem.
I have 4 gigs ram installed and it appears the bios sees 8 gigs ram.
My "System Testing" fails the memory test because of this.

This may be because I'm running 12.04 lts as explained here: [http://askubuntu.com/questions/338614/ubuntu-12-04-32bit-system-fails-memory-testing](http://askubuntu.com/questions/338614/ubuntu-12-04-32bit-system-fails-memory-testing)

 [COLOR=#000000]michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo /usr/share/checkbox/scripts/memory_compare[/COLOR]
[COLOR=#000000][sudo] password for michael: [/COLOR]
[COLOR=#000000]Meminfo total: 3965516 kB[/COLOR]
[COLOR=#000000]DMI total: 8192000 kB[/COLOR]
[COLOR=#000000]Accuracy: 48.00[/COLOR]
[COLOR=#000000]Memory totals not close enough[/COLOR]
[COLOR=#000000]michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

If someone thinks doing a bios update would correct this situation, please do tell.


[/COLOR]

---

### Post by grahammechanical on 2015-02-14
> [COLOR=#000000]I have 4 gigs ram installed and it appears the bios sees 8 gigs ram.[/COLOR]

How do you know that to be the case? Have you accessed the BIOS setup utility to see what it says the memory total is? What do you see if you run

```
sudo dmidecode -t 17
```

That will show what RAM modules are in what memory banks and the size of the memory/RAM modules. As the askubuntu answer indicated if there are integrated devices that share memory then the test that is running in Ubuntu 12.04 could be producing an inaccurate measurement. You BIOS may know accurately the amount of memory it has. It is the test that is faulty.

Regards.

---

### Post by michael-piziak on 2015-02-14
> **grahammechanical said:**
> How do you know that to be the case? Have you accessed the BIOS setup utility to see what it says the memory total is? What do you see if you run

```
sudo dmidecode -t 17
```

That will show what RAM modules are in what memory banks and the size of the memory/RAM modules. As the askubuntu answer indicated if there are integrated devices that share memory then the test that is running in Ubuntu 12.04 could be producing an inaccurate measurement. You BIOS may know accurately the amount of memory it has. It is the test that is faulty.

Regards.

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo dmidecode -t 17
[sudo] password for michael: 
# dmidecode 2.11
SMBIOS 2.5 present.


Handle 0x0034, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 1
    Locator: XMM1
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz
    Manufacturer: JEDEC ID:7F BA 00 00 00 00 00 00
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number:  


Handle 0x0035, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 1
    Locator: XMM2
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz
    Manufacturer: JEDEC ID:AD 00 00 00 00 00 00 00
    Serial Number: B6E13062
    Asset Tag: Not Specified
    Part Number: HYMP112U64CP8-S6


Handle 0x0036, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 2
    Locator: XMM3
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz
    Manufacturer: JEDEC ID:7F BA 00 00 00 00 00 00
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number:  


Handle 0x0037, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 2
    Locator: XMM4
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz
    Manufacturer: JEDEC ID:7F 7F 7F 7F 7F 51 00 00
    Serial Number: 20620515
    Asset Tag: Not Specified
    Part Number: 64T128020EU2.5B2


Handle 0x0039, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0033
    Error Information Handle: Not Provided
    Total Width: 2 bits
    Data Width: 2 bits
    Size: 4096 kB
    Form Factor: Chip
    Set: None
    Locator: SYSTEM ROM
    Bank Locator: Not Specified
    Type: Flash
    Type Detail: Non-Volatile
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified


michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$


If it's the test that's faulty or a bug in 12.04 lts as indicated from the link, then I am not as concerned about it.  If a bios update could solve the bug, then I'd do a bios update - but I doubt it would.

Please comment.

---

### Post by michael-piziak on 2015-02-15
Update:

I downloaded Ubuntu 14.04 LTS and made a bootable USB flash drive and booted into 14.04 LTS.
I ran the "System Testing" application that 14.04 uses, selecting memory, and my memory passed it's test twice.

So my conclusion is System Testing in Ubuntu 12.04 lts does not work correctly concerning memory, and the bios is **not** the problem.

It would be nice if this bug were fixed, as 12.04 LTS is still supported.

Thanks so much for your replies and time.  I choose to use 12.04 LTS for a few reasons.

---

