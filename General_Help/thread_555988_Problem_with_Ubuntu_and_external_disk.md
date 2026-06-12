---
title: "Problem with Ubuntu and external disk"
date: 2007-09-20
forum: General Help
---

### Post by hotrod6657 on 2007-09-20
Hi everyone, let me first start off by saying that i am extremely new to Linux and while i love it so far I'm very much in the process of learning my way around.

So here's my problem.  A few weeks ago i decided to install Ubuntu on an external hard drive that i have connected to my laptop (Thinkpad t60p).  My laptop runs XP and i figured that installing Linux on an external drive would give me the best shot of not harming my windows install if something went wrong.  I have a lot of other stuff on the hard drive so i couldn't make it a dedicated install and had the Ubuntu installer create a new partition on the drive for Linux.  This all went well, and Ubuntu works like a charm.  The problem arises when i try and use my computer without the external drive.  When i do this i get a grub error 25 and can't access anything until i connect the hard drive and reboot the system.  

I've done a bit of checking and it seems like I've lost all or some of my MBR that was on my windows install and that the computer's trying to boot using GRUB, which is currently installed on my external drive, leading us to my problem.

Now, I'm open to any suggestions as to how to resolve this.  I've tried using the windows recovery console but to no avail.  I don't have a windows Cd since the OS came installed on my machine.

on a side note, I'm new to this forum so if I've missed something or haven't followed protocol please let me know and I'll do my best to fix the problem.

Thanks in advance everyone, 

hotrod

---

### Post by Happy_Man on 2007-09-20
Yeah, try and get a Windows CD from a friend so that you can get your MBR back. 

In future, right before you click "install" on the LiveCD installer, check "advanced" and specify the GRUB install location as "(1,0)" *without the quotes of course* 

That'll put it on the external, so that GRUB loads when you have it plugged in, but Windows will load when it's not.

---

### Post by hotrod6657 on 2007-09-20
Okay cool, thanks.  I'll start phoning friends to see if i can track down a CD.  I wish in hind sight that i had done a little bit more research and realized that i could install GRUB on the external drive.

If i can't find a CD or can't get that to restore my MBR are there other options?

Thanks again for your quick response.

---

### Post by Happy_Man on 2007-09-20
I believe the Super GRUB disk can also restore the MBR. 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by hotrod6657 on 2007-09-20
wow, happy_man, thank you so much for your suggestion.  I did a little looking and burned a copy of Super GRUB and it is amazing.  fixed my MBR problem without hardly trying and seems like a very valuable resource to have.  I don't think i've ever gotten this much help in such a short time on a forum before, thanks again.  I think i know where i'll be turning to the next time i need a hand.

---

