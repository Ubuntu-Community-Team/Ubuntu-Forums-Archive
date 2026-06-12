---
title: "VMware: Modify virtual machine BIOS...advice? Thinkpad and IBM Recovery CDs"
date: 2007-11-10
forum: General Help
---

### Post by briwood on 2007-11-10
Hey - I realize this is a pretty random question...and not entirely Ubuntu-related, but here goes...

I installed VMware and got to the point where I can Power On my virtual machine.  I have a Thinkpad T40p that dual boots XP/Gutsy.  IBM did not provide Windows XP CDs with this machine.  After a lot of whining I got them to send me the 4 IBM Recovery CDs and waive the $50 fee. 

I can get boot off the 1st CD, but I promptly get the message

[INDENT]** Your bios is not compatible with this recovery cd**[/INDENT]

I've read that it's possible to modify the virtual machine's bios.  I am wondering if there is any way to create a "snapshot" of my real BIOS and then get the VM to use use the same settings.  If the VM BIOS contains the "magic key", I should be able to install XP of the recovery CDs.

...or am I going to have to purchase XP? *shudder*

Thanks for any comments...

Brian

---

### Post by fjgaude on 2007-11-11
Gosh, I'm not sure any of this would be legal. That disk you have goes only with the hardware, I suppose. I know of no way to do what you wish, legal or otherwise.

---

### Post by briwood on 2007-11-12
Legality crossed my mind - briefly. Since all I'm doing is installing XP again on the same Thinkpad, I personally don't have any moral issues with it. 

I have a idea that might work.  Will report back if it does.

---

### Post by netbandit on 2007-11-12
You have a couple options here.  I own a thinkpad R50p, and it was great for its day.  If you want to have your legal copy of Windows that you got with the system in a virtual machine this is what you can do:

Unrecommended method:
format the thinkpad, install from the recovery CD's to have windows just like when you bought it, and then use the P2V program from VMWware to create virtual machine files on another computer.  I don't recommend this method because it will reinstall all those drives for things like the battery, acceleromoter, display, etc.  

Recommended method:
copy off the i386 folder from the thinkpad, then do a clean install (using your favorite boot disc) with the i386 files to the thinkpad.  once it is up, P2V it and then you have a cleaner copy.  You also have the benefit of the P2V program installing all the drivers for you.

I've never actually tried these methods, but from my experience I think they will work.,

Good Luck!
-nb

---

### Post by briwood on 2007-11-16
Thanks for the ideas netbandit.  I'm not very excited about formatting my machine, but I will keep these notes as an option.   

There is a way to create a new bios in the virtual machine.  I was wondering if I just get the latest bios from Lenovo and update the virtual machine with that, maybe then I could boot the recovery cds from the VM.  Probably, it's not that easy, but worth a try.

---

### Post by Craigus on 2007-11-16
There's also this option if XP is still installed:

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")

I do this on my desktop machine and it works fine. It is essential to create a hardware profile for the virtual machine, as in the tutorial.

---

