---
title: "[SOLVED] This should work, but would like a little confirmation"
date: 2008-03-04
forum: General Help
---

### Post by Radioman991 on 2008-03-04
Hello

I have an IBM Thinkpad T43 from work.  Runs XP, and kind of stuck with that.  The Winders HDD is encrypted, and I would not risk repartitioning, and using GRUB to dual boot off the internal drive.....so here is what I'd like to try....

I have a 100 GB external USB drive.  BIOS says first boot device is USB, so I SHOULd be able to install Gutsy onto that drive...and boot direct to Gutsy, as long as the USB drive is plugged into the laptop.  If the USB isn't connected, the laptop should boot into Winders...I would think.  I don't care if I can or cannot access the Winders drive from within Gutsy.

If anyone knows any traps I might fall into before I attempt this later today, feel free to reply.

Regards, PK

---

### Post by gobbles414 on 2008-03-05
Radioman991,

GRUB is a potential trap for sure. During a normal installation of Ubuntu for dual boot with Windows, GRUB actually overwrites the Windows bootloader. Since it sounds like you're planning to keep the Windows bootloader intact, I'm not sure if your computer will know to use GRUB on your external USB drive. My best guess is that booting from the USB will totally bypass the Windows bootloader.

I'd be curious to learn the results of your installation.

---

### Post by mixmaster on 2008-03-05
You can do this with a USB stick so I don't see why you shouldn't be able to do it with an external USB drive.

---

### Post by Radioman991 on 2008-03-05
Well.....my MBR got hosed.   Most likely caused by me being a noob....well thats how you learn I suppose.  In addition, I have no admin password to repair myself.

On the good side, I am getting a new HDD from Helpdesk ( I am a remote employee...no office), so I threw caution to the wind and nuked the IBM T43p drive to get Ubuntu on it so I could somewhat work today.  The ATI graphics card in that Thinkpad does NOT play well in the sandbox, like my Dells do.

Kind of  rough way to find out though  :-)

---

### Post by gobbles414 on 2008-03-05
> **Radioman991 said:**
> Well.....my MBR got hosed.   Most likely caused by me being a noob....well thats how you learn I suppose.  In addition, I have no admin password to repair myself.

On the good side, I am getting a new HDD from Helpdesk ( I am a remote employee...no office), so I threw caution to the wind and nuked the IBM T43p drive to get Ubuntu on it so I could somewhat work today.  The ATI graphics card in that Thinkpad does NOT play well in the sandbox, like my Dells do.

Kind of  rough way to find out though  :-)

Yeah, I've hosed a PC or two in my day too. :) Is your new hard drive going to arrive to you in an encrypted state? If not, use your Windows installation disk to partition your new hard drive. Then you can install Windows on one partition and Ubuntu on the other. Or if that's not an option: install Windows, do a defrag and error check, and then allow the Ubuntu installer to "resize" your new hard drive.

Keep us informed about your progress, please.

---

### Post by Radioman991 on 2008-03-05
Naw...its gonna show up encrypted.  All laptops from Corporate show up that way.  I can get a Linux laptop, but no VPN yet...and can't run the apps I support on Linux.  

Upon further review, I noticed I goofed on the boot sequence in BIOS....so BEFORE I put the new drive in, I am going to try the install on the USB drive again.....and see if I can boot to it

Appreciate all the responses.  If I can get the external to properly boot, I'll flag the thread as solved...til then, stay tuned.

---

### Post by Radioman991 on 2008-03-05
Well, got Ubuntu on the external drive.  I would have saved myself a lot of aggravation had I done 2 things....

1)  REMOVED my internal HDD before trying to install to the USB drive

2)  Set up the boot properly in BIOS.

The only minor issue I am running into is I have had the machine freeze twice...had to power off to get rebooted into Ubuntu.  Don't know if this is an issue with running the USB drive or not.  I do realize its not going to be a perfect soslution...but now I can run Ubuntu on the road...and only XP when I HAVE to.

Thanks all

---

