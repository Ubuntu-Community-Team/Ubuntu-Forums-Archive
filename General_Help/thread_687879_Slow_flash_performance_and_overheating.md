---
title: "Slow flash performance and overheating"
date: 2008-02-04
forum: General Help
---

### Post by Crypty on 2008-02-04
I love using ubuntu and it has completely replaced windows for me but I have one, somewhat major problem with it. In firefox, a simple flash video, such as youtube, or even a small flash ad, sends my processor usage soaring to the 90-100% range. Flash objects, if large enough, will be very, very sluggish, and in many cases, my computer will overheat and shut down as a result. This never happened, and still does not happen when I boot windows and use firefox and view a flash object. Even very large flash videos and games work fine under windows. Non-flash videos don't cause any trouble.
The laptop is a fairly recent HP dv1340 with a 1.86Ghz Pentium M and 1GB of ram. 

Any help is appreciated. Thanks.

---

### Post by Samhain13 on 2008-02-04
I have the same problems with Firefox and Flash too. If I'm not mistaken, the problem is in the plug-in itself, but I'm sorry I can point you to any helpful places.

However, to address this issue, especially with those small Flash banner ads, I just created a new Firefox profile and added *.swf to the Adblock preferences. I use that profile when I just want to go around the Internet, reading news and what-not. I use the default profile, which has everything ON, when I want to visit YouTube, for example.

Although, desipte the high CPU usage, I have yet to experience an overheat. My CPU temperature only increases by 2 Celcius max because of those Flash apps.

Anyway, I'm posting because I'm interested in this matter too.

---

### Post by Estepario on 2008-02-12
Same problem here, 

when i see some youtube video or any thata use flash i have overheating over 70°C and great usage of cpu.

i'm using ubuntu gutsy in a dell inspiron 600m. intel centrino.

another thing is that from teh new version of the flash plugin of teh last week, the problem is worse.

---

### Post by cypresstwist on 2008-02-22
Same thing here. Overheating Dell D820. Reaches 75-80 degrees Celsius when I view flash videos and the fan needs about a half an hour to stop screaming. Using SMP. I need a fix for this and FAST.

---

### Post by G@B0 on 2008-02-25
Same problem on Sony Vaio FZ180E

Overheating to 60 degrees when watching youtube videos.
This is making me crazy.

We need a fix for this and FAST.

---

### Post by Arlanthir on 2008-02-25
Another one here...

---

### Post by StOoZ on 2008-02-25
and another one.
exactly the same problem with Firefox.

---

### Post by Crafty Kisses on 2008-02-25
Post the following output:
```
top
```

---

### Post by wobbiebobbie on 2008-02-25
**This post could be related to an Ubuntu bug filed at**: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				ok guy here how I got the flashplayer to work and no over heating and my youtube works fine 
1st download the adobe flash player and get the .tar file it should go to the desktop unpack the file and a second file should be on you desktop click on the( install flash player 9 linux) a popup window will show up and click on ( run in terminal )

---

### Post by mynameisflorian on 2008-02-28
your pc shouldn't overheat, no matter how hard you push it. If it's overheating you either:

