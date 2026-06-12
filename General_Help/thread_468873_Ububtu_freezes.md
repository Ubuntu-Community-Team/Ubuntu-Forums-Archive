---
title: "Ububtu freezes"
date: 2007-06-09
forum: General Help
---

### Post by marcv700 on 2007-06-09
Many thanks to all of you who work hard to allow us to use a great product.:D:D

I feel that I may have enough information for someone who has a better insight into the functioning (or should I say malfunctioning ;)) I have encountered with Ubuntu.

When I upgraded from Ubuntu 6.06 to 6.10 last November. It worked fine for about a month after which I started to have glitches for which the only way out was a reboot..

I have a Celeron 866 with 512 Mb, an ATI Radeon VE

I know I should write different messages for different problems but as a matter of completeness (since there may be a link relating them) I will mention that either Open Office, Firefox or Kmail) will disappear while I am using them. I simply restart them.

The main problem is when Ubuntu completely freezes (no keyboard, no mouse) This has happened at least once a week since December. In the meantime I have completely installed last week (from scratch) Ubuntu 7.04 in the hope that it would be fixed. No luck.

Again I tried to search the forum (as I did many times since last December) to try and find if I could find a clue (I did not post but searched)

A couple of days ago I did find a solution that someone said fixed a similar problem by adding the parameters noapic nolapic pci=noacpi acpi=off hoping this would fix the problem ]

Programs still disappeared but no freezes until this morning...

I also realized this morning that one of the reasons I enjoyed Linux so much (I tried a few distributions in the last few years) and the beauty of it is that when you are stuck you could switch to the console mode and kill the application causing problem. 

The other beauty of the UNIX environment being that an application can fail but it should not impact (as it runs in a multitasking environment) interfere with (or clobber) others!

So the problem seems to be at a different level. 

The problem is that when the system freezes I cannot find or trace any record in the logs (or do not know where to find) something that could help fill a bug report.

What I do realize now is as far as I can remember these freezes occur while I am in an application and do an operation  which requires opening a window (like choosing Open in a menu or switching to another opened document.) when the dreaded mouse freeze (and keyboard) appears 

I hope this may shed some light on the problem and that maybe someone will be able to add 2 and 2 to point to a particular module that could create such behavior. ;)

Thanks a lot

---

### Post by MattJ100 on 2007-06-09
That's an odd problem. Can you rule out a hardware fault? I had similar strange symptoms on a PC under both Windows and Ubuntu. I later found that the problem was the graphics card, you never know...

I'm assuming you are not using Beryl, desktop effects, or any other graphically intensive programs?

---

### Post by marcv700 on 2007-06-09
Thanks Mattj100,

In fact I am not ruling out hardware as I have had, like you, a problem that occurred on both Windows and Mandrake (at the time). It was due to a leaking capacitor. It would occur after the computer had been on for some time (hours).

In the particular case of Ubuntu I do not have Windows installed on the computer and  the pattern is different. It may do it just right after I started the computer and have been working for as a short time as 15 minutes (like 2 days ago) and this morning then I am ok for the day! and it never happens when I work with a console (ctl-alt).

As far as the graphic card (or the driver) is concerned it might be a possibility. This is one reason why I reinstalled a clean system as I was not sure if I had changed the ATI driver at one time,. There are two available and this time I went with the CD install, so I presume it is not the proprietary driver.

The purpose of my post was trying to get some guidance as to how I could rule out either the hardware (I did run memtest, any comparable tests for graphic cards???)  or the software.

Thanks again

---

### Post by electrahogg42 on 2007-06-09
I am using feisty and am having a problem with everything freezing on me I can get online and stay no problem but open up anything in my desktop and it wont close have to force quit do that once or twice and the desktop freezes mouse pointer still moves keyboard still works but nothing opens or closes have to turn of power to reboot,   computer has been off all day so it isnt a heat problem just started doing this last night I really dont want to reinstall ubuntu if i dont have to but this is frustrating !!!!!!

---

### Post by FuturePilot on 2007-06-09
Well you're not the only one. Unfortunately no one knows what the problem is. It's happened to me on my laptop if it makes you feel any better
You might want to check this thread out
[http://ubuntuforums.org/showthread.php?t=412125]("http://ubuntuforums.org/showthread.php?t=412125")

---

### Post by marcv700 on 2007-06-09
Thanks futurePilot and electrahogg,

I checked the link (like others I checked before) and quite a few people are having problems but there is always  a little difference. Some can still move the mouse and the clock counts (not my case) I did a fresh install of Feisty, no beryl.
I cannot file a bug report since I do not have any useful information.
I have had this problem under edgy.
I tried FTP to my system, no connection possible DEAD :(
The link that pointed to berenger (or a name close to that) pointed to the problem (fairly old but must still exist) of the ATI driver support under Linux (contrary to Windows environment)
I am pretty much convinced that this is the core of the problem.

Is there any way I can take off that graphic adapter (which has been useless under Linux) and instead use the video on my ASUS CUSL2-C motherboard???  I bought the adapter to use dual screen (which I was able to do with Windows but never with Linux).

Is there any possibility that de ATI driver messes up things, that is freezes Linux , which I felt was in control, without finding any traces of that.

Thanks little by little I may go in the right direction

---

