---
title: "no response after suspend  in ubuntu 7.04"
date: 2007-09-27
forum: General Help
---

### Post by RockyRock on 2007-09-27
Hi, I installed a windows xp + ubuntu 7.04 64bit dual boot system on a Desktop with AMD 64 x2. 

The ubuntu works fine until last night when I pressed the "suspend" button instead of "shut down" to have fun. Then, immediately the LCD has no signal, and the keyboard has no response at all. But the power light is on and cpu fan was still making noise.   It seems very similar to a situation of laptop standby, though the machine is not a notebook but a desktop. I don't know how to "unlock" it. So I just pressed the power button to reboot the system. 

The ridiculous thing is that the system skipped self-check. I saw the lights on the keyboard flashed once when the power is on. Then, no response at all ( I tried to press the cap key, no light is on).  LCD still has no signal.  Power light is on and CPU fans starts to work. The machine just "stand by" :(

Even if I put in a live CD, the system has no response when reboot. I can not even access my BIOS information now, neither to the XP system. so essentially I've no idea how to reinstall a system under current situation.  The system looks just dead, no response for whatever I do. 

Is there any key combination to unlock the "suspension" situation? 
Any suggestion is highly appreciated!! Thanks a  lot!

-Lei

---

### Post by GoodPanos on 2007-09-27
Have you been able to shut the notebook completely...power off and remove battery and then turn it back on?

---

### Post by RockyRock on 2007-09-27
The situation is that it is a DeskTOP. not a notebook.

---

### Post by nvteighen on 2007-09-27
Suspend has some weird behaivor. I had a similar situation, but I was able to reboot my computer. Sometimes, I can manage to wake the computer up, but then keyboard does not work and I can't enter my password at the lock screen.

You should wait until Gutsy is released with the new 2.6.22 kernel, I think.

---

### Post by GoodPanos on 2007-09-27
Oops :oops:

Regardless...hold the power button for 5 secs and it should power down the PC or you can just pull out the power cord from the back.

---

### Post by RockyRock on 2007-09-27
I've already tried "press the power key and reboot" for many times. 

It reboots without self-check. So even if I put in a live CD, the system won't read it. It just "stand by". 

Even if the kernel has new version, I've no idea how to update or reinstall a new system. sigh...

Maybe I need to pull out the hard disk to backup my data first.

---

### Post by nvteighen on 2007-09-27
Do you mean that when you reboot from power button, BIOS doesn't even appear? That's weird: suspension is done to RAM, so if you take power away, it should be lost and reboot should be normal... Or have you done hibernation?

---

### Post by RockyRock on 2007-09-27
Exactly, the BIOS does not appear. This is really weird.  So I even didn't know how to reinstall now.

I thought the UBUNTU suspend implement some similar features as hibernation. 

I'll try to jump reset the CMOS on the mainboard to see if it works.

Didn't expect UBUNTU to be so "weird" :)

---

### Post by nvteighen on 2007-09-27
But this is not a software but a hardware/physical issue, I think and resetting CMOS won't help if BIOS even does not appear!

Have you tried to unplug your computer?

I've had weird behaivors at suspension, but I could always escape into Console (Ctrl+Alt+F1) and reboot.

Maybe your PC needs to be cleansed from dust or check connections (apologize if it sounds bad, but have you checked if monitor is connected correctly?). It really looks like an external issue.

---

### Post by RockyRock on 2007-09-27
I unplugged my power cable and leave the machine for several hours. I also tried to clean the inside (actually, not much dust as the machine is relatively new)  and reconnect the monitor, keyboard, mouse etc. and reboot.  Bingo! it works now:)

Thanks a lot for your suggestion. But I'm still not sure this is related to Ubuntu's software problem or my hardware problem. Probably I can try to suspend the machine again to see the effect :)

---

### Post by nvteighen on 2007-09-28
> **RockyRock said:**
> I unplugged my power cable and leave the machine for several hours. I also tried to clean the inside (actually, not much dust as the machine is relatively new)  and reconnect the monitor, keyboard, mouse etc. and reboot.  Bingo! it works now:)

Thanks a lot for your suggestion. But I'm still not sure this is related to Ubuntu's software problem or my hardware problem. Probably I can try to suspend the machine again to see the effect :)

Glad to hear it's solved! (By the way, mark this thread as solved, please, using the Thread Tools menu)

---

