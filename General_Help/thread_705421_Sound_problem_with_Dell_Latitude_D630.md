---
title: "Sound problem with Dell Latitude D630"
date: 2008-02-23
forum: General Help
---

### Post by ajeetraj on 2008-02-23
Hello everyone, 

I have been having this problem for quite some time now. If I start my computer with the headphones connected, and if I take my headphones off later then my laptop speakers don't work...Then the only way I can make them work is after restarting without the headphones plugged. After that, if i connect the headphones back, the headphones don't work and only my pc speakers work. it doesn't even mute after plugging the headphones. I have looked around the forum a lot but I haven't found any solution. I have also tried all sort of things in the volume control and i have checked all the given options but nothing seems to help me here. 

Did someone have the same problem? if you had then how did you fix it? please share some wisdom here :)

my lspci output is the following: 
```
deepu@karma:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

Hope to get some quick help! 

Thanks in advance!

ps: if you wanna know anything else about the specs of my comp then please let me know!

---

### Post by northern lights on 2008-02-23
The following HowTo should solve your problem: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by ajeetraj on 2008-02-25
Hey man, I am sorry to say that the link actually didn't help me at all. After following the link, after the restart, I lost everything. I have absolutely no sound at all on my system. well, I have been looking around on the forums and stuff, but no luck. 

The main problem is that, my sound card driver is not available otherwise, i could have installed it manually. you can see it by yourself:

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

btw my card is ICH8 and its the newest from Intel i think. Anyway, thanks for your effort and hope that someone will be able to help me out :)

---

### Post by northern lights on 2008-02-25
Ajit -

frickin' Behari nutter! I suppose you were not entirely sober when you screwed your system?!
Man, you really don't live that far from me, I'll swing by tonight and we can work ob it 2gether.

P.S. How was your Physical Oceanography exam?

---

### Post by superprash2003 on 2008-02-26
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by RikardSvenningsen on 2008-03-18
I got no sound, and as I can tell i don't have a detected sound card, My pc is sold in Denmark by Dell (DK) they said that it should be a supported Dell model.
What can I do to get some sound?

---

### Post by northern lights on 2008-03-26
Richard, can you please post the output of ```
cat /proc/asound/cards
```

---

### Post by RikardSvenningsen on 2008-03-28
Sorry for the late respond.
Gives this respond.

rs@RS-U1:~$ cat /proc/asound/cards 
--- no soundcards ---

---

### Post by auddin2 on 2008-03-28
I have the same laptop and problem:
here are my outputs:

```

root@laptop:~# cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
root@laptop:~# aplay -l
aplay: device_list:204: no soundcards found...
root@laptop:~# cat /proc/asound/cards
--- no soundcards ---

```

The "lspci" command gives me the same output as the first post.

---

### Post by DellCA on 2008-03-31
The Latitude D630 uses the Intel IDT® STAC9205 audio chipset.  I haven't tried getting that particular audio chipset to work in linux so I don't know if it needs anything specific (kernel conf, etc) but I thought I'd pass on that information in case it helps you find the settings you need to get audio working correctly.

Another option, depending on how you have things set up, would be to see how the audio behaves in Windows (since the system originally shipped with Windows).  While it doesn't really help with the linux side, it does help determine if its a hardware problem or not (if it works fine in Windows, it is not a hardware problem).

Larry
Dell Customer Advocate

---

### Post by northern lights on 2008-03-31
It's most likely to certainly not a hardware problem.

If you were to check this [link]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel"), which Deepu posted already you'd see that the ALSA version used in Gutsy does not support ICH8 family sound devices. You probably could download the current ALSA source and compile by hand (I doubt Gutsy repos will have it soon) or update to the latest Hardy Beta - sound on the Latitude D630 worked since Hardy Alpha5 at least...

---

### Post by RikardSvenningsen on 2008-04-01
In my case, it works great under Windows Vista 64 bit but I prefer to work with Linux Ubuntu in that I got more power to work with.

---

### Post by northern lights on 2008-04-03
In 26 days Hardy will be released as a stable. If you want to avoid installing a beta, which I wouldn't recommend unless you're rather firm with *nix, wait it out for 4 weeks and sound will be there...

Otherwise you have to got through manual ALSA compilation...

---

### Post by RikardSvenningsen on 2008-04-03
I wait for the new driver.
Would there be some announcement of the driver and/or some installation guide.

---

