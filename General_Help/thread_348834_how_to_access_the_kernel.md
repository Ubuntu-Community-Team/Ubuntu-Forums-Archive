---
title: "how to access the kernel"
date: 2007-01-29
forum: General Help
---

### Post by burmanabhay88 on 2007-01-29
i'm kinda of new to linux. i have to do shell programming later. can anyone please tell me any of these things.
1. what it kernel
2. how to access it
3. where is shell programming done????
please do help me out????

---

### Post by Ramses de Norre on 2007-01-29
The kernel is a part of your OS, it's the program that handles memory allocation, hardware interfaces, ... It's a part of every OS and thus windows has a kernel too (ntoskrnl I think it is).
You can't "access" it because it isn't something "accessible" it's just a piece of code like a video driver or something.
For shell scripting: basically it's writing commands in a text file, marking the file as executable and opening it.
You're best bet is to search for a tutorial online about shell scripting.

---

### Post by az on 2007-01-29
> **burmanabhay88 said:**
> i'm kinda of new to linux. i have to do shell programming later. can anyone please tell me any of these things.
1. what it kernel
2. how to access it
3. where is shell programming done????
please do help me out????

1.  Already answered.  But to add more details, the kernel is loaded into memory by the bootloarder.  The kernel image is in /boot. 
2.  What exactly do you mean?  You can read a number of kernel values in /proc.  You can write to some of them and have an effect on the kernel.  You can also read the logs from the kernel activity in /var/log/
3.  A shell script is a text file.  You write the file and then you run it.  You can access the command line by opening a terminal (Applications - Accessories - Ternimal) or by using a virtual console (CTRL-ALT-F1 and use CTRL-ALT-F7 to get back.

---

