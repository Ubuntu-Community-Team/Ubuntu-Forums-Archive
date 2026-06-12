---
title: "Freezing problems in Ubuntu 20.04 (and Mint)"
date: 2020-12-09
forum: General Help
---

### Post by kerburettor on 2020-12-09
Hi,

I've had freezing issues for several weeks already. I've been using Ubuntu 20.04.1 since its inception back in April/May 2020 without notable errors but since two/three weeks ago I started noticing a strange behavior on my machine: It would start freezing every now and then, seemingly randomly (I tried to correlate that behavior with the use of a particular software; there doesn’t seem to be any), and the machine soon restarts. Crashes happen inevitably when I’m using Linux (I had Ubuntu installed in dual-boot alongside Windows and the latter works just fine – never crashes) but I just can’t predict when they’re going to happen. The problem starts with my peripherals not working anymore (keyboard and mouse stop working) and after about 20 seconds, the computer automatically restarts.  
 
 
 What I tried:  
 
 
 1) Hard rebooting + capacitor discharging. Discharging static electricity seems to help a little bit when I’m trapped in an infinite cycle of “crashing-restarting-crashing-restarting...”, but the problem will happen again eventually.
 2) Checking /var/log/syslog. Did not understand what was written inside but there doesn’t seem to be any incriminating entry when a crash happens.
 3) Updating and upgrading. When I was using Ubuntu, I used to have ppa issues and some error messages possibly due to repositories I added, but now with Mint these commands ran smoothly.
 4) Uninstalling amdgpu, but I never really managed to do so cleanly because of point 3)
 5) This evening I deleted my root partition (Ubuntu) and replaced it with a Mint distribution. I’ve been having several crashes until now, so this doesn’t seem to be an OS-related issue?
 
 
 However I get these messages after choosing “Mint – MATE” in the GRUB (see picture). Does this mean I’ve got hardware issues?  
 
 
 Thanks
  [IMG]https://i.ibb.co/h8SLJc6/20201209-223143-0.jpg[/IMG]

---

### Post by Dennis N on 2020-12-09
It's a hardware problem. Google "mce error" to see articles giving some possible causes and effects. The effects can include freezing.

I have these every start up on one of our computers, but never any noticable effects, so I just ignore.

```
dmn@Tyana:~$ journalctl -b | grep mce
Dec 09 14:40:48 Tyana kernel: mce: CPU0: Thermal monitoring enabled (TM1)
Dec 09 14:40:48 Tyana kernel: mce: [Hardware Error]: Machine check events logged
Dec 09 14:40:48 Tyana kernel: mce: [Hardware Error]: CPU 0: Machine Check: 0 Bank 7: ae00000000801136
Dec 09 14:40:48 Tyana kernel: mce: [Hardware Error]: TSC 0 ADDR 8be6c800 MISC 70e0000086 
Dec 09 14:40:48 Tyana kernel: mce: [Hardware Error]: PROCESSOR 0:906eb TIME 1607550045 SOCKET 0 APIC 0 microcode ca
Dec 09 14:40:48 Tyana kernel: mce: Using 10 MCE banks
```

These messages are seen only in the journal in my system, not on the console.

---

