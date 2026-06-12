---
title: "Some weird problem I am having."
date: 2008-05-30
forum: General Help
---

### Post by TommyIndep on 2008-05-30
Hello everybody, I've been postponing this post as I was hoping I could fix this myself, turns out that's not an option though. This might sound a bit stupid, but I don't really know what the problem is, but I'll try my best to describe it.

Let's say I am editing a picture in GIMP, then when I press "File" --> "Save As", the whole program freezes, the same happens when downloading pictures from Firefox, *Right Click* --> "Save As", then Firefox freezes. 
When I try uploading photos on Photobucket or wherever and I click "Upload from computer" Firefox freezes for about 30 secs.
I've also noticed that when I right click on things, e.g. the panels, and click "Properties", it takes about two minutes for the menu to show up.
And the most annoying things out of all, whenever I try to open Emerald Theme Manager it can take up to 15 minutes from when I click open 'til I see the actual window!

Does anybody have a clue about what's wrong?
If it's to any help, I am using Ubuntu 8.04.

Thanks in advance for all help. :)

---

### Post by wpshooter on 2008-05-30
Please describe the specs. of your machine for us.

Thanks.

---

### Post by el_baby on 2008-05-30
Does it happen in other programs also?

Try launching openoffice and chose **File** -> **open**

Is it a fresh install? Or did you upgrade from Gutsy?

I think I have *[thread=811795]the same problem[/thread]* (but got no solution yet)... I think it started after I upgraded, but I ain't sure...

---

### Post by TommyIndep on 2008-05-30
I am using a Acer TravelMate 5520 with a AMD Athlon 64 X2 Dual-Core Processor, 1GB of RAM and 120GB HDD. My Graphics card is a ATI Radeon Xpress 1250. Was that helpful?

---

### Post by TommyIndep on 2008-05-30
> **el_baby said:**
> Does it happen in other programs also?

Try launching openoffice and chose **File** -> **open**

Is it a fresh install? Or did you upgrade from Gutsy?

I think I have *[thread=811795]the same problem[/thread]* (but got no solution yet)... I think it started after I upgraded, but I ain't sure...

I just tried what you said and it seems like it's the same problem! This all started a while after I upgraded from Gutsy!

---

### Post by WRDN on 2008-05-30
Try turning off all visual effects and seeing if it makes a difference- i've heard ATI graphics cards have caused problems in the past, so I would start here.
If that doesn't help, it may be worth reinstalling the video drivers.

---

### Post by TommyIndep on 2008-05-30
I tried turning off all visual effects, but with no success, Open Office and firefox still froze. I might try re-installing the video drivers, though the process is a pain in the a**, haha.

---

### Post by WRDN on 2008-05-30
> **TommyIndep said:**
> I tried turning off all visual effects, but with no success, Open Office and firefox still froze. I might try re-installing the video drivers, though the process is a pain in the a**, haha.

Could you post a screenshot of your System Monitor Processes please, sorted by memory (highest first).

---

### Post by TommyIndep on 2008-05-30
Here they are, sorry, my language is Norwegian so where it says "Sover" it means "Sleeping" while "Kjører" means "Running".

---

### Post by WRDN on 2008-05-30
Thanks for posting the screenshots.
For starters, revert back to the original theme. Even if you turn off visual effects, emerald is implementing some with the Windows theme. The default one is "Human".
This should remove the emerald process.
Then, end the process "compiz.real". Though you have compiz-fusion turned off, that process still appears. Ive read to stop it completely, you will have to uninstall and reinstall compiz-fusion.

Final question, are you upgrading from Gutsy or is it a clean install of Hardy?

---

### Post by TommyIndep on 2008-05-30
I'll give it a go, does this mean I can't use Visual Effects?
And to answer your question, I upgraded from Gutsy when Hardy came out, so it's an upgraded version!

EDIT: I removed all of the processes you told me to, and it didn't have any effect, it's still as slow!

---

### Post by WRDN on 2008-05-30
> **TommyIndep said:**
> I'll give it a go, does this mean I can't use Visual Effects?
And to answer your question, I upgraded from Gutsy when Hardy came out, so it's an upgraded version!

EDIT: I removed all of the processes you told me to, and it didn't have any effect, it's still as slow!

