---
title: "How to tell my SSD speed - should I upgrade mobos?"
date: 2015-05-27
forum: General Help
---

### Post by PsychedelicWonders on 2015-05-27
I have an Asus mobo that allows 3/mbs and I know that SSDs can/should be running at 6/mbs - so that right there may want me to upgrade, but my computer is still surprisingly fast for how old it is and without it being over clocked.

How can I tell how fast my new SSD is interacting with the mobo to see it if it's even running at the 3/mbs or if it's less?

If it's not even doing 3/mbs I will probably just upgrade at this time to take full advantage of the speed of a new mobo & 5820k Hexacore.  (vs my 6600 quad core)

---

### Post by sandyd on 2015-05-27
For all ports```

dmesg | grep "SATA link up"
```

---

### Post by nerdtron on 2015-05-27
3mbps? is that a typo or you mean mean 3gbps read/write speed of SSDs?


Anyway, if you want to see how fast you can read/write data to your SSD drive:
READ speed:
```
$ sudo hdparm -Tt --direct /dev/sda

/dev/sda:
 Timing O_DIRECT cached reads:   154 MB in  2.01 seconds =  76.47 MB/sec
 Timing O_DIRECT disk reads: 334 MB in  3.01 seconds = 110.82 MB/sec

```


WRITE: (warning: this will create a 1GB file on your current directory, you should delete that file after the test)
```
sync; [FONT=courier new, monospace]dd if=/dev/zero of=testfile0 bs=1M count=1000; sync; 
```

delete the file you created on your test:
```
rm testfile0 
```
[/FONT]

---

### Post by PsychedelicWonders on 2015-05-28
Well I forgot my encryption password for ubuntu already lol so I can't run the test in ubuntu as of yet, I'm going to have to to a secure erase and re-install of Ubuntu.  No big deal really it was a fresh install so nothing to worry about losing.

But I did run an SSD speed test of a Samsung 850 Pro 256g SSD in windows 7 and here are the results.

I have Ubuntu on a Samsung 850 Pro 128g SSD

[COLOR=#323232][FONT=verdana]Is this good or not really? [/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]At this point since i just bought two Samsung 850 pros, I dont want to spend more on PCI card SSDs and would almost rather just upgrade mobo & processor if my speeds really suck with my current mobo/processor[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]I read where this program writes a 1gb file for the test, how do I go about deleting this 1gb file?[/FONT][/COLOR][ATTACH=CONFIG]262274[/ATTACH]

---

### Post by Bucky Ball on 2015-05-29
SATAIII will do 6gbps, yes. SATAII is 3. Which SSD do you have, SATA III or II?

Update: Looks like the 850s are capable of SATAIII 6gbps speeds. From [here]("http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/ssd850pro/specifications.html"):

> SATA 6Gb/s (compatible with SATA 3Gb/s and SATA 1.5Gb/s)

---

### Post by PsychedelicWonders on 2015-06-03
So for SATA II with SATA cables, but bios set to IDE - am I getting good speeds?

I'm trying to install Asus ACHI/RAID drivers so I can try to get the ACHI function in bios.  

This is for windows right now, I need to re-install Ubuntu as I forgot my encryption password already lol

---

