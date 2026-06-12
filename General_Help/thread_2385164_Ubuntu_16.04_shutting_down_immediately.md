---
title: "Ubuntu 16.04 shutting down immediately"
date: 2018-02-17
forum: General Help
---

### Post by g.oler on 2018-02-17
Hello, my laptop shuts down in less than s minute or within seconds. It doesnt switch off until the moment I put the password to start it up. I also suspect the fan is not moving I have tried blowing it up but there is no change, please help.

---

### Post by TheFu on 2018-02-17
If I "tried blowing it up" on a laptop, I'd expect it never would work again.  Perhaps we have a misunderstanding?

---

### Post by deadflowr on 2018-02-17
There is not enough information at all.
It would be helpful to know something, anything, about the hardware.
Like make and model.
Simple things to get the ball rolling.

---

### Post by g.oler on 2018-02-19
Its HP probook 4520s, core i3, 32bt, I feel its over heating though it always does over heat and blow hot air but it doesnt switch off.Now I feel the fan is not moving and it switches on for about 1 minute

---

### Post by TheFu on 2018-02-19
What is "32bt"?
I have an i3 netbook that doesn't have the fan on all the time, but it has a heat pipe for cooling.

I'd make a new live-boot flash drive and boot off that to see if the problem is with the install or not.  If it runs fine that way, it is an install issue, not the HW.  Right?

---

### Post by g.oler on 2018-02-19
I meant blowing up for dust. blowing dust away especially at the fan

---

### Post by g.oler on 2018-02-19
I meant 32bit, may I know exactly to do the live-boot flash drive.How to do the booting, am not a pro in this excuse some of my reporting haha

---

### Post by g.oler on 2018-02-19
I have tried live booting into flash drive but it switches off before the process is complete

---

### Post by mörgæs on 2018-02-19
> **g.oler said:**
> Now I feel the fan is not moving

When the computer is turned on or off? 

Does the fan rotate freely if you push it with a piece of wire, toothpick or similar?

---

### Post by TheFu on 2018-02-19
An i3 should just slow down when it gets hot and only shut off when burning. The CPU will not be damaged.
Check that the heat management for the entire system is connected correctly and working - CPU heatsink, paste, and fan(s).

Also, I'd pull the drive, connect it to a different machine and look over the log files. Any CPU thermal issues would definitely be in the logs.  They look like this ... let me grab some:
```
$ journalctl -k -p err
-- Logs begin at Mon 2018-02-19 05:30:10 EST, end at Mon 2018-02-19 13:26:24 EST
Feb 19 05:51:45 hadar kernel: CPU0: Core temperature above threshold, cpu clock 
Feb 19 05:51:45 hadar kernel: CPU4: Core temperature above threshold, cpu clock 
Feb 19 06:01:45 hadar kernel: CPU4: Core temperature above threshold, cpu clock 
Feb 19 06:06:45 hadar kernel: CPU0: Core temperature above threshold, cpu clock 
Feb 19 06:06:45 hadar kernel: CPU4: Core temperature above threshold, cpu clock
```
My "hadar" machine is a 2009-ish Core i7 and has cooling issues too, but it doesn't shut down.  You can use a live-boot on a different machine with journalctl --directory to specify the location of the log files on the disk.

---

### Post by g.oler on 2018-02-19
no it doesn't, though there is sound that comes from the area as if the fan is blowing but there is no air blown out at all as usual. Thinking maybe its the processor sound.

---

### Post by mörgæs on 2018-02-20
> **g.oler said:**
> Thinking maybe its the processor sound.

A processor has no moving parts and makes no sound. 

This thread is getting too weird for me but you could try responding to TheFu's post.

---

### Post by g.oler on 2018-02-20
The fan does not turn, I have tried it with a toothpick

---

