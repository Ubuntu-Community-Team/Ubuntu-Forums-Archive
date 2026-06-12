---
title: "Overclocking CPU in 14.04"
date: 2014-07-25
forum: General Help
---

### Post by larry23 on 2014-07-25
Hello,

I recently purchased the Pentium G3258 planning on overclocking but I'm having some trouble.

I've got a GA-Z97-Gaming 5 MB that did not support overclocking of the G3258 until a recent BIOS update which has been installed.
Linux kernel is 3.13.0-32

The UEFI BIOS shows the clock speed as the updated value but when I boot up into linux it doesn't appear to take effect. These values shown below ARE THE SAME whether i'm overclocked to 4.2GHz or at the stock 3.2GHz.

```
sedna@sedna:~$ sudo lshw -c cpu | grep capacity
       capacity: 3800MHz
sedna@sedna:~$ sudo lshw -c cpu | grep capacity
       capacity: 3800MHz
sedna@sedna:~$ sudo dmidecode -t processor | grep Speed
    Max Speed: 3800 MHz
    Current Speed: 3200 MHz
sedna@sedna:~$ cat /proc/cpuinfo |grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 800.000

```

I understand that the last command's return is due to throttling. But:

1) Max speed should be adjusted based on my overclocked value, correct?
2) current speed *may happen to be* 3200 MHz at the specific instance the command is run but even under max load it remains at 3200 MHz.

I couldn't find anything related to the 3.13 kernel, but I read that past kernels had trouble displaying the updated values. However, I don't believe this is the case since the cpu temp didn't jump up at all going from 3.2 to 4.2 and the performance did not increase.

Is there anything that needs to be done to the OS to 'unlock' the CPU? Should I just try c2ctl?

Thanks

---

### Post by 5mZKCMUmw1Le on 2014-08-03
Hi,

I have the exact same setup and exact same problem.

Were you able to solve this?

My hypothesis is that there is some dynamic CPU frequency scaling is bugged and overriding the BIOS.

---

### Post by iconpart on 2014-10-19
The command lshw doesn't give the cpu speed, only what it is capable of. Instead, use :
   
```
paul@Pauls-box:~$ more /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 58
model name    : Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
stepping    : 9
microcode    : 0x17
cpu MHz        : 1600.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
```


to see the current speed. This may keep changing if your system autoadjusts cpu speed.

---

