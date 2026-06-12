---
title: "When booting &quot;Must load kernel first&quot;"
date: 2022-01-08
forum: General Help
---

### Post by wt-pm66 on 2022-01-08
I hope this is the right section for this, if not then please direct me to the right place, 

A few months ago, actually after I had a chance to beta Windows 11 I decided I needed to switch back to linux. So I went and just immediately installed Kubuntu, as it was my favorite distro back when. The install went perfect, but I had a problem running it, I posted on a Kubuntu forum, nobody knew anything. So I changed over to, I think before it was over I had installed every variation of Ubuntu/Debian there is, and every one of them had the same problem, When booting, or rebooting, the OS would always stop and give an error message of "Must load kernel first". After about 4 or 5 reboots it would finally load completely. This was many months ago, I finally gave up on an Ubuntu clone, and tried some Arch, and some independents, I finally decided to put Linux on the back burner until I got some other stuff out of the way, that was at least 6 months ago so I don't remember everything from that time. But the only issue really was the "Must load kernel first" error. like I said, once I get it to boot all the way, there was no problem. I remember that I would installl and reinstall at least twice just in case. But after the 3rd time I was obvious it was something within the OS, or installer or whatever, or in conjunction with something with this pc, It's been one problem after another. 

Dell Inspirion laptop
 
Processor    Intel(R) Core(TM)   i3-1005G1 CPU @ 1.20GHz   1.19 GHz

Installed RAM    8.00 GB (7.77 GB usable)

System type    64-bit operating system, x64-based processor

---

### Post by The Cog on 2022-01-09
That makes me wonder if there is something odd in the EFI boot partition. Is the disk completely free to wipe and start again - i.e. use the live installer to overwrite the first gigabyte or so with zeros and then re-partition before installing? It's drastic and I'm clutching at straws, so it's a last resort guess.

---

### Post by wt-pm66 on 2022-01-09
I've still got windows 10 installed, which I don't want to lose, I guess I could always reinstall windows, big thing is I want it available for a while just in case I run into a problem like I have with the "load kernel" situation with 'ubuntu. Let me see just what I can arrange this. Thanks for the reply, you've got my little hamster wheel turning, and I've a few ideas, I'll let you know what I come up with.

---

### Post by yancek on 2022-01-09
How did you install windows 11?  Was it an upgrade somehow from windows 10?  Did you download a windows 11 iso and boot/install it from a DVD/USB?
Is ths drive on which you have the current windows10 a GPT drive thus necessitation an EFI install?  Did you install Kubuntu and the other Linux OS's UEFI?  Is windows 10 the only currently installed/functioning OS on the computer?  Seems unusualy you would have this same problem with different OS's.  Have you tried and online search for that  error as it seems to occur frequently?

---

### Post by wt-pm66 on 2022-01-11
Let me see how many of your questions I can answer. They are all valid questions, which I should have thought to answer in my OP. 

