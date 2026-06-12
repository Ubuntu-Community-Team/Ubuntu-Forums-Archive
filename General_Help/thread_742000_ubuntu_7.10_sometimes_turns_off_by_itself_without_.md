---
title: "ubuntu 7.10 sometimes turns off by itself without any reason"
date: 2008-04-01
forum: General Help
---

### Post by kuisys on 2008-04-01
any advices?

---

### Post by stalkingwolf on 2008-04-01
a bit more information is needed.  To start with what are your system specs?

---

### Post by stefangr1 on 2008-04-01
And also: what exactly do you mean by "turns off". If it really turns of totally it is almost certainly a hardware issue, like extreme overheating.

---

### Post by kuisys on 2008-04-01
> **stefangr1 said:**
> And also: what exactly do you mean by "turns off". If it really turns of totally it is almost certainly a hardware issue, like extreme overheating.

I have conky installed I see my CPU is working fine and its temperature ir normal about 60C

yea it turn off totaly, sometimes computer turn off from 5 times to 15 times per day, some day compiuter works fine without shutting down... 

system spec? is this 1024 RAM 1.8ghz processor 80gb hdd? My computer HP dv4000. 

Sorry for my poor english speak.

---

### Post by dad311 on 2008-04-01
Bad power supply?  Over loaded power supply?

---

### Post by kuisys on 2008-04-01
no, at home where are 3 computers, 2 notebooks and 1 personal... all working fine. when my computer have win xp it works fine, without any turning off.. but ubuntu turns off by itself..

---

### Post by cdenley on 2008-04-01
If the systems simply powers off, I would say it's definitely a hardware issue. Does it go through the shutdown procedure, or is it like someone just pulled the plug? I would start swapping hardware with one of your working computers, starting with the power supply. Is the fan working on your power supply?

---

### Post by kuisys on 2008-04-01
> **cdenley said:**
> If the systems simply powers off, I would say it's definitely a hardware issue. Does it go through the shutdown procedure, or is it like someone just pulled the plug? I would start swapping hardware with one of your working computers, starting with the power supply. Is the fan working on your power supply?

ubuntu turn off like I go to System->ShutDown turn off like normal, not like I plug off power cabel... fan is working.

---

### Post by ikekrull on 2008-04-01
I've seen this on my machine.

 In my case it was leaky capacitors on the motherboard making voltages swing out of spec. 

However, it could be any number of things. Hardware is one possibility,but hardly a foregone conclusion, as ubuntu gutsy is known to be unstable on many systems, especially AMD64 based.

If there is no kernel panic, or any other messages wrtten to /var/log/kern.log, then you can't easily troubleshoot this at a software level. 

I would make a visual inspection of the motherboard, check for bulging or leaking capacitors - if they are present and you are under warranty get the board replaced - reseat any PCI cards and check temperature of components - overheating can cause spontaneous shutdowns. Run the memtest from the boot menu.

If your hardware seems good, and is rock-stable under windows, then its probably kernel 2.6.22 which, in my experience, is extremely unstable on AMD64 systems (due to my leaking caps i cant say for sure whether older 32 bit AMD CPUs and chipsets are just as flaky but i suspect this is the case). 

I have found that Gutsy is both a blessing and a curse, as it has lots of new features but the kernel has major issues with some classes of hardware. Your only paths to stability may be to either wait for hardy, install a hardy kernel (may cause additional problems), compile a new kernel yourself (maintainability nightmare) or just live with gutsy switching itself off randomly.

I can say my AMD64 box with hardy has not crashed once in the 2 days its been running, compared to gutsy which was unable to run for more than 2 hours at a stretch on the same machine.

You'll get no useful response from either ubuntu or kernel devs, as the kernel is not a bleeding-edge version, and ubuntu devs will simply advise you to wait for hardy.

---

### Post by dad311 on 2008-04-02
Is it going into sleep mode/ hibernate or does it turn off while your typing?

---

### Post by McMagic on 2008-04-03
I have an hp  dv8000, very similar pc with gutsy loaded and am having the same problem as him, it seems. Randomly, the machine will power down, as if i clicked the power button in the top right and selected "shutdown", however, i notice that when i boot back up, programs like word and firefox detect severed sessions, so they were not actually shut down correctly like in a normal system shutdown. I feel like this may be a heat failsafe because whenever this happens it seems like the processor area is extremely warm. Im considering buying a cooling pad to see if that addresses it. Anyone else with a dv*000 with some input as to what this is would be appreciated!

---

