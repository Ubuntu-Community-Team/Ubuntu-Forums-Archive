---
title: "Random rebootings... kernel problem?"
date: 2021-08-26
forum: General Help
---

### Post by alro7779 on 2021-08-26
Hi, guys!

I'm having this issue... from time to time my machine reboots all of a sudden. Since I got no warning or error messages, I don't know if it exists a log so I can look for the culprit. However, I think the problem might be with the liquorix kernel I installed a time ago. Where should I look, guys?

By the way, that liquorix kernel I'm using was supposed to give me better performance on playing games. Is it true?

-Alex.

---

### Post by mikewhatever on 2021-08-26
One way to verify your suspicion is to install the default Ubuntu kernel from the repositories, and uninstall whatever you have. If reboots stop, then you might be right. Random reboots could also be the cause of faulty hardware - RAM, CPU, PSU, etc.

---

### Post by alro7779 on 2021-08-26
Thanks for your reply, Mike!
I suppose we, Linux users, have a tool for testing faulty hardware, right? I know Memtest86+ for memory testing, but for CPU, PSU or whatever hardware we have, do you know some?

---

### Post by mikewhatever on 2021-08-27
There are software tools like Memtest or CPU stress programs, but their abilities are limited. For example, memtest dosn't tell if errors are related to a RAM stick, the slot, or the buss, so you need to crosstest with another PC, or try to eliminate options, which is rather tedious.
However it seems irrelevant in your case, at least utill the default kernel is tested.

---

