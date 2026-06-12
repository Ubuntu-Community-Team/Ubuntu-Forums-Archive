---
title: "Multiple programmmes crashing frequently"
date: 2015-05-06
forum: General Help
---

### Post by lads on 2015-05-06
About a week ago Firefox started crashing very frequently, 20 to 30 times a day. On random pages, doing random things, sometimes even when it is minimised. I ran the updates and checked the system for malware with rkhunter. After trying that and a few more suggestions from the Firefox help pages without visible results, I submitted [a report to the Firefox Forum]("https://support.mozilla.org/en-US/questions/1058754").

Meanwhile other programmes started crashing randomly: Rhythmbox, ownCloud client, Dropbox, etc. Other programmes such as Eclipse or pgAdmin started hanging occasionally.

Some python scripts on which I am working right now are crashing with exceptions issued by malloc and free e.g.:

    *** Error in/usr/bin/python2.7': free(): invalid next size (normal): 0x0000000001fe7fc0 ***

I ran the memory test and it reported a few errors. I got the memory chips replaced and now the memory test passes without reporting errors. However, applications keep on crashing.

This morning the hard drive was swapped into another laptop with the same mother-board and the symptoms are exactly the same, with multiple applications crashing and exceptions on memory access. Thus an hardware issue is discarded for the moment.

What else can be causing these problems? Any suggestions on what I may do to track it down?

Thank you.

---

### Post by dino99 on 2015-05-06
start cleaning the system (clean, autoclean, autoremove, gtkorphan), then deactivate third party repos (ppa, ...) and possibly downgrading some packages if you have some untrusted upgrades.

---

