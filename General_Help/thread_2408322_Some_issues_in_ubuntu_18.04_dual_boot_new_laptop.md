---
title: "Some issues in ubuntu 18.04 dual boot new laptop"
date: 2018-12-17
forum: General Help
---

### Post by chaostheory1000 on 2018-12-17
Hi All,

I have recently upgraded my laptop and did a dual boot setup using Windows 10 and Ubuntu 18.04.

Afterwards I am having a few issues where I need help.

I consider myself as a novice so it is quite likely I made some errors while installing (my previous laptop from 2010 also had dual boot Win 7 and Ubuntu 16.04 done by  me on similar lines, however, that was MBR and old BIOS, new laptop is GPT and UEFI which were new to me, hence errors might have crept in).

1. The startup time for ubuntu is around 50 sec. It is a bit disappointing as on my old laptop, the startup time used to be 35 seconds. (The old laptop had i3 processor, 4 GB RAM whereas new has i5 processor 8G RAM). I can copy the output for > systemd-analyze blame in next reply or on pastebin according to what you people suggest.

2.  I find that my USB external Hard drive is not working in new laptop but it is working fine in old laptop. When inserted, the indication light of External Hard Drive lights up continuously with some vibration/sound in hard drive but absolutely no recognition etc in laptop. I tried going to disk manager, system components,etc but it is not being detected. This is same in both Windows and Ubuntu so I suspect might be some BIOS issues.


My Methodology to install Windows 10  and Ubuntu 18.04:

[LIST]
[*]Installed Win 10 in completely normal way, just ensured about UEFI and GPT. 
[*]Using windows disk manager, shrank the original partition to 220 GB NTFS, Created new Partition of 550 GB NTFS for data to be shared between Win and Ubuntu, then blank space of around 230 GB to be used to install Ubuntu. 
[*]I did not touch any partitions created by Win 10 setup. 
[*]Installed Ubuntu 18.04 using / of 60 GB and /home of 170 GB both ext4 and around 9 GB for swap. 
[*]Went to bios and set ubuntu in boot order. 
[*]Then as WiFi was not working searched for a solution and now it is working. 
[/LIST]


Thanks.

---

