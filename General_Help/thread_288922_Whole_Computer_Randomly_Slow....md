---
title: "Whole Computer Randomly Slow..."
date: 2006-10-30
forum: General Help
---

### Post by fazza on 2006-10-30
Our computer seems to work fine most of the time, but every now and then it just goes really, really slow. Sometimes I've waited 2-3 mins for evolution to open; sometimes I tell a program to close, and it just sits there. Then a window comes up saying 'Program not responding. Force Quit?' or something like that. So I click 'Yes' and still nothing happens. Occasionally, but more and more frequently, I click 'shutdown' and nothing happens atall. And it boots up mighty slow, especially when it gets to the bit where it says scanning the windows partition. Can anyone help? I put ubuntu on our pc because my parents were getting annoyed with Windows; now they're annoyed with this because it keeps slowing down and crashing! Any replies would be appreciated!

---

### Post by cborner on 2006-10-30
Fazza,

Could you provide the specs for your computer?

System Type: Desktop/Laptop/Server?  Make and model would be helpful if it isn't a home-built system.
CPU: Make and speed
Memory: How much and type (if known)
Hard Drive(s): Number of drives, make, model, and size.

---

### Post by fazza on 2006-10-30
Eeeeeeerrrrrrrr...
Desktop.
Pentium III (not sure what speed).
383MB RAM (one MB died!).
Quantum Bigfoot 6GB (Win98 ) & (I think the other one's a Seagate) 80GB.
That's all I know

---

### Post by cborner on 2006-10-30
Okay, with time and use, any PC is going to slow down somewhat.

Also, newer doesn't always mean 'faster' when it comes to software.

Random slowness on older machines, especially ones running lots of processes, is to be expected.  It's likely that you're 'eating' most of your physical memory and operating off swap space.

What's happening then is that the machine has to swap a bunch of stuff out of memory to the swap partition, then swap the necessary data back into memory.  Depending on the data involved, this could take a bit.

If the app is expecting to be fed data within a certain window of time, it's going to give you a 'not responding'.

Oh, and one final dumb question.  Ubuntu is installed to your hard drive right?  You're not running it off the LiveCD?

---

### Post by fazza on 2006-10-30
yah... dumb question! ;)
ta for info

---

### Post by fazza on 2006-10-30
would there be anything i could do to speed it up then, or not?

---

