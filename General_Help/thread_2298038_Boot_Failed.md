---
title: "Boot Failed"
date: 2015-10-08
forum: General Help
---

### Post by chemist931 on 2015-10-08
On my laptop running 15.04, whenever I connect to a specific network, my laptop freezes and the caps lock light starts blinking.  This has been happening ever since I first started trying to connect to this network.  The problem is that the only way to be rescued is to hardstop it.  Usually this is okay (but annoying), but this time it messed something up when I tried to reboot.  I am not very skilled in this part of many operating systems :(.

[http://picpaste.com/unnamed-B4DlaolA.jpg](http://picpaste.com/unnamed-B4DlaolA.jpg)

---

### Post by tgalati4 on 2015-10-08
Could be a hardware vs software wireless encryption problem.  The flashing caps and numlock key indicates a Kernel Panic--which means your system has locked up hard.  But you knew that.

What wireless card are you using?  Open a terminal, and post the output of:

```
lspci | grep Network
```

Don't use the power button to shutdown, that can mess up your hard disk.  Use the Magic Keys first, then use the power button, but only as a last resort.

Magic Keys (follow the instructions at the bottom of this link):  [http://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop](http://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop)

---

### Post by chemist931 on 2015-10-08
Thanks for the help, but I can't actually access a terminal, even tty1. The very last bit of output on the screen is the last one it gives, so no terminal besides the minimal init one.

---

### Post by QIII on 2015-10-08
Hello!

Do you know how to get to the command line from recovery mode?  If so, try a previous kernel in recovery mode, execute that command and snap a picture with your cell phone.  Post that back here.

---

### Post by chemist931 on 2015-10-09
I can't get to a terminal besides initramfs! I've tried everything to try to get somewhere where I can enter that command, and the only other kernels I can choose are the default one and upstart, both of which don't work.

---

### Post by tgalati4 on 2015-10-10
Make a LiveUSB of 14.04 for troubleshooting.  Boot from that so we can repair the damage to your hard disk.  How many times did you power off with this network problem?

---

### Post by chemist931 on 2015-10-20
Okay, I fixed the booting issue (clean install).  I'll start another thread for the kernel panic problem.

---

