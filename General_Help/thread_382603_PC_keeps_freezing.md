---
title: "PC keeps freezing"
date: 2007-03-12
forum: General Help
---

### Post by nero666 on 2007-03-12
hello guys,

my pc is having some freezing problems for a while

when i'm using the computer it hangs randomly,sometimes the mouse stop responding, and then the keyboard, and sometimes it freezes completely

when i try to compile a new kernel its hangs..

i'm also having this kind of problem in windows xp (blue screen..)

i have executed memtest86 for about 10 hours without errors, and also some diagnostics for the hard disk...

i don't know what it can be... but i'm pretty upset with it

any help will be appreciated
thanks

using ubuntu 6.10 (kernel 2.6.17) / windows xp
athlon64 3500+
ddr400 1gb
hd seagate 120gb
mobo abit ax8

---

### Post by Kateikyoushi on 2007-03-12
Is your power supply enough for the system, and are the power rails stable ? Can check it with the abit system monitor. What cooler do you use ? Is the airflow enough inside the case ?

---

### Post by laidback on 2007-03-12
Overheating cpu?

---

### Post by bobpaul on 2007-03-12
90% sure your processor is overheating. A good way to test this, in Windows, is to run Prime95 and set it to one of the high cpu usage or high heat torture test modes.

Prime95 is available for Linux as well, but only command line.

You probably have dust in your CPU heat sink, your HS Fan is broke, or you improperly installed your HS on the CPU (too much/too little thermal paste, removed HS without cleaning and using new paste, etc). Alternatively, it could be too much heat is simply building up inside the case. You may need to replace a broken case fan, etc.

---

### Post by ComputerGuy56 on 2007-03-12
Also, on my computer when it starts, you press F1 and it goes to a WINDOWS booting screen diagnostics(not grub) there I can see what my CPU temperature is and how fast the fan is. Though some computers don't have it I think....

---

### Post by bobpaul on 2007-03-12
> **ComputerGuy56 said:**
> Also, on my computer when it starts, you press F1 and it goes to a WINDOWS booting screen diagnostics(not grub) there I can see what my CPU temperature is and how fast the fan is. Though some computers don't have it I think....

Umm... that sounds like your system BIOS configuration utility. This is part of the motherboard and not related to Windows or Linux. When the computer turns on, the bios is loaded off the ROM chip. This then loads the boot loader off your boot hard drive. If you have linux installed, this is probably Grub. Grub then loads the Linux kernel, or the Windows boot loader (NTLoader).

Unless you're pressing F1 sometime after choosing Windows on the Grub screen, but I don't recall Windows responding to that key on bootup...

It would be better to have temp monitoring software running when you cause a crash, but if you go in there IMMEDIATELY after a crash and read the temps, you'll probably see that they're relatively high.

---

### Post by nero666 on 2007-03-12
thanks for the help, guys

i used prime95 for about 10min and the temperature came up to 62C but the system was stable and didn't crash (windows xp)

anyway i opened the case and took all the dust from it (a lot)

now i'm on ubuntu and tried to compile a new kernel and then the system gives me these messages and stop compiling (txt attached)

looks like i'm having these page faults, dunno why, i am having the same on windows xp

---

### Post by nero666 on 2007-03-12
now prime95 give me an error:

FATAL ERROR: Rounding was 0.5, expectecd less than 0.4
Hardware failure detected, consult stress.txt file.
Torture Test ran 9 minutes - 1 errors, 0 warnings.
Execution halted.

---

### Post by al_sharpe on 2007-03-22
Hello nero666:

What video card do you have.
My experience with nVidia 6600GT is that it will overheat, at random 
creating the freezes you describe.
Very frustrating.
Al Sharpe

---

### Post by nero666 on 2007-03-22
hi there,
my problem is fixed now

it was the memory slot i think
i changed the mem from slot 1 and 2 to 3 and 4 and now it's working normally

anyway thx to everybody

---

