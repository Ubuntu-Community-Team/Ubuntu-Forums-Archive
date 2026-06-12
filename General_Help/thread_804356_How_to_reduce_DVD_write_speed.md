---
title: "How to reduce DVD write speed?"
date: 2008-05-23
forum: General Help
---

### Post by telko on 2008-05-23
Hello,

Trying to write a DVD I´ve found that I cannot do it at speeds slower than 6x. I´ve tried different programs (Brasero and GnomeBaker); and even I chose a slow speed like 1x or 2x, when it writes I realize it´s writing at 6x. I´ve also tried from command line with "growisofs" and option "speed=1", but the result is the same, writing at 6x. On the other hand, I can write faster without any problem. This happens with DVDs from all brands, +R and -R.

I think I have a clue with "dvd+rw-mediainfo", with the output:
$ dvd+rw-mediainfo /dev/cdrom1
INQUIRY: [DVDRW ][20X20X12X ][6A31]
GET [CURRENT] CONFIGURATION:
Mounted Media: 1Bh, DVD+R
Media ID: MCC/004
Current Write Speed: 16.0x1385=22160KB/s
Write Speed #0: 16.0x1385=22160KB/s
Write Speed #1: 12.0x1385=16620KB/s
Write Speed #2: 8.0x1385=11080KB/s
Write Speed #3: 6.0x1385=8310KB/s
GET [CURRENT] PERFORMANCE:
Write Performance: 6.4x1385=8864KB/s@[0 -> 0]
Speed Descriptor#0: 00/0 R@6.4x1385=8864KB/s W@16.0x1385=22160KB/s
Speed Descriptor#1: 00/0 R@6.4x1385=8864KB/s W@12.0x1385=16620KB/s
Speed Descriptor#2: 00/0 R@6.4x1385=8864KB/s W@8.0x1385=11080KB/s
Speed Descriptor#3: 00/0 R@6.4x1385=8864KB/s W@6.0x1385=8310KB/s
READ DVD STRUCTURE[#0h]:
Media Book Type: 00h, DVD-ROM book [revision 0]
Legacy lead-out at: 2295104*2KB=4700372992
READ DISC INFORMATION:
Disc status: blank
Number of Sessions: 1
State of Last Session: empty
"Next" Track: 1
Number of Tracks: 1
READ TRACK INFORMATION[#1]:
Track State: blank
Track Start Address: 0*2KB
Next Writable Address: 0*2KB
Free Blocks: 2295104*2KB
Track Size: 2295104*2KB
ROM Compatibility LBA: 262144
READ CAPACITY: 0*2048=0

I see that the list of "write speed" ranges from 6x to 16x, therefore I think that the problem is not in the program I use, but it´s in a lower level.

I´ve been using Ubuntu (and Linux) for a short time, but I think the problem is in the driver. I don´t know if I can change the DVD writer driver or even where to search for a new driver. 

I´m using Ubuntu 8.04 and all the packets are upgraded to the last version.

Anyone can help me or give me advice to write at 2x or 4x speed?

Thank you.

---

### Post by HunterThomson on 2008-05-23
I use K3B (in the add/remove thing) you can select the write speed by selecting it in a drop down box. fairly striate forward you should get it to work no problem.

---

### Post by HunterThomson on 2008-05-23
> **telko said:**
> Hello,

Trying to write a DVD I´ve found that I cannot do it at speeds slower than 6x. I´ve tried different programs (Brasero and GnomeBaker); and even I chose a slow speed like 1x or 2x, when it writes I realize it´s writing at 6x. I´ve also tried from command line with "growisofs" and option "speed=1", but the result is the same, writing at 6x. On the other hand, I can write faster without any problem. This happens with DVDs from all brands, +R and -R.

I think I have a clue with "dvd+rw-mediainfo", with the output:
$ dvd+rw-mediainfo /dev/cdrom1
INQUIRY: [DVDRW ][20X20X12X ][6A31]
GET [CURRENT] CONFIGURATION:
Mounted Media: 1Bh, DVD+R
Media ID: MCC/004
Current Write Speed: 16.0x1385=22160KB/s
Write Speed #0: 16.0x1385=22160KB/s
Write Speed #1: 12.0x1385=16620KB/s
Write Speed #2: 8.0x1385=11080KB/s
Write Speed #3: 6.0x1385=8310KB/s
GET [CURRENT] PERFORMANCE:
Write Performance: 6.4x1385=8864KB/s@[0 -> 0]
Speed Descriptor#0: 00/0 R@6.4x1385=8864KB/s W@16.0x1385=22160KB/s
Speed Descriptor#1: 00/0 R@6.4x1385=8864KB/s W@12.0x1385=16620KB/s
Speed Descriptor#2: 00/0 R@6.4x1385=8864KB/s W@8.0x1385=11080KB/s
Speed Descriptor#3: 00/0 R@6.4x1385=8864KB/s W@6.0x1385=8310KB/s
READ DVD STRUCTURE[#0h]:
Media Book Type: 00h, DVD-ROM book [revision 0]
Legacy lead-out at: 2295104*2KB=4700372992
READ DISC INFORMATION:
Disc status: blank
Number of Sessions: 1
State of Last Session: empty
"Next" Track: 1
Number of Tracks: 1
READ TRACK INFORMATION[#1]:
Track State: blank
Track Start Address: 0*2KB
Next Writable Address: 0*2KB
Free Blocks: 2295104*2KB
Track Size: 2295104*2KB
ROM Compatibility LBA: 262144
READ CAPACITY: 0*2048=0

I see that the list of "write speed" ranges from 6x to 16x, therefore I think that the problem is not in the program I use, but it´s in a lower level.

I´ve been using Ubuntu (and Linux) for a short time, but I think the problem is in the driver. I don´t know if I can change the DVD writer driver or even where to search for a new driver. 

I´m using Ubuntu 8.04 and all the packets are upgraded to the last version.

Anyone can help me or give me advice to write at 2x or 4x speed?

Thank you.

Owe ok.... why do you want to write at lower speeds? What problems are you haveing?

---

### Post by FuturePilot on 2008-05-23
> **HunterThomson said:**
> Owe ok.... why do you want to write at lower speeds? What problems are you haveing?

Sometimes it's better to burn things at a slower speed to reduce the risk of errors, such as .iso files.

---

### Post by zvacet on 2008-05-23
Does your optical drive support that kind of speed?My doesn´t.

---

### Post by telko on 2008-05-23
I haven´t tried k3b but the other apps I´ve tried have the same drop down box to choose speed, so I would discard that solution. Provinding that all these apps use the same low level programs (I´m not sure about this) all of them would give same results.

I think that the DVD writer supports that speeds because I´ve tried to burn a DVD-RW whose maximum speed is 4x and then the output of "dvd+rw-mediainfo" tells that the "current write speed" is 4x.

As FuturePilot says, I want to reduce risk in writing iso files.

Thanks.

---

### Post by bingoUV on 2008-05-23
> **telko said:**
> 

I think that the DVD writer supports that speeds because I´ve tried to burn a DVD-RW whose maximum speed is 4x and then the output of "dvd+rw-mediainfo" tells that the "current write speed" is 4x.



Sorry, but I am unable to understand how this means that your DVD writer supports writing at 1x. Try 4x for DVD-RW, that seems to be supported from your above statement.

---

### Post by telko on 2008-05-23
Maybe I haven´t explained well myself.

I´ve been successful writing a DVD-RW at a speed of 4x. Therefore, I think I should be able to write a DVD-R at the same speed (maybe I´m wrong?)

Of course this doesn´t mean that my DVD writer supports speeds slower than 4x, but at least I think I should achieve that.

The point is what king of change must be done. As I said before, I think is about the driver, but I don´t know how to change drivers in Ubuntu.

Thanks again.

---

### Post by telko on 2008-05-28
Hi again.

I´ve also tried with k3b and the result has been the same. The drop down box to select the write speed only offers 4 alternatives: 6x, 8x, 12x and 16x.

Trying a DVD-RW whose maximum speed is 4x, the drop down box only offers 4x speed. And when I burn it it´s done at 4x.

Therefore, I don´t understand why I cannot choose 4x when writing a DVD-R whose maximum speed is 16x.

Any ideas?

---

