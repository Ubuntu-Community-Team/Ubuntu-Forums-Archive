---
title: "Strange keyboard issue on Ubutu server"
date: 2022-07-07
forum: General Help
---

### Post by kentaylor2525 on 2022-07-07
I installed Ubuntu server 22.04 -  32 bit on a Raspberry Pi 3B+.  The initial user "ubuntu"  can log in fine at the console and things seem to work OK.  I ran  Raspi-Config and found it not present. Strange but easy enough to  install. I enabled SSH and connected to the Pi from a CentOS 7  workstation. Things worked as expected.  

I created another user ```
useradd ken --create-home -g sudo; sudo passwd ken
```

ken can also login at the console or via ssh. So far, so good. However,  when logged in as ken I find that the arrow keys on the keyboard -  located between the main keys and the number pad - do not work.  Up  arrow produces  ^[[A right arrow produces  ^[[C etc. This happens both  at the console and over ssh. 

I have used raspi-config to examine the localization of the keyboard  both when logged in as ubuntu and as ken. I find the keyboard to be  correctly specified as Generic 105-key PC; English (US); English (US).

Why is my newly created user not using the default keyboard?  How can I correct the situation? This is a new one on me.

TIA,

Ken

---

