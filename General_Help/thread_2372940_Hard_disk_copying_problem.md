---
title: "Hard disk copying problem"
date: 2017-09-30
forum: General Help
---

### Post by ra7411 on 2017-09-30
[COLOR=#000000][FONT=Arial] I ran into an aggravating problem yesterday.   I had a new 2 terabyte hard disk that I wanted to copy about 620 GB onto. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Instead of copying everything,  repeated attempts using Nemo, Nautilus and even Grsync would end with most of the 620 gigs not being copied onto the new disc.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial] The reason that kept coming up was that the designation of the new disc apparently kept changing from read/write to read only.   Several times, I tried using chown  in the terminal and then resetting permissions in the properties tabs, and that would work for a short time and then the whole  read only problem would occur again.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Finally, I decided to see if my other Ubuntu 1604 install on the machine would work any  better.  I booted into it,  and used Grsync to do the copy job with no further problems. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have no idea why things went haywire other than  it's apparently associated with an O/S problem In my main install.  [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Any ideas?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by TheFu on 2017-09-30
How is the new disk connected to the problem system?  USB?  If so, try a different USB port, different cable, different enclosure.  If SATA, then try a different SATA port, different SATA cable, different power connections.

Also, looking at **dmesg** might provide some clues.

It is very unlikely that it is an OS issue. It is most likely either a physical hardware issue or a disk issue - consider taking it back and getting another.

---

### Post by ra7411 on 2017-09-30
>[COLOR=#000000]How is the new disk connected to the problem system?<

It's a SATA 3.5" HD in a desktop machine, standard hookup. The HD passes SMART tests, and as I posted, Grsync running on my alterante o/s install copied the 620gbs just fine. I've run some vids off it and it went ok. The machine now has 3 Hitachi 2tb HDs.

That's all I know.[/COLOR]

---

### Post by TheFu on 2017-09-30
sorry - I took *alternate install* to mean different PC.

I'd look for kernel issue reports and still look at dmesg output.

If you are using a non-standard file system, like btrfs, then that could be the issue too.  The different OSes probably use different libraries for the file system access.

---

### Post by HermanAB on 2017-10-01
In my experience it is a power supply issue most likely.

Anyhoo, the advantage of rsync (or grsync) is that the files are guaranteed copied correctly, so when copying massive amounts of data, it is pretty much mandatory.

---

