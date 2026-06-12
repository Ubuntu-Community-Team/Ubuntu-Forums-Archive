---
title: "Very hot system"
date: 2008-05-18
forum: General Help
---

### Post by mcgodx on 2008-05-18
I bought all the parts needed to built a computer last week and I built it, the specs are as follows:

Intel DG35EC motherboard
Intel Q9300 Core 2 Quad (45nm) processor at 2.5GHz (no overclocking)
4GB of Geil Esoteria DDR2 RAM
2 320GB hard drives (will be putting a RAID card in there to put them in RAID0
1 DVD drive
On board graphics for now, but plan on upgrading to an 8800GTS

The problem I am having is, according to lm-sensors, my system runs HOT.  The CPU is 66C which isn't so bad I guess, but the chipset (I'm assuming it's the chipset, it is in lm-sensors as "system temp", it stays anywhere from 92-96C.  I don't know if that is normal, but I don't think it should be that high...

I looked at the fan speed, and they stay from 1050-1100.  They are rated at 2050.  I have them wired to the motherboard connectors.  Is there a way other than hooking them straight up to the power supply to speed them up?  I think there may be a problem somewhere as I should think the fans would spin up when the system gets that hot.  I don't have enough room in my case for a hardware fan controller, since it is a micro atx unit.

Thanks for any help

Mylan

---

### Post by Nem1976 on 2008-05-19
Have you checked the Bios tempature readings yet?  There may be an issue with the lm-sensors not reading the sensor correctly.  Reboot the system and get into the bios and under hardware monitoring see what the system temps are showing.  If they are reading as high as lm-sensors then you have an issue.    You can even just open the case up and see how hot it feels inside.  If it is hot then the fans may not be blowing enough air through.  But would check the bios readings first.

Nem

---

### Post by mcgodx on 2008-05-19
> **Nem1976 said:**
> Have you checked the Bios tempature readings yet?  There may be an issue with the lm-sensors not reading the sensor correctly.  Reboot the system and get into the bios and under hardware monitoring see what the system temps are showing.  If they are reading as high as lm-sensors then you have an issue.    You can even just open the case up and see how hot it feels inside.  If it is hot then the fans may not be blowing enough air through.  But would check the bios readings first.

Nem

Not exactly sure if it's right, my BIOS only shows CPU and "internal temperature".  Maybe that's the air temperature inside?  The CPU was at 53C and the "internal temp was at 46C", right now according to lm-sensors it is 67C right after boot.  The "Sys Temp" is at 94C.  That's quite a bit cooler, but then again the CPU would probably cool down SOME wouldn't it?  The fans were spinning at the same rate.  Around 1100RPMs.

---

### Post by Nem1976 on 2008-05-19
Most likely it sounds like an issue with lm-sensor not registering the correct sensor.  What I would do it leave the system on for 10 min's or something then just restart it and go into the bios right away.  check the temp's and see what they say.

---

### Post by sdennie on 2008-05-19
I think some motherboards don't correctly report temperatures to lm-sensors.  I have a machine that regularly reports that one of the temperatures is -174 degrees (which seems unlikely).  I would check the following and, if all the temps are reasonable, I don't think you have anything to worry about:

```

cat /proc/acpi/thermal_zone/THM/temperature
nvidia-settings -q GPUCoreTemp

```

You can also check the temperature of disk with:

```

sudo apt-get install smartmontools
sudo smartctl --all /dev/sda | grep Temp

```

---

### Post by mcgodx on 2008-05-19
Thanks.  I think the problem is that one sensor, whatever it is.  Everything else seems fairly consistent in lm-sensors with 32C for the hard drives (which makes sense, my laptop's hard drive wasn't much hotter than that), ~62-67C for the CPU, and about 44 for "Aux Temp", which I guess is the "Internal Temp" that I was noticing in the BIOS.  "Aux Temp does go all over the place from time to time, though, I saw it just go to -2C, 27C, and 13C in 1 minute, then it sits there fine for a while.

Weird.

I don't guess there is a better way of monitoring this, is there?

---

### Post by Nem1976 on 2008-05-20
I read that a new lm-sensor was being released or has been released.  

[http://www.phoronix.com/scan.php?page=news_item&px=NjQ3OQ](http://www.phoronix.com/scan.php?page=news_item&px=NjQ3OQ)

---

### Post by fsmithred on 2008-05-20
You could edit /etc/sensors.conf in the section for your chipset to comment out the aux temp, and maybe to factor the MB temp (half of that 94 is correct). Or, you could use gkrellm to monitor the sensors, and set it up so it displays the right information. The latter is easier.

---

### Post by danwood76 on 2008-05-20
67*C is high for this CPU, thermal throttling kicks in at 65*C I believe.
What cooler do you have on it?

If your system is idleing at 67 then you should either reseat the cooler with some better thermal grease or get a new cooler.

---

### Post by fjgaude on 2008-05-20
Yes, my dual core 45nm E8400 runs at about 26C idling and 44C at full load. Quad core runs likely hotter but the cooler is everything. Likely the Intel one that comes with it is okay as long as you don't overclock. I would think about 35C should be what it should be by what I've read of the original poster.

---

### Post by danwood76 on 2008-05-20
My E6420 idles at 30C and under load hits 58 and I think thats hot.
Though I am OC'd to 3.6GHz and on water.

---

### Post by fjgaude on 2008-05-20
Well, the fan, water or air, tells the tale:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.36/1.34v:

```

root@sunshine:/home/frank# hdparm -tT /dev/md32
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec

```

---

