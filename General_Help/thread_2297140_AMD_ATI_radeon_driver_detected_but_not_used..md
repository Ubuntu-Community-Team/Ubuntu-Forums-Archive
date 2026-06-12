---
title: "AMD ATI radeon driver detected but not used."
date: 2015-10-01
forum: General Help
---

### Post by amit_sharma5 on 2015-10-01
I know there are many threads like this, but none were able to solve this problem of mine.
So, I bought a new laptop, lenovo G50-70 59-422418. It has one Intel integrated GPU and one AMD ATI one ([COLOR=#111111][FONT=Arial]2GB ATI JET LE R5 M230 DDR3L[/FONT][/COLOR]).

So I opened the additional drivers, and selected the proprietary driver and installed it. Now when I checked, ubuntu is not using the AMD GPU, instead it is using intel one (as showing in system settings).

So my question is simple, how could I make my system to use AMD graphics card.

More Details(Please let me know if any more details are needed):
I typed the following command and the output is as follows:
```
root@G5070:~# lspci -nn |egrep "VGA|Display" 
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun LE [Radeon HD 8550M / R5 M230] [1002:666f] (rev ff)


```

```
root@G5070:~# lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b) (prog-if 00 [VGA controller])


```


NOTE: in the additional drivers, it's showing under amd card that: "This device is using an alternative driver."
[http://drive.google.com/file/d/0BwiiBhoUrv3fUmFzV1A2c3IwNWs/view?usp=sharing](http://drive.google.com/file/d/0BwiiBhoUrv3fUmFzV1A2c3IwNWs/view?usp=sharing) (Image link of Additional Drivers)

Thanks.

---

### Post by QIII on 2015-10-01
The alternative driver is the AMD fglrx driver, which is the one you want.

When you installed fglrx-updates, did you do 

```
sudo amdconfig --initial 
```?

If not, do so now to be sure.

Since about 14.04.3 or 14.10, the problem of switching with an AMD/Intel hybrid graphics system has largely been fixed -- provided that your system is muxless.  That means that the Intel graphics adapter does not act as a multiplexer for both GPUs.

If that is the case and your AMD adapter is properly initialized, the Catalyst Control Center will let you switch between the two.  It is not on-the-fly like in Windows.  You have to reboot.

If your system is muxed, you'll have to use a different approach.

---

### Post by amit_sharma5 on 2015-10-01
I don't know if my system is muxed or not. If there's any way to find it, please direct me to that direction.
Apart from that, I didn't did that amdconfig when I installed my driver, but now, when I tried it, it's giving me this error: "amdconfig: No supported adapters detected"
Thanks.

---

### Post by amit_sharma5 on 2015-10-02
I don't know why, but it's solved now.
What I did was, first switch to the x.org driver, then restart, then installed the fglrx one (without updates). and used the command "[COLOR=#000000][FONT=Ubuntu Mono]sudo amdconfig --initial".
Thanks[/FONT][/COLOR][COLOR=#000000] [/COLOR]QIII..=d>=d>=d>

---

