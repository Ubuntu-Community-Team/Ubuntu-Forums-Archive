---
title: "problem after install"
date: 2008-06-26
forum: General Help
---

### Post by blackhock on 2008-06-26
i have installed ubuntu 8.04 using Wubi and after reboot and see the the boot option 
1-windows xp proffesional.
2-Ubuntu
i selected ubuntu and then the logo came out with the orange progress bar then it takes 5 minute until it turned dark with some words in white like
[165.812795]ata2.01:Exception Emask 0x0 SErr 0x0 action 0x2 frozen

and a lot like that i tried to press Esc to enter the 4 options and all of them led to this black page with errors .
please help me in this .
My pc is :
intel(R) Pentium(R) 4 CPU 1.80GHz
GeForce2 MX/MX 400 [NV11]
384 RAM

---

### Post by PmDematagoda on 2008-06-26
Well, that error usually suggests bad sectors or a hard drive that is about to fail, so you may want to take a look at that.

---

### Post by blackhock on 2008-06-26
hey i need a solution man

---

### Post by WRDN on 2008-06-26
You should start by checking the disk, so boot from the Windows disk (if you have it), enter the recovery console and enter "chkdsk /r".
You can also do this by booting into XP, and entering the command in the Command Prompt (Start > Run > "cmd"). You may have to reboot the PC during this process, and it will complete the disk check before the login screen appears.
In the command, the "/r" command is used to locate bad sectors and recover readable information. You could also use the "chkdsk /f" command to automatically fix any errors encountered.

---

### Post by teaumaz on 2008-06-26
> **blackhock said:**
> hey i need a solution man
As PmDematagoda suggests, the solution might be to check your drive's health and if need be, replace it...

---

### Post by Conger on 2008-07-24
So, let's say I'm getting the same error message, ran dskchk /f, and it didn't fix the problem... Is my ONLY solution to get a new HDD?

And does this error mean for sure that my HDD is going to fail? In other words, should I be shopping for a new HDD even if I give up on Ubuntu?

---

### Post by thyre on 2008-07-24
how old exactly is your hard drive?

---

### Post by Conger on 2008-07-24
I bought it in March, this year.

The only reason I can think of it being messed up is that I had to reinstall windows recently, so I had to transport the HDD back and forth from a friend's house to transfer my important files from my HDD to theirs. 

Idk, but it seems unlikely that the way in which I handled it would cause it to be failing.

---

### Post by Conger on 2008-07-25
Sorry to have to bump, but I'm really worried that I might lose all my important files (i'm a digital artist) soon... and I really have nowhere else to put them.

So... yeah, those questions up there. ^^^

Anyone?

---

### Post by minhmeoke on 2008-07-25
A small number of hard drives fail prematurely. Your hard drive manufacturer may have diagnostic / health monitoring tools for download on their website. If there are errors, you could get it replaced under warranty.

If you have important files, just buy an external USB/Firewire hard drive or usb stick, and save the files there, it is a good investment.

---

### Post by Conger on 2008-07-25
I ran all the most extensive tests on SeaTools from Seagate... my drive passed all of them. 

So, now I don't know what to think.

---

### Post by Conger on 2008-07-27
No ideas? Anyone?

I really want to try linux.

---

