---
title: "Speed test of SD card"
date: 2013-03-18
forum: General Help
---

### Post by Fraoch on 2013-03-18
Yeah, I know, this isn't possible, but it's like I'm reading from a cache or something?

Doing speed testing on an SD card using Ubuntu 12.10 64-bit and the following commands:

```
dd if=/dev/zero of=~/test.tmp bs=500K count=1024

dd if=~/test.tmp of=/dev/null bs=500K count=1024
```

I'm interpreting that as writing zeroes to test.tmp, then reading back test.tmp to /dev/null.  Right?

It worked a couple of times, now I'm getting:

```
mark@Sauron:/media/mark$ dd if=/dev/zero of=/media/mark/test.tmp bs=500K count=1024
1024+0 records in
1024+0 records out
524288000 bytes (524 MB) copied, 466.175 s, 1.1 MB/s
mark@Sauron:/media/mark$ dd if=/media/mark/test.tmp of=/dev/null bs=500K count=1024
1024+0 records in
1024+0 records out
524288000 bytes (524 MB) copied, 0.166738 s, 3.1 GB/s
```

What?  3.1 GB/s shouldn't be possible over USB 2.0.  It shouldn't even be possible over SATA3 for that matter...

What's going on here?

---

### Post by The Cog on 2013-03-18
The second dd is probably reading from cache memory rather than from the hardware.

---

### Post by Fraoch on 2013-03-18
> **The Cog said:**
> The second dd is probably reading from cache memory rather than from the hardware.

That's what it looks like, but I can't figure out what cache.  The SD card itself has no cache of course, nor does the card reader.  With a speed of 3.1 GB/s, looks like it's reading from main memory somehow?  Odd also that it performed this test properly a few times, then this, consistently and repeatedly.

---

### Post by rnerwein on 2013-03-18
> **Fraoch said:**
> That's what it looks like, but I can't figure out what cache.  The SD card itself has no cache of course, nor does the card reader.  With a speed of 3.1 GB/s, looks like it's reading from main memory somehow?  Odd also that it performed this test properly a few times, then this, consistently and repeatedly.
hi
if you want to know what's going up - following these steps.
1. after you reboot - open a terminal and run: top (have a look at mem used and cached used)
2. run your tests using another filename ---> look again at the values
3. run it again     ---> look at your values
4. delete those files
5. look again at the top values (mem used and cache) - surprised ?-)
what i'll tell U is - it is not always what you see is what you get.
by the way that's a part of the reason (I/O speed - not CPU ticks - that's mostely blended ) of the price of hig-end servers.
ciao

---

### Post by Cheesemill on 2013-03-18
> **Fraoch said:**
> That's what it looks like, but I can't figure out what cache.  The SD card itself has no cache of course, nor does the card reader.  With a speed of 3.1 GB/s, looks like it's reading from main memory somehow?  Odd also that it performed this test properly a few times, then this, consistently and repeatedly.

It's being cached in RAM.

Any file that you access on a Linux machine is held in RAM as a cached file, the file is only dropped by the cache if your RAM is needed for a running process.
For more information this page may be of some help...

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by rnerwein on 2013-03-18
> **Cheesemill said:**
> It's being cached in RAM.

Any file that you access on a Linux machine is held in RAM as a cached file, the file is only dropped by the cache if your RAM is needed for a running process.
For more information this page may be of some help...

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
+1 Cheesemill - short and clear (just a little question: what is RAM ? - you now what i mean - have my funny day today ;-)   )
ups - don't understand me false ( i think you now what i mean)
ciao
          richi

---

### Post by Fraoch on 2013-03-18
> **Cheesemill said:**
> It's being cached in RAM.

Any file that you access on a Linux machine is held in RAM as a cached file, the file is only dropped by the cache if your RAM is needed for a running process.
For more information this page may be of some help...

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

That makes sense, thank you.

I'm googling around, and it seems that there are workarounds to disable caching for this process:

