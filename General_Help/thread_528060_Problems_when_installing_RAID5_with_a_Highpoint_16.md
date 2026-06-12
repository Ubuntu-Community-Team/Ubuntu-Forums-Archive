---
title: "Problems when installing RAID5 with a Highpoint 1640 card"
date: 2007-08-17
forum: General Help
---

### Post by HarryM on 2007-08-17
Hello,

I'm trying to get a RAID5 array working on Feisty. I have a Highpoint 1640 controller, so I started following the FakeRaid instructions and installed dmraid. It finds the disks in the raid, but fails to activate them:

```
root@arta-serv:~# dmraid -r

/dev/hde: hpt45x, "hpt45x_cijgafjff", unknown, ok, 625142437 sectors, data@ 0
/dev/hdg: hpt45x, "hpt45x_cijgafjff", unknown, ok, 586114693 sectors, data@ 0
/dev/hdi: hpt45x, "hpt45x_cijgafjff", unknown, ok, 586072357 sectors, data@ 0
/dev/hdk: hpt45x, "hpt45x_cijgafjff", unknown, ok, 586114693 sectors, data@ 0


root@arta-serv:~# dmraid -aY

ERROR: hpt45x: RAID type 8 not supported
ERROR: adding /dev/hde to RAID set "hpt45x_cijgafjff"
ERROR: hpt45x: RAID type 8 not supported
ERROR: adding /dev/hdg to RAID set "hpt45x_cijgafjff"
ERROR: hpt45x: RAID type 8 not supported
ERROR: adding /dev/hdi to RAID set "hpt45x_cijgafjff"
ERROR: hpt45x: RAID type 8 not supported
ERROR: adding /dev/hdk to RAID set "hpt45x_cijgafjff"
No RAID sets

```

Google only returns [one result for that error message]("http://www.linuxquestions.org/questions/showthread.php?t=381986"), which isn't a helpful one -- the guy gave up. There is a thread here, though, that suggests that [it might be possible using the proprietary drivers]("http://ubuntuforums.org/showthread.php?t=272115").

I'm reasonably new to Linux and I'm not sure how I might go about installing a proprietary driver.   [Drivers are available]("http://www.highpoint-tech.com/USA/bios_rr1640.htm") but not for Ubuntu. Can I install drivers intended for another distribution? Will it break things?

The array has ~750Gb of data on it and I don't have anything like that much space anywhere else, so I need to get the current configuration working if at all possible. Needless to say, losing all that data would be extremely bad, so I'd rather not try anything risky :)

---

### Post by fjgaude on 2007-08-17
I've been using software Linux raid for sometime now with full satisfaction. I tried fakeraid from my motherboard and found that Ubuntu's Feisty latest kernel, i.e., 2.6.20.16, doesn't support raid5. I believe that 2.6.22 in Gutsy does... but I switched and am more than happy with md and mdadm, the present Linux standard.

I know that mdadm only supports raid 0, 1, 4, 5, 6, and Linear (JBOD).

I don't know raid 8. How are you getting this? Oh, I see, a Highpoint 1640. Since dmraid recognizes your hpt board it would be fine if you had a raid level that the Linux kernel handles. Maybe the newest kernel would do the trick, 2.6.22.

What does a sudo dmraid -tay show?

frank

---

### Post by HarryM on 2007-08-19
> **fjgaude said:**
> 
What does a sudo dmraid -tay show?


```
root@arta-serv:/home/arta# dmraid -tay

ERROR: hpt45x: RAID type 8 not supported
ERROR: adding /dev/hde to RAID set "hpt45x_cijgafjff"
ERROR: hpt45x: RAID type 8 not supported
ERROR: adding /dev/hdg to RAID set "hpt45x_cijgafjff"
ERROR: hpt45x: RAID type 8 not supported
ERROR: adding /dev/hdi to RAID set "hpt45x_cijgafjff"
ERROR: hpt45x: RAID type 8 not supported
ERROR: adding /dev/hdk to RAID set "hpt45x_cijgafjff"
No RAID sets

```

Cheers for the advice -- I'll install .22 and report back.

---

### Post by HarryM on 2007-10-31
Ok, well, just to clear this up:

I've now installed .23 and dmraid still doesn't work. It gives the same error and gives up. I had a bit of a play with mdadm but it looked like it would have to create its own array rather than using the one created by my card, so I decided not to do much with it -- mustn't lose this data!

Eventually I installed the hpt374 proprietary driver (the "open source" one). Thankfully, that works quite nicely.

For anyone considering what RAID card to buy, avoid this one: it's been a pain to get working and it's not a real RAID card anyway; it offloads a lot of stuff to the CPU. Essentially, it sucks, and you'll be much better off spending a bit extra on a card that actually works, or just using a software raid. This card is the worst of both worlds.

---

### Post by fjgaude on 2007-10-31
Okay, thanks for keeping us informed. I've learned that software can be very, very fast if the controllers are running off the PCI-Express bus and not the PCI. PCI tops out at 133 MB/sec, and that is the speed of two modern drives in stipe, raid0. PCI-E x1 has a throughput of 250 MB/sec, and x4 something like over 500 MB/sec, and that is good enough for raid5 with five drives. 

I see that Hitachi's newest drives are claiming throughputs of 144 MB/s, single drive. Wow!

Any of the cheap controller cards are not worth buying because of their low throughput. You need to spend at least $300 to get to what the latest motherboards cover, with their attached-to-PCI-E bus, coming in at over 300 MB/s in stripe or raid5.

Highpoint 2310 seems to be a fast controller card, as Tom's Page as presented.

---

### Post by citydog on 2007-11-18
Hi HenryM,

Can you share how you were able to compile the proprietary driver for gusty?  Hopefully, you are on gusty as that's what I am using.

Thank,

---

### Post by citydog on 2007-11-18
To add, I would like to get existing data off the raid5 and switch back to linux raid.  So, if you are willing to share binary, my kernel version is 2.6.22-14-generic.

Thanks in advanced.

---

### Post by HarryM on 2007-11-19
I don't remember exactly how I did it, sorry -- it was pretty straightforward though. IIRC, I just compiled it and installed the .ko with modprobe. The readme in the source code download has some basic instructions, should get you started at least.

---

### Post by screaminglucy on 2008-01-05
See this related thread:
[http://ubuntuforums.org/showthread.php?t=631090]("http://ubuntuforums.org/showthread.php?t=631090")

---

