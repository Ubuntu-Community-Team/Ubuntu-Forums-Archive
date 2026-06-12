---
title: "System becomes slower during use"
date: 2016-08-19
forum: General Help
---

### Post by dlalonde2 on 2016-08-19
I've used my Ubuntu machine to work (I'm a web programmer and I work on a remote server so, other than a text editor and browsers I don't use a lot of software).

After some hours I can feel it become a bit more sluggish. I've checked with my browsers (yeah Chrome and Firefox do tend to eat up your system) so I tried closing them and starting over. But the problem remains. I've opened top to check if I saw something but no.

On the exact same machine, with the same tools, that never happens. 

What could be causing this?

---

### Post by Rocket2DMn on 2016-08-19
If it's not the CPU that's being used up, then it must be something else.  As a developer, I'm sure this is obvious to you.  I assume you're not using up all your RAM and starting to swap to disk?  Maybe your disk (HDD or SSD) is the problem - is it full (perhaps getting clogged with log files)?  Both HDDs (classic spinning disks) and SSDs slow down as they approach capacity, and esp. older SSDs go bad after too many writes.

As with any debugging, we need to narrow the problem down to one (or possibly a few) components, and preferably be able to quantify the behavior or actually find warning/error messages in a console or log files.  Anything in the logs in /var/log look suspicious?  dmesg is always a good place to start.

---

### Post by dlalonde2 on 2016-08-19
> **Rocket2DMn said:**
> If it's not the CPU that's being used up, then it must be something else.  As a developer, I'm sure this is obvious to you.  I assume you're not using up all your RAM and starting to swap to disk?  Maybe your disk (HDD or SSD) is the problem - is it full (perhaps getting clogged with log files)?  Both HDDs (classic spinning disks) and SSDs slow down as they approach capacity, and esp. older SSDs go bad after too many writes.

As with any debugging, we need to narrow the problem down to one (or possibly a few) components, and preferably be able to quantify the behavior or actually find warning/error messages in a console or log files.  Anything in the logs in /var/log look suspicious?  dmesg is always a good place to start.

I have 4 GB or RAM but it's never used completely and I did modified the swapiness as well. But it's not full, I have loads of space on both my root and home folders. 

I'll look at the /var/log when I get home. I wonder if my graphics cards could be at fault although I don't see how. I know drivers have a hard time with it (I had to tweak my install so that it doesn't tear on Firefox and doesn't heat up during the day when the lid is closed). But it's a strange world when Windows 10 is snappier that Ubuntu! ;)

---

