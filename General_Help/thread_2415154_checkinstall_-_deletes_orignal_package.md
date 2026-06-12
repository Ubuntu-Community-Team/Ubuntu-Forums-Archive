---
title: "checkinstall - deletes orignal package"
date: 2019-03-21
forum: General Help
---

### Post by anneranch on 2019-03-21
I just successfully used "checkinstall" to build "bluez" package for specific architecture. 
> 
jim@jim-desktop:~$ sudo dpkg -l "bluez"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  bluez:armhf    5.50-1       armhf        bluez-5.50



Now I no longer have the original "bluez" package on my system. 

Since I am basically using "bluez" library to code in C++ I wonder how I could prevent "checkinstall" to remove the original "bluez" package - for X86 architecture. 

Ideally I like to have both architectures X86 and armhf bluez packages installed, hence be able to link to the desired library as necessary. 
Any idea ?

Thanks 
Cheers

---

