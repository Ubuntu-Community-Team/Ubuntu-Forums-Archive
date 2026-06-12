---
title: "Ran autoclean &amp; autoremove and now won't boot (16.04)"
date: 2017-09-27
forum: General Help
---

### Post by 1005703 on 2017-09-27
[FONT=arial]I was getting a low disk space message ("The volume boot has only _ bytes disk space remaining"), so I ran the following command:
[/FONT][FONT=arial black][FONT=system][FONT=arial]sudo apt-get autoclean && sudo apt-get autoremove

Now my laptop won't boot, and I get this screen (see attached image). The text isn't even complete, and it runs of the side of the screen.

Please help, this is my work computer and I need to get it back up and running ASAP. Many thanks in advance[/FONT].[/FONT]
[/FONT]

---

### Post by tony-rosmaninho on 2017-09-28
Please try to reboot system using an holder kernel, in Expert Setup.....

---

### Post by tony-rosmaninho on 2017-09-28
then try to do this:

```
**dpkg --configure -a**
```
```
**sudo apt-get install -f**
```

i guess it will solve

---

### Post by 1005703 on 2017-09-28
Thank you, Tony - I figured this out myself in the end. Panic over.

---

### Post by HermanAB on 2017-09-28
If you need to save space, then it is better to use deduplication than automatically deleting goodness knows what...

I made this little script for my Fedora system.  Ubuntu should be similar:
#! /bin/bash
# Use the script findup, part of fslint package
# to convert duplicate files into hard links.
sh /usr/share/fslint/fslint/findup -m /home/herman/Data

It can save hundreds of megabytes of space.

---

### Post by tony-rosmaninho on 2017-09-28
> **1005703 said:**
> Thank you, Tony - I figured this out myself in the end. Panic over.


Hehe,

I'm not an Linux Expert, but i already learned to be calm.... forum's like this are crucial, and we have here a lot of experts, with time and calm, they help us to solve the problems.


But I understand you, sometimes we don't have time :D

---

### Post by ajgreeny on 2017-09-28
Great news, and well done for figuring this out!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

