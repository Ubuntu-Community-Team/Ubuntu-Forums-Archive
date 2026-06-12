---
title: "Incorrect Time"
date: 2007-03-23
forum: General Help
---

### Post by legzelda on 2007-03-23
Whenever I boot up my computer, the time is always wrong.  I can select the option to sync the time with a server, and that works, but when my laptop is not connected to the Internet and I turn off my computer, the time is always incorrect the next time I boot it up.  This problem also seems to happen after I suspend my laptop.  Any suggestions?

---

### Post by jimbob on 2007-03-23
I had that problem a while back and it turned out that I had inadvertently set the UTC flag to on.

Right click on the clock and choose preferences and make sure use UTC is not checked.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by daxumaming on 2007-03-23
If disabling UTC didn't work try checking on your BIOS (by hitting ESC or DEL right after you power up your computer). Then check , and change if necessary, your system tiime.

---

### Post by legzelda on 2007-03-24
I am not using UTC, but thanks for the suggestion.  My BIOS seems to be the problem.  Interestingly, when I change the time in the BIOS, it does not keep counting.  Ubuntu reflects the BIOS's time, but it only starts counting when I boot into the system, and it counts from the time at which I set the BIOS.  Furthermore, when I put my computer into suspend mode, the time also suspends.  If I turn off my computer, the time does not keep counting.  In addition, the Grub bootloader countdown does not work.  I am thinking there might be something messed up with my BIOS., particularly with whatever makes the computer measure time  Do you have any suggestions about how to fix this?

---

### Post by jimbob on 2007-03-24
Also, take a look at /etc/default/rcS.

If it says UTC=yes, change it to no and reboot.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by daxumaming on 2007-03-26
> **legzelda said:**
>  Interestingly, when I change the time in the BIOS, it does not keep counting.  Ubuntu reflects the BIOS's time, but it only starts counting when I boot into the system, and it counts from the time at which I set the BIOS.  Furthermore, when I put my computer into suspend mode, the time also suspends.  If I turn off my computer, the time does not keep counting.  

You need to replace the battery of your motherboard to fix this problem. Even a state of the art computer priced at $10,000 are still dumb enough when it comes to this, and when the battery dies out. Just open your case and take out the battery, then go to a local RadioShack or BestBuy store and go buy a replacement.

---

### Post by legzelda on 2007-03-27
Well, sure enough, it was the CMOS battery.  Evidently, Ubuntu has caused this same problem for many Dell laptop owners.  Unfortunately, whenever I boot my computer, I get the "time-of-day clock stopped" error.  Does anyone know the location of the CMOS battery on an E1505's motherboard and how I might go about replacing it?  Also, I could try the fix many other users said worked: simply unplugging and plugging in the CMOS battery.

---

