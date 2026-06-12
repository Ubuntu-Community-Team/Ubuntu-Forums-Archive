---
title: "Update/Synaptic/Apt-Get Crashes!!"
date: 2007-03-03
forum: General Help
---

### Post by DaRush on 2007-03-03
Ubuntu 6.10, Amd 64 on Compaq Pressario V200 laptop.

Had to Install a custom kernel 19.1 among other things, in order to get my broadcom wifi to work.
That ran fine, but I didn't update the kernel packages for fear of troubleshooting my wifi again.  Worked like this for more than a month (including updates and synaptic manager), but today I noticed that my update icon is no longer showing.  When I run add-remove programs, the window loads for a second then just shuts off by itself.  I try running Synaptic package manager, that prompts me for a password, then just closes by itself too.  Finallly I ran sudo apt-get upgrade, this produced:
Segmentation faultsts... 0%

I did not install anything new on the computer, just mildly used it for typing, etc.  This just seems to have stopped working by itself!

this is the relevant system log that I think has something do with the problem...
Mar  3 18:17:02 vlady-laptop kernel: [   76.031466] gnome-app-insta[4784]: segfault at 0000000000000000 rip 00002ae72bfa30f0 rsp 00007fff7f134848 error 4
Mar  3 18:25:40 vlady-laptop kernel: [  339.297670] synaptic[5156]: segfault at 0000000000000000 rip 00002b26205700f0 rsp 00007fff8d6dd9a8 error 4
Mar  3 18:32:56 vlady-laptop kernel: [  557.427183] apt-get[5502]: segfault at 0000000000000000 rip 00002ae98024c0f0 rsp 00007fff2b051c58 error 4
Mar  3 18:33:14 vlady-laptop kernel: [  566.568350] apt-get[5519]: segfault at 0000000000000000 rip 00002b053a7d50f0 rsp 00007fff70ac7338 error 4
Mar  3 18:34:48 vlady-laptop kernel: [  613.542225] gnome-app-insta[5577]: segfault at 0000000000000000 rip 00002b535ec6a0f0 rsp 00007fff4c46bb78 error 4
Mar  3 18:35:01 vlady-laptop kernel: [  620.750975] python[5606]: segfault at 0000000000000000 rip 00002b6ab93150f0 rsp 00007ffff1dc4bc8 error 4
Mar  3 18:35:02 vlady-laptop kernel: [  620.983935] synaptic[5605]: segfault at 0000000000000000 rip 00002b1aa92d80f0 rsp 00007fff04973758 error 4

I would appreciate any help... 
Thanks

---