*How did you install windows 11? Was it an upgrade somehow from windows  10?  Did you download a windows 11 iso and boot/install it from a  DVD/USB?
I combined these questions as they are all basically the same. I was in the Microsoft Beta test group, I don't remember the exact name. But I've been in that since the beta test for W7 came out. They ignored  my input on W8 (Possibly Vista, I don't remember the exact order of release), anyway I played with W11 for about two weeks, during that time they made some really stupid changes, and I knew we were looking at another W8, change just to change. Progress is good, change just to change is usually bad. Yes, I downloaded an ISO, put it on a usb and installed in a dual-boot. 


*Is ths drive on which you have the current windows10 a GPT drive thus  necessitation an EFI install?  Did you install Kubuntu and the other  Linux OS's UEFI? Have you tried and online search for that  error  as it seems to occur frequently? 				
Combining two seperate questions I will answer both in one answer. Yes, single drive, dual boot set up. When I first started looking for answers, turning off, UEFI and going with MBR was suggested by several people. My first install of Kubuntu (the first Linux I installed) was giving me the same error from the beginning, so I went through and turned off UEFI (I'm aware you don't actually turn off UEFI, but it is the only way I can think to say it, as it's too early in the morning). Anyway, I turned off secure boot, and some other things (I think), but that was maybe 8 or 9 months ago, and I've done so much, and tried so much, that I don't remember exactly what I've done. 



*Is windows 10 the only currently installed/functioning  OS on the computer?  
At the moment, yes windows 10 is the only system. I decided to just remove everything but W10, and delete all other partitions, and get a clean disk so to speak, then I decided to wait until I had more time to work on it, as I had a bunch of irl stuff going on. 


*Seems unusualy you would have this same problem  with different OS's.  
I totally agree with this statement. I was thinking that it came down to everything I tried had been either a Debian or Ubuntu variant, so I figured the core boot code was the same. But then I tried non-Debian flavors, some of them were the same problem, other booted fine but then had other problems. Again it's been so long, and I've done so much else, and I've misplaced my notes on what I installed and what problems I ran into, and what "solutions" I found, and their result. Actually I think my son grabbed them. 

I updated my bios, ran chkdsk, went through the Windows boot repair, and several distro's boot repair, usually that was the boot repair you download while in the live session. I ran all kinds of diagnostics, and found nothing that would cause any kind of problem. Matter of fact every Diagnostics, and boot repair that I tried, came back completely clean, no problem found. So I really don't know what could be wrong. I have  gotten around to trying this again, so I thought I might be better off to get advice before I try to install, rather than after. I just didn't realize how much of those failed attempts I had forgotten. But I haven't forgotten the "Must load kernel first" error. 

Thank you for giving your help in this.

---

### Post by tea for one on 2022-01-11
> **wt-pm66 said:**
>  When I first started looking for answers, turning off, UEFI and going with MBR was suggested by several people. My first install of Kubuntu (the first Linux I installed) was giving me the same error from the beginning, so I went through and turned off UEFI (I'm aware you don't actually turn off UEFI, but it is the only way I can think to say it, as it's too early in the morning). Anyway, I turned off secure boot, and some other things (I think), but that was maybe 8 or 9 months ago, and I've done so much, and tried so much, that I don't remember exactly what I've done.

> **wt-pm66 said:**
> At the moment, yes windows 10 is the only system. I decided to just remove everything but W10, and delete all other partitions, and get a clean disk so to speak, then I decided to wait until I had more time to work on it,

Can you confirm that Windows 10 is installed in UEFI mode with GPT?

---

### Post by wt-pm66 on 2022-01-11
> **tea for one said:**
> Can you confirm that Windows 10 is installed in UEFI mode with GPT?

Sure I was just about to open the bios anyway, give my an hour two.

---

### Post by wt-pm66 on 2022-01-12
Now that you mention it, I did do the complete wipe and reinstall, back when all this first started. I don't remember exactly what happened, but I managed to screw up my windows install, and had to start over. That didn't help. I figured that while I was doing it I might as well do it right. So I downloaded a disk format type program, put it on usb, restarted and then completely wiped the disk. I had it do 2 passes, of overwrite, then started over loading Windows

---

### Post by wt-pm66 on 2022-01-12
> Can you confirm that Windows 10 is installed in UEFI mode with GPT?

So I've double checked, and yes it is set for UEFI. Although nowhere does the BIOS specifically mention GPT, based on the languae used in the UEFI secion I assume it's talking about GPT. Especially since my Partition Manager list everything as GPT, and gives directions how to convert GPT to MBR.

---

### Post by tea for one on 2022-01-13
> **wt-pm66 said:**
> So I've double checked, and yes it is set for UEFI. Although nowhere does the BIOS specifically mention GPT, based on the languae used in the UEFI secion I assume it's talking about GPT. Especially since my Partition Manager list everything as GPT, and gives directions how to convert GPT to MBR.

The UEFI Set Up pages will not confirm if your disk is using GPT, you'll  have to boot into Windows 10 to confirm.

Check via Disk Management > Right Click C: > Properties > Volume > Partition Style

Here is a link with more detail including command line methods [https://pureinfotech.com/check-gpt-mbr-partition-windows-10/](https://pureinfotech.com/check-gpt-mbr-partition-windows-10/)

Alternatively, you can boot into a live Ubuntu session and check via Gparted or the equivalent in Kubuntu.

---

