---
title: "Stuck on Busy Box, lubuntu 15.04"
date: 2015-10-19
forum: General Help
---

### Post by matteo26 on 2015-10-19
Hello everybody, I hope this is the correct section. (I'm not really a new ubuntu user :cool:but it's the first time I write in this forum so excuse me for any mistake).

Once every two times I turn up my PC I get stuck on the black screen with this writing: :confused:

[B]BusyBox v1.22.1 (Ubuntu 1:1.22.0-9ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/B]

How can I shutdown correctly or load the OS (lubuntu)? Any hint?
I tried some commands in similar posts but nothing really works.
Thanks in advance ):P

---

### Post by ian-weisser on 2015-10-19
Are you saying that about 50% of the time, your system boots properly? And about 50% of the time you drop to the initramfs prompt?
Have you seen any pattern?

The initramfs prompt usually has nothing to do with an unclean shutdown.
The error messages before 'BusyBox' would help a lot. There are many possible causes for the symptom you describe, and those error messages would help to narrow the possibilities.

If it's intermittent and unpredictable, and the error messages indicate I/O errors or mounting errors, look toward hardware failure - failing hard drive, or perhaps failing power supply..

---

### Post by matteo26 on 2015-10-20
Well, this week it's being like this, it's happening very often (maybe only 30%).
As far as I noticed,  this is the first message, no errors before: the motherboard screen appears, then the screen is black and then it enters the busybox;
at this point I'd like to exit, but I don't know any useful command (shutdown now, sudo shutdown now, they don't work), so the only way I know is to press the power button and I'm afraid I'm damaging the hardware even more.

So my question is: how to shutdown the computer without damaging it? or to load the OS from the busybox?
In other words, is there any command to exit the busybox without touching the power button?

---

