---
title: "Desktop Big Time Major Problem"
date: 2007-01-10
forum: General Help
---

### Post by sa_ill on 2007-01-10
Huh Im sick and tired of my desktop now.
It used to hand a lot and Blue Screens were a regular thing. My computer vendor advised my to change my RAM because my old one had defective and burnt circuits.
I did that, bought a new DDR400 512MB RAM, but still no help.
My system hangs frequently with a blue screen. And half the time it just gets stuck and then restarts.
The blue screen message I get is are of two kinds

1. KERNEL_STACK_INPAGE_ERROR
STOP: 0X00000077 (0XC000000E, 0XC000000E, 0X00000000, 0X01B51000, 0X24A2000)

2. KERNEL_DATA_INPAGE_ERROR
STOP: 0X0000007A (0XC03E054, 0XC000000E, 0XF8395384, 0X05679860)
atapi.sys - Address F8395384 base at F8388000 DateStamp 4110764d

The number in bracets may vary but usually its the one given.
I googled all the messages but the the information on the internet is retty irrelevant. Please help me its causing me a lot of problems.

PLEASE HELP ME.

---

### Post by kidders on 2007-01-10
Hi there,

These look like paging errors ... but aren't they MS error messages? (Surely you're posting in the wrong forum!)

---

### Post by smoker on 2007-01-10
this is a windows error, you should really post details,

but try a look at this page
[http://support.microsoft.com/kb/315266](http://support.microsoft.com/kb/315266)

best of luck, though if you want to, try linux and never have those problems again!

---

### Post by sa_ill on 2007-01-10
I triend the microsoft website but no help.
Please if you guys can help me personally I would really appreciate it.
If you want me to give you more information about this problem ask me what kind of info do you want.

---

### Post by d3v1ant_0n3 on 2007-01-10
[ THIS ](http://www.annoyances.org/exec/forum/winxp/1074490383) discussion board looks like it's dealing with a similar problem.

When I googled atapi.sys, I got a lot of pages- give it a try, something might be helpful?

---

### Post by smoker on 2007-01-10
did you try the solutions on the page i linked?

> Boot Sector Virus
To determine if you have a boot sector virus, run a current virus-checking program, and if needed, disinfect your computer.
Back to the top	Back to the top
Not a Boot Sector Virus
&#8226;	View the System Log in Event Viewer for additional error messages that help you determine the device that is causing the error.
&#8226;	Bad block. Stop 0x77 is caused by a bad block in a paging file, or a disk controller error, or in extremely rare cases it is caused when non-paged pool resources are unavailable.
&#8226;	If the first and second parameters are 0, then the stack signature was not found in the kernel stack. The cause of this issue is defective hardware. If the I/O status is C0000185 and the paging file is on a SCSI-based hard disk, you should verify the disk cabling and SCSI termination.
&#8226;	If the I/O status code is 0xC000009C or 0xC000016A, this normally indicates that the data could not be read from the disk due to a bad block.
&#8226;	If you can restart your computer after the error message, Autochk runs automatically and tries to map out the bad sector. If for some reason Autochk does not scan the hard disk for errors, manually start the disk scanner. If your computer is formatted with the NTFS file system, run Chkdsk /f /r on the system partition. You must restart your computer before the disk scan begins. If you cannot start your computer due to this issue, use the Command Console and run Chkdsk /r.
&#8226;	Defective or unreliable random access memory (RAM) is another common cause of this issue.
&#8226;	Verify that all the adapter cards in your computer are properly seated.
&#8226;	Ensure that all adapter card contacts are clean.
&#8226;	Disable system caching in the BIOS to see if this resolves the error.
&#8226;	If this does not resolve the issue, your computer mainboard (motherboard) may be damaged.
Back to the top	

---

### Post by sa_ill on 2007-01-10
i did the chkdsk /r thing
it found some errors and rectified it but still no good looks

---

### Post by usien on 2007-01-10
r u a user pf ubuntu as well?if not then u shud consider it!i was a windows user 4 abt 12 years (used versions 3.1,95,98,2000,me,xp nd vista).i just converted 2 linux a few weeks ago.8)

---

### Post by sa_ill on 2007-01-11
linux has support issues

---

### Post by usien on 2007-01-11
like wat?did u get over ur issues with windows?:-D

---

### Post by Netherspirit on 2007-01-11
I have been a Windows user for many years too. I installed Ubuntu because I was sick of all the Windows problems (virus, spyware, general lack of proper security etc). Long story short, all the information and support that I needed to learn Ubunutu from scratch was documented in Ubuntu or on this forum or in the links provided on this forum. What more support do you need? 

I am on the verge of completely removing Windows from my home PC. I will be running Windows in VMWare for the 1 or 2 apps that I need.

At work I have to use Windows, and I am enjoying Linux so much that I am considering installing VMWare to run Linux on my work PC to have some of my fav programs like Amarok. :-D And the idea of browsing the web on Windows freaks me out a little.

---

