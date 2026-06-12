---
title: "RAID arrays HowTo ?"
date: 2008-06-09
forum: General Help
---

### Post by drsox1899 on 2008-06-09
I have a PC just for doing experiments in Linux - well now it's RAID experiment time.

I've been reading about fake RAID (software RAID made to look like hardware RAID) and my question is this :

I was going to buy an Adaptec AAR-1220SA PCI-Express RAID controller to run 2x Seagate 80GB SATAs in a RAID0 config for speed.  
This seems likely to be a Fake RAID controller - so am I any better off than just using the built in RAID capability on my Asrock ALiveNF6P-VSTA mobo ?

I can see that I get another 2 SATA drive slots, but what else ?

Thanks

---

### Post by housam on 2008-06-09
you can read all about it [[COLOR="Red"]_here_[/COLOR]]("http://en.wikipedia.org/wiki/RAID")

---

### Post by fjgaude on 2008-06-09
If that Adaptec board costs more than about $300.00 then it is real raid, and you will need a Linux driver to make it work in Ubuntu.

If you have a fast CPU and memory, software can be as fast as hardware. Look at my speeds shown earlier:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

I'm using mdadm raid5 on four Seagate drives of which each has a throughput of about 70MB/sec.

---

### Post by drsox1899 on 2008-06-09
> **fjgaude said:**
> If that Adaptec board costs more than about $300.00 then it is real raid, and you will need a Linux driver to make it work in Ubuntu.

If you have a fast CPU and memory, software can be as fast as hardware. Look at my speeds shown earlier:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

I'm using mdadm raid5 on four Seagate drives of which each has a throughput of about 70MB/sec.

No, it's a lot cheaper so unlikely to be real RAID.  Your speeds look very good - I'll try out the software RAID.  
I need to use WinXp as well so a fake RAID seems to be the best way for both - so say the Ubuntu Oracles.

Thanks

---