[http://romanrm.ru/en/dd-benchmark](http://romanrm.ru/en/dd-benchmark)

I might try the conv=fdatasync option specified on that page.

Incidentally I probably wasn't using this the proper way in the first place.  I'm speed testing two new SD cards for use in a Raspberry Pi (not delivered yet!) which only has 512 MB of RAM and could never cache 524 MB of data:

[http://elinux.org/RPi_SD_cards#Performance](http://elinux.org/RPi_SD_cards#Performance)

---

### Post by Cheesemill on 2013-03-18
Just a little snippet to add. If you want to force all cached files to be dropped to ensure you are testing the speed of the SD card you can use the following command between runs...
```
echo 3 | sudo tee /proc/sys/vm/drop_caches
```

---

### Post by tgalati4 on 2013-03-18
Because of the hardware differences between a Rapberry Pi and a true Linux desktop or laptop, the real speed test will need to be done using actual hardware, running actual programs on the Pi.  Anything else is just a suggestion of performance.  If you want robust testing, then install *phoronix-test-suite* and run some I/O and file-handling benchmarks.  I don't know if the phoronix test suite has been ported to the Pi, but that would give you some serious benchmarks to compare.

Because of the wear-leveling used on SD cards, they tend to slow down over time.  So new card versus 6-month-old card testing would be useful.

---

### Post by rnerwein on 2013-03-18
> **Cheesemill said:**
> Just a little snippet to add. If you want to force all cached files to be dropped to ensure you are testing the speed of the SD card you can use the following command between runs...
```
echo 3 | sudo tee /proc/sys/vm/drop_caches
```
hi cheesemill
that's ok - but i think you missed the "sync" before. must be your keyboard ;-)
no swet - have fun (you understand me or ?)
ciao

---

### Post by Fraoch on 2013-03-18
> **tgalati4 said:**
> Because of the hardware differences between a Rapberry Pi and a true Linux desktop or laptop, the real speed test will need to be done using actual hardware, running actual programs on the Pi.  Anything else is just a suggestion of performance.

Yeah - I was afraid of that.  It's a long wait for a Raspberry Pi lately (total of 6 weeks, I'm down to 4 now) so I was buying accessories and playing around with emulators.

Given the stress I'm putting on these SD cards by repeatedly attempting these tests and the dubious results I'm getting I'll have to stop.

Thanks.

---

### Post by tgalati4 on 2013-03-18
My experience with a Barnes&Noble Nook Color that has been reflashed with Android Gingerbread:  Running with a Class 4 or 6 SD card was faster than a Class 10 because the 4/6 cards used smaller block sizes than the larger Class 10 cards.  Due to the bandwidth of the SD card slot in the Nook, the smaller, slower Class 4/6 cards worked better--especially when running Android directly from the card, not the built-in flash.  So using spec numbers and emulated hardware won't give you true performance.  It was a suprising result for folks playing with the Nook, but I suspect the PI has hardware closer to the Nook than a laptop.

This is a long read, but you will gain some insight into how SD cards work:  [http://forum.xda-developers.com/showthread.php?t=1005633](http://forum.xda-developers.com/showthread.php?t=1005633)

---

### Post by Fraoch on 2013-03-18
> **tgalati4 said:**
> My experience with a Barnes&Nobel Nook Color that has been reflashed with Android Gingerbread:  Running with a Class 4 or 6 SD card was faster than a Class 10 because the 4/6 cards used smaller block sizes than the larger Class 10 cards.  Due to the bandwidth of the SD card slot in the Nook, the smaller, slower Class 4/6 cards worked better--especially when running Android directly from the card, not the built-in flash.  So using spec numbers and emulated hardware won't give you true performance.  It was a suprising result for folks playing with the Nook, but I suspect the PI has hardware closer to the Nook than a laptop.

Sure hope that isn't the case here because I bought two of the fastest Class 10 cards I could afford - one was a new "UHS-1" type.  However I made sure these exact ones were listed and had fast test results posted on the Raspberry Pi page.  But as your link points out, benchmarks aren't everything.  :(

I've tested them both using CrystalDiskMark to compare to that posting.  It's somewhat hopeful, the slower card measures 0.73 MB/s for 4K random writes with queue depth = 32 and the "faster" card 0.463 MB/s.  So middle-of-the-road, but surpassed by some of those class 2 and 4 cards which I did see in the store beside the ones I bought.  Looks like I overbought.

The Pi's card reader is connected directly to the CPU's GPIO pins, not through any kind of storage subsystem.  We'll see if that means raw speed trumps block sizes...

Oh well, I can use them in cameras if they prove problematic, and replacement class 4/6 cards are fairly cheap in comparison.  And they're from a top-tier manufacturer (SanDisk) so they should be fairly robust and reliable.

---

