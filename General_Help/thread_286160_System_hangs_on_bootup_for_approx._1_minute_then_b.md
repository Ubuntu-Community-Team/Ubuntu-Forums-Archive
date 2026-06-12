---
title: "System hangs on bootup for approx. 1 minute then boots fine...?"
date: 2006-10-27
forum: General Help
---

### Post by strabes on 2006-10-27
I have a new install of edgy. On the new bootsplash screen when the bar is about 1/3 filled, my system hangs for about 1 minute. There is no processor activity at all. After that 1 minute or so the bar finishes filling up, and my computer boots fine. I was just wondering if anyone is having the same problem or has figured out a fix for this? I assume it is because of some bootup process or hardware configuration but I can't really tell because there is no text on the new bootsplash. I have a Dell Inspiron E1705 by the way. I realize this is a super vague and non-specific question but it's really bothering me.

---

### Post by beerorkid on 2006-10-27
well some module or something is hanging up.  There is some key combination that will allow you to see the scrolling text.  Think it is tab or alt f2?

after that you can get BUM (boot up manager) installed and pull the offender out.

you can always hit crtl C and it will skip loading whatever is holding it up.

---

### Post by jocko on 2006-10-27
If you want to see what's taking time during boot, install bootchart:
```
sudo aptitude install bootchart
```
Each boot it will create a chart that may give you some clues in /var/log/bootchart.

---

### Post by strabes on 2006-10-27
hmm neither of those key combinations seem to be working to show any text on the bootsplash screen. I will continue searching for something like this though. Thanks for your input

---

### Post by beerorkid on 2006-10-27
try just f2  (suggestion from linux dork where I am at)
Not on a ubuntu box currently.
Out of office on a winders laptop :(

---

### Post by strabes on 2006-10-27
what i did was boot into the recovery mode kernel using grub, and the part that it hangs on is when it says "configuring nework interfaces." What should I disable in BUM to make this stop?

---

### Post by beerorkid on 2006-10-27
well I looked through bum and did not see anything that jumped out at me.

possibly set your IP address as a static?

It does seem like something is definately mucked up though.

---

### Post by sandrovich on 2006-10-27
I have the same problem with a fresh install. When the boot bar is at 5/100 the computer hangs up, after a while it goes up and the login screen appear. To see what part of the boot is messing around, I edit the boot in grub, removing the quiet splash option. I realize the problem is with my sata controller, the system stops looking for drives in ports where there are nothing. This is the output:
```
ata1: SATA max UDMA/133 cmd 0xF882A100 ctl 0x0 bmdma 0x0 irq 193
Oct 28 00:35:19 abit-at8 kernel: [17179588.260000] ata2: SATA max UDMA/133 cmd 0xF882A180 ctl 0x0 bmdma 0x0 irq 193
Oct 28 00:35:19 abit-at8 kernel: [17179588.260000] ata3: SATA max UDMA/133 cmd 0xF882A200 ctl 0x0 bmdma 0x0 irq 193
Oct 28 00:35:19 abit-at8 kernel: [17179588.260000] ata4: SATA max UDMA/133 cmd 0xF882A280 ctl 0x0 bmdma 0x0 irq 193
Oct 28 00:35:19 abit-at8 kernel: [17179588.636000] ata1: SATA link up 1.5 Gbps (SStatus 113)
Oct 28 00:35:19 abit-at8 kernel: [17179588.636000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:007f
Oct 28 00:35:19 abit-at8 kernel: [17179588.636000] ata1: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48
Oct 28 00:35:19 abit-at8 kernel: [17179588.636000] ata1: dev 0 configured for UDMA/133
Oct 28 00:35:19 abit-at8 kernel: [17179588.636000] scsi0 : ahci
Oct 28 00:35:19 abit-at8 kernel: [17179589.556000] ata2: SATA link down (SStatus 0)
Oct 28 00:35:19 abit-at8 kernel: [17179619.576000] ata2: qc timeout (cmd 0xec)
Oct 28 00:35:19 abit-at8 kernel: [17179619.576000] ata2: dev 0 failed to IDENTIFY (I/O error)
Oct 28 00:35:19 abit-at8 kernel: [17179619.576000] scsi1 : ahci
Oct 28 00:35:19 abit-at8 kernel: [17179620.496000] ata3: SATA link down (SStatus 0)
Oct 28 00:35:19 abit-at8 kernel: [17179650.516000] ata3: qc timeout (cmd 0xec)
Oct 28 00:35:19 abit-at8 kernel: [17179650.516000] ata3: dev 0 failed to IDENTIFY (I/O error)
Oct 28 00:35:19 abit-at8 kernel: [17179650.516000] scsi2 : ahci
Oct 28 00:35:19 abit-at8 kernel: [17179651.436000] ata4: SATA link down (SStatus 0)
Oct 28 00:35:19 abit-at8 kernel: [17179681.456000] ata4: qc timeout (cmd 0xec)
Oct 28 00:35:19 abit-at8 kernel: [17179681.456000] ata4: dev 0 failed to IDENTIFY (I/O error)
Oct 28 00:35:19 abit-at8 kernel: [17179681.456000] scsi3 : ahci
```

I have my hd plug into de port number one, and the system recognize it (sata link up 1.5Gbps), but it takes up to one minute or more to realize that there aren't more drives available in the other ports.

I have an abit at8 motherboard with ati rs480 northbridge, and uli m1575 southbridge with sata controller in chip (m5288 )

---

### Post by strabes on 2006-10-27
soooo... what should I do?

---

### Post by beerorkid on 2006-10-28
possibly start a thread that says "configuring nework interfaces hangs"

You are a few steps closer.  Threads tend to be burried, it would be more specific.

Or check in the bugfix area  [https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu)

---

### Post by strabes on 2006-11-01
For some reason after hitting ctrl + C (I think) while it was booting and hanging at that point, it stopped and now it doesn't hang anymore. Edgy boots dang fast on my computer wow.

---

