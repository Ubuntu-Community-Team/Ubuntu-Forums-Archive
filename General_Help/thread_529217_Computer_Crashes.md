---
title: "Computer Crashes"
date: 2007-08-18
forum: General Help
---

### Post by yataf on 2007-08-18
I have infrequent computer crashes in Ubuntu, same with in Windows Xp too. I'm thinking it is a power supply problem rather than over heating because I checked the cpu temps after a crash and it doesn't seem to be very high. I suspect it is a power supply problem but I'm not too sure on how to find out for sure. I bought a power supply before and tested it in Windows and I still had a crash. Could the graphics card be over heating?

---

### Post by steveneddy on 2007-08-18
Sounds like the memory to me.

Run the memcheck from the live cd.

Let it run for a while, like an hour or two.

---

### Post by heimo on 2007-08-18
> **yataf said:**
> I have infrequent computer crashes in Ubuntu, same with in Windows Xp too. I'm thinking it is a power supply problem rather than over heating because I checked the cpu temps after a crash and it doesn't seem to be very high. I suspect it is a power supply problem but I'm not too sure on how to find out for sure. I bought a power supply before and tested it in Windows and I still had a crash. Could the graphics card be over heating?

One thing you should check is possibly faulty memory. Run memtest (a choce in Grub boot menu) for couple hours. If possible, try with less memory installed.

---

### Post by yataf on 2007-08-19
I remember I ran memtest before and it came up with nothing, I guess I'll run it again tomorrow. I will post my results.

---

### Post by yataf on 2007-08-19
11 hours of memtest, no errors so it's not the ram.

---

### Post by arsenic23 on 2007-08-19
How old is your machine?  What's it made out of? (lspci if you don't know off the top of your head.)  If it's an older machine, do you still have any 40 pin IDE cables in use?  What PSU are you using exactly?  How long have you had the problem?  When windows was crashing did it give you any errors before, durring, or after the crash?

---

### Post by yataf on 2007-08-19
BSOD, with a hardware error. All I have is a 6600 Gt, 160 GB hard drive, dvd writer, cd writer, floppy drive, and a network card. If anything I also suspect the network card but it's just a hunch.

---

### Post by arsenic23 on 2007-08-19
Don't remember the hardware error ?  Knowing it would really help.
Also what type of CPU (socket type and brand)?

If you think it might be the network card one thing you can try is to disable the wakeonlan setting in your bios.  It's a long shot but if it's set to on and you don't use it, it won't hurt to turn it off.

-----------------------------------
EDIT:

Also, to anyone who knows:  Does memtest check the video cards RAM ?  I don't use memtest myself when it comes to testing memory so I'm not familiar with it.

---

### Post by yataf on 2007-08-19
No, it just said a hard ware error and I should contact people. I have a 3.00 Ghz Pentium 4 prescott socket 478. Or it could be the addition of the network card using too much power, but I doubt it uses much. I have a 350 watt supply so it's kinda low.

---

### Post by arsenic23 on 2007-08-19
Ok, here's some more things you can test:

Open your case and look at the group of large transistors right next to your CPU.  If they are swelling on the tops then you definately have bad power or have experienced a large surge in the past.

Take a look at your IDE cables, there are two basic kinds - ones with 80 little ribs and ones with 40.  Now the one going to your hard drive should not be a 40pin cable, but sometimes companies still use the 40 pin cables for the optical drives.  It's not likely, but I've seen the older 40 pin cables go bad and cause all kinds of problems.  If you have a 40 pin cable in your case you can feel it to see if it's a little stiff.  If it feels stiff it would not hurt to replace it.  (They cost almost nothing.)

If your really serious about testing your power and your not familiar or comfident enough to use a volt meter manually, then you may consider buying this or something like it:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16899705003](http://www.newegg.com/Product/Product.aspx?Item=N82E16899705003)

---

