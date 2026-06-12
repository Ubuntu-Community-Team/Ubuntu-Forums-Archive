---
title: "nvidia-glx 686"
date: 2006-09-19
forum: General Help
---

### Post by JamesB on 2006-09-19
I have a similar problem to the K7 post about nvidia-glx being broken. I have everything running fine with kernel 2.6.15-23, but when I upgraded to 2.6.15-26 and -27 the nvidia module wasn't loaded AND the wireless network card dissappeared :confused: 
I've tried re-installing and all the other tips and tricks I could find. The only thing I can think of is that may be the resitricted package isn't as up-to-date as it should be as this has happen on 2 kernel upgrades](*,) 

Any help or ideas would be appreciated

---

### Post by Slychilde on 2006-09-19
Did you try

```
sudo apt-get install linux-restricted-modules-686
```

it worked for me, and both wireless and the nvidia card should be fixed by that, although I have heard before you may also have to recompile something (ndiswrapper?).

---

### Post by JamesB on 2006-09-19
> **Slychilde said:**
> Did you try

```
sudo apt-get install linux-restricted-modules-686
```

it worked for me, and both wireless and the nvidia card should be fixed by that, although I have heard before you may also have to recompile something (ndiswrapper?).

Thanx for the tip.
Already have installed, cae down with the upgade, haven't got ndiswrapper as the wireless card worked straight out the box with 2.6.15-23, but not even seen by later kernels??

---

### Post by Slychilde on 2006-09-19
Hmmm no, a newer kernel should have old + new stuff.  Maybe it misconfigured your computer?  I'm rather clueless about wireless still, so someone else will probably be much more help, but do you know what modules your old kernel was using for your wireless, maybe besides the restricted modules?  Do 

```
cd #home directory
lsmod > running_modules.txt
echo "End of kernel-23 module" >> running_modules.txt
```

in your current kernel.  Reboot to the 27 kernel and do

```
cd #home dir
lsmod >> running_modules.txt
```

Try to compare the two and see if there is a module missing or something.  That is the only idea I can think of having almost nil experience with wireless.  I know that's a decent way to troubleshoot if your ethernet isn't being detected and it was before.

---

