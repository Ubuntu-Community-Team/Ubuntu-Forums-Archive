---
title: "Query regarding the cheap side of laptop choices and Fed Tax Preparation"
date: 2024-09-29
forum: General Help
---

### Post by Old Jimma on 2024-09-29
Hello Fellow Ubuntuers!

I use a commmonly used US Federal Tax software that I'll call 'Twin T" just for fun.

I run it on an old 32 bit desktop.

Pretty soon, "Twin-T" will support only tax preparation on a 64 bit computer. This seems to imply that if I want to keep using "Twin-T" and stay on the good side of John Law, I gotta buy a 64-Bit computer running the hearaled "W" opperating system.

I can buy a pretty good refurbished latptop running the "W" opperating sytem... for not too much money.

However, I sure don't want to buy a computer that I use for only 1 app for only a few weeks in the year.

I know that I can remove the hard drive of the "W" computer, insert another hard drive, and load Ubuntu on it an play gleefully... until its time to do Federal and State taxes in the Spring.

**[SIZE=4]My question is: when the day comes when I need to work on taxes, can I remove the hard drive running ubuntu, and reinsert the hard drive running windows so that I can run "Twin-T" and get my taxes done?[/SIZE]**

Thanks,
Old

---

### Post by yancek on 2024-09-29
You seem to be implying that this software can only be used on windows rather than the problem being a 64bit system.  All recent releases of Ubuntu are 64bit so there would be no problem unless this company only has software which will run on windows.

If you get the new computer with windows on it and remove the windows drive and then put it another drive and install Ubuntu to that drive it should work and you can simply make the drive selection from the BIOS to select Ubuntu or windows.  Or enable os-prober and run update-grub from Ubuntu with both drives attached.  Simpler if an EFI machine which it will probably be unless the hardware is 5+ years old.

---

### Post by dragonfly41 on 2024-09-29
You could also have an Azure Windows account which you can use when keeping "John Law" on your good side.  I am going through tax returns right now (U.K. side) and my bank offers appropriate tools. I don't know what "Twin-T" you refer to. Also there is an opensource accounting tool "Akaunting" which you can run in Ubuntu but I'm starting with an account in the cloud to become familiar. My take is not to rely on a single tool when it comes to tax returns. And build desktop automation scripts. Consider executors having to step in to sort out affairs. "Dead man's handle" policy.

P.S. research iXBRL file format to create your own returns.

---

### Post by oldfred on 2024-09-29
TurboTax only runs in Windows.
If taxes simple enough, you may be able to use the new on-line version from IRS to file.

I have posted multiple times about how I hate laptops. Not ergonomic and small screen, keyboard at wrong height etc.
but needed a laptop for travel & TurboTax. My CPA retired, so back to TT which I started using back in DOS days.

But I regularly boot Windows just to do updates, which take a while. Do not want months of updates which may then have issues if too many at once. 
Now issue is to make fixes in Windows I have to use Google and it seems every version of Windows has slightly different gui, so screens do not match my system to make fixes. Ubuntu terminal makes fixes a lot easier.
I actually primarily use desktop with Kubuntu, but have install & copy of data from desktop in external SSD which I use with laptop.

TheFu has posted several times about purchase of a used laptop that then is not very expensive, but better performance than many newer low cost systems.

TheFu laptop suggestions. 
[https://ubuntuforums.org/showthread.php?t=2470620&p=14073999#post14073999](https://ubuntuforums.org/showthread.php?t=2470620&p=14073999#post14073999)
Deal site had  Dell 14 inch Core i3 for US$330
Intel, 11" too small 13" about right if 1080p, 8GB RAM, 
Anti laptop rant
[https://ubuntuforums.org/showthread.php?t=2435155&p=13926792#post13926792](https://ubuntuforums.org/showthread.php?t=2435155&p=13926792#post13926792)

---

### Post by Norm24 on 2024-09-29
I've been using TT online with Ubuntu for over a decade.No issues.

---

### Post by him610 on 2024-09-29
> I can buy a pretty good refurbished latptop running the "W" opperating sytem... for not too much money.

If you decide on this course of action, you may want to consider getting the W11 version.

---

### Post by bobunderwood99 on 2024-09-29
Couldn't you run TT in a Windows VM?

[https://www.irs.gov/filing/free-file-do-your-federal-taxes-for-free](https://www.irs.gov/filing/free-file-do-your-federal-taxes-for-free)

I suggest using IRS Direct File (if available to you) or Fillable Forms.

Beware of Guided Tax Software - [https://www.cnbc.com/2024/01/23/ftc-bans-deceptive-advertising-for-free-filing-from-turbotax-.html](https://www.cnbc.com/2024/01/23/ftc-bans-deceptive-advertising-for-free-filing-from-turbotax-.html)

---

### Post by ian-weisser on 2024-09-30
> **Old Jimma said:**
> 
**[SIZE=4]My question is: when the day comes when I need to work on taxes, can I remove the hard drive running ubuntu, and reinsert the hard drive running windows so that I can run "Twin-T" and get my taxes done?[/SIZE]**


If you really want to do it that way, then it will probably work.

Don't wait until mid-April to test it. 

I would not encrypt the Windows system, nor use Secure Boot. Keep that boot as simple as possible.
If you plan to connect to a network, then budget several hours to catch up on Windows updates and reboots before the system becomes useful for doing any work.

---

### Post by dragonfly41 on 2024-09-30
> Don't wait until mid-April to test it.


**+1**


Recently I have experienced multiple obstacles in filing.
Today we had an area power outage at 11th hour.
So my advice from recent experience is to do "dry runs" in advance.
Be prepared. Have n+1 routes to submit returns.

---

### Post by Old Jimma on 2024-10-03
Many thanks to all who commented.

I suspect that , having 2 thumbs on both hands, I'd screw things up somehow and it would cost me.

Thanks again,
Old

---

