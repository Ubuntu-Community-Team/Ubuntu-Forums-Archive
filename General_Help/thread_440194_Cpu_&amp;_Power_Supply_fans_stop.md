---
title: "Cpu &amp; Power Supply fans stop"
date: 2007-05-11
forum: General Help
---

### Post by timmy007 on 2007-05-11
Hi all 
New to linux:KS 
I was running Ubuntu 6.06 everything working fine 
Tried to upgrade to 6.10 that didn't work so I started again from a clean disk 
I reformatted and installed Ubuntu 7.04  
Now when turn on the computer the fans are running but after the grub loads the CPU and power supply fans stop  
Not good for the box 

Any ideas on what could be stopping the fans:confused:

---

### Post by carolinason on 2007-05-11
Interesting, sounds like acpi.

What is the make and model of the motherboard?

---

### Post by hessiess on 2007-05-11
i thort the power suply fan was controled by a tempriture sensor in the powersuply, independently from the rest of the computer

---

### Post by timmy007 on 2007-05-11
Hi All :KS 

It's an Intel P3 550MHz with an Intel mother board; it’s quite an old box 
That’s what I thought too the bios controls the power supply and CPU fans and its speed and temp 
The power management side of the bios is all ok nothing has change from before the upgrade ??

---

### Post by carolinason on 2007-06-06
This motherboard uses APM and it might be advantageous to disable any power management services. Try this to see if there is any result.

Also check the battery on the motherboard. Just a thought.

---

### Post by tgalati4 on 2007-06-06
Post the output of dmesg, but only the stuff that relates to APM and ACPI.  If Dapper was running fine on this machine, what were you looking for in Feisty?

---

### Post by Crafty Kisses on 2007-06-06
> **timmy007 said:**
> Hi all 
New to linux:KS 
I was running Ubuntu 6.06 everything working fine 
Tried to upgrade to 6.10 that didn't work so I started again from a clean disk 
I reformatted and installed Ubuntu 7.04  
Now when turn on the computer the fans are running but after the grub loads the CPU and power supply fans stop  
Not good for the box 

Any ideas on what could be stopping the fans:confused:

That's really strange. :o

---

### Post by timmy007 on 2007-06-21
Hello Everyone 

Thanks for the help so far its been great :p
I got sick of trying to fix it so I went out and got myself a new AMD Althon 64 x2 5600+ box 
And the thing screams power :D

thanks again everyone
timmy007

---