Hmmmmm, it may be worth checking what errors are appearing.
To do this, click System > Administration > System log and filter out the word error (View > Filter).
You could also try reinstalling the kernel image. To find what version you are running, type the following in the terminal:

```
uname -a
```

Then, type 

```
sudo apt-get install --reinstall linux-image-2.6.24-17-generic
```

*Note: Your image name may be different. As mentioned, use the "uname -a" command to find which you are using*

---

### Post by TommyIndep on 2008-05-30
Amazingly, re-installing the kernel image didn't have any effect. 
The System Log showed quite many errors though, should I add a screenshot?

---

### Post by WRDN on 2008-05-30
> **TommyIndep said:**
> Amazingly, re-installing the kernel image didn't have any effect. 
The System Log showed quite many errors though, should I add a screenshot?

No suprise the image reinstall didnt affect anything. I didnt really expect it to but it was worth a try.
Anyway, regarding the log, could you post the errors here. Just select them all and copy them.

---

### Post by TommyIndep on 2008-05-30
I see. OK I copied all of the errors that came up, this is the result:

May 26 12:46:48 thomas-laptop syslogd 1.5.0#1ubuntu1: restart.
May 26 13:06:52 thomas-laptop kernel: [ 1507.126078] ip6_tables: (C) 2000-2006 Netfilter Core Team
May 26 13:06:54 thomas-laptop exiting on signal 15
May 26 13:58:59 thomas-laptop syslogd 1.5.0#1ubuntu1: restart.
May 26 13:59:00 thomas-laptop kernel: Inspecting /boot/System.map-2.6.24-17-generic
May 26 13:59:00 thomas-laptop kernel: Loaded 28488 symbols from /boot/System.map-2.6.24-17-generic.
May 26 13:59:00 thomas-laptop kernel: Symbols match kernel version 2.6.24.
May 26 13:59:00 thomas-laptop kernel: Loaded 27720 symbols from 112 modules.
May 26 13:59:00 thomas-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
May 26 13:59:00 thomas-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
May 26 13:59:00 thomas-laptop kernel: [    0.000000] Linux version 2.6.24-17-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 13:57:17 UTC 2008 (Ubuntu 2.6.24-17.31-generic)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] Command line: root=UUID=2d969e86-925e-41f6-993c-b5175f314bf7 ro quiet splash
May 26 13:59:00 thomas-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe80000 (usable)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe80000 - 000000002fe93000 (ACPI data)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe93000 - 000000002fe95000 (ACPI NVS)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe95000 - 0000000040000000 (reserved)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 26 13:59:00 thomas-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] end_pfn_map = 1048576
May 26 13:59:00 thomas-laptop kernel: [    0.000000] DMI present.
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F83E0 checksum 0
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: RSDP 000F83E0, 0024 (r2 PTLTD )
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: XSDT 2FE88D12, 005C (r1 ACRSYS ACRPRDCT  6040000 INNA        0)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: FACP 2FE92A33, 00F4 (r3 ATI    Herring   6040000 ATI     F4240)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: DSDT 2FE88D6E, 9CC5 (r1    ATI    SB600  6040000 MSFT  100000E)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: FACS 2FE94FC0, 0040
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: SLIC 2FE92B9B, 0176 (r1 ACRSYS ACRPRDCT  6040000 ANNI        1)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: SSDT 2FE92D11, 01C4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: ASF! 2FE92ED5, 0063 (r32    DMA AMDTBL    6040000 PTL         1)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: APIC 2FE92F38, 0054 (r1 PTLTD  ^I APIC    6040000  LTP        0)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: MCFG 2FE92F8C, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: HPET 2FE92FC8, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
May 26 13:59:00 thomas-laptop kernel: [    0.000000] ACPI: DMI detected: Acer


A lot of files not found...
I noticed that it doesn't say error anywhere here, but it does in the system log!

---

### Post by TommyIndep on 2008-05-30
I'm guessing by to the small amount of replies, no one but me has been unfortunate enough to experience this? Ah well. Maybe it'll be fixed in 8.10.

---

### Post by TommyIndep on 2008-05-31
Ok I'm giving this thread its last bump, if no one replies I'll just wait for 8.10.

Thanks everybody who tried to help! :)

---