- are over clocking the system (c'mon is the $20 of extra power really worth burning out your CPU?)

- have a cooling problem. Perhaps a fan went out? Another common problem (especially in houses with pets and smokers) is "dusting" -- where the heat sinks and other components get caked with dust. I pulled almost a half-cup of dust out of my computer last time I cleaned it (and performance went way up). Don't clean your computer unless you know what you're doing. If you didn't put it together, then it's probably a good idea to find a nerd and take him (or her!) out for dinner...

- have defective/old hardware



I also have this problem, no matter what version of flash I use. My theory is that flash draws onto the screen dot-by dot, rather than have the video card bitblt it like windows does. The inefficiency of flash compounded with drawing on the screen "the slow way" is what I think causes these symptoms...

- Florian

---

### Post by 3ark on 2008-05-31
Same here, my laptop jumps from about 57-59 degrees well into the high 70 degrees. This is a pretty serious problem.

---

### Post by Ang on 2008-06-09
Same problem here on the laptop and the stationary computer. And since everything on the web is containing something with flash so does it make the windows computers feel like super machines!

---

### Post by ejbest on 2008-06-09
Hello, I am new to this forum and ubuntu (if I should be posting elsewhere, please help me); however, I have been working with Linux for a great while.  The system has installed and I am basically working (at a very slow pace) with everything seeming to function; however, it is very painfully slow.  Opening browsers going through system menus and just about everything is slow slow slow - and I do mean snails crawl slow.

Windows XP was screaming on this PC before crashing and now it is running ubuntu. Since I have seen other posting there hardware listing, I have pasted 'some' of mine.
       description: Motherboard
       product: P4P8T
       vendor: ASUSTek Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1003.001 (09/02/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 478
          size: 3GHz
          capacity: 3400MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 33
          slot: System board or motherboard
          size: 1002MiB
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD1600AAJS-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAP94568614
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ddd5d
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 112e2c6a-1e7b-45c3-af08-b0cf52dbe25f
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-05-25 12:48:40 filesystem=ext3 modified=2008-06-08 11:28:18 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-06-07 23:08:16 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MiB
                   capacity: 2933MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi
          physical id: 1
          bus info: usb@5:7
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: CardReader CF
             vendor: USB2.0
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 0100
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: CardReader MS
             vendor: USB2.0
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
             version: 0100
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: CardReader SD
             vendor: USB2.0
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
             version: 0100
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: CardReader SM XD
             vendor: USB2.0
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
             version: 0100
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde

---

### Post by Arlanthir on 2008-06-09
@ejbest:

Welcome to the Ubuntu Forums ;)

I think you should post it on another thread, this one is only about flash, and you seem to have bigger problems!

---

### Post by Benniee on 2008-06-11
I have the same problem, and it's driving me nuts.

I've got a Dell Inspiron 8500 - Kubuntu 8.04 installed - and the nonfree plugin for firefox. 

After a recent round of updates from the repos the problem seems to be worse - taking the CPU temp to safety shutdown levels, which I've realised when walking back to the computer to see it shut down.

Someone mentioned installing the flash player from Adobe, which I'd like to give a try. Is there a step-by-step for removing the currently installed plugin and installing the player direct from Adobe?

Thanks,
Benniee

---

### Post by Benniee on 2008-06-12
As an update - I fixed my overheating shutdown problem by giving the fan on the Dell a really good clean out. It was only a little blocked with dust, but after a clean it manages to keep the CPU temp stable when running flash stuff.

Firefox still chews up HEAPS of cpu when browsing a page with any kind of flash on it. Would like to know why as my Windows box barely cracks a sweat on the same pages.

Benniee

---

### Post by cooltd825 on 2008-06-26
yeah, my computer doesn't overheat.  But Firefox definitely uses up its share of my processor.  I'm just glad my Gateway case has an amazing cooling system, but it sounds like a freight train when I'm on a flash site.

I'm running an Intel Pentium D 2.8 Ghz, 3 GB of RAM, and an Nvidia 8500 GT.  when I'm on a flash-intensive site, it's using around 70-80% of my processor.  this is insane.  It happens on Firefox 2, Firefox 3 (btw, i hate this browser), and Opera.  this makes me think it's a problem with the Linux Flash plugin.

P.S.  i  have no problems when I'm booted up in Vista  ;)

---

### Post by _Stevie_ on 2008-06-27
count me in. i got a turion on my laptop and the 1st cpu is always maxed out. i'm using opera thought. but this also happens with firefox.
in the case of opera its "operapluginwrap" which causes the cpu hogging. in firefox i didnt check yet.

---

### Post by Jarmungie on 2008-07-07
Same problem here with an Inspiron 6000. Really a pain. I have heard that this could be due to the flash plugin utilizing the processor instead of the GPU to process flash. My laptop is not shutting down but it is very hot to the touch and it gets too hot to sit on my lap which is very annoying. 

Mine also seems to get very hot when I let it sit idle for a while but I think this may be due to open web pages (running flash) during that time.

Does anyone know for sure why this is happening yet?

---

### Post by _Stevie_ on 2008-07-07
this issue is so annyoing. i cannot use my notebook to browse websites anymore.

---

### Post by Derspankster on 2008-07-13
Haven't seen any recent posts on this topic. It's mid July, 2008 now and I'm still having this same heat/flash problem on my Acer 5003 running 8.04. I've cleaned the fan and vents (neither was particularly dirty) and an using a laptop cooler now. 

Any flash content still maxes out my cpu and sends temps soaring. Can't seem to come up with a fix. Any news out there on this issue?

---

### Post by Arlanthir on 2008-07-13
I think it's a driver issue and no one but Adobe people can fix it.

---

