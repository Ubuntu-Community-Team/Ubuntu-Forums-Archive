---
title: "Hardware or OS problem"
date: 2014-04-13
forum: General Help
---

### Post by Engineeringtech on 2014-04-13
I don't want to get into an involved troubleshooting session.  I just wondered what others think about this problem.

I have nn old (2002) Gateway 600YGR laptop with a 1.6 ghz Pentium 4-M.  It dual boots Ubuntu 12.04 LTS, and Windows 2K (which I only boot into on rare occasions when I run an old CAD app.)  I download security updates for 12.04 almost four times a week.   The machine ran fine until about four months ago, when I started getting random cursor jumping.  I'll be typing, and my  cursor will suddenly jump to a different part of the paragraph.  Or I cannot place the cursor at a particular location.  It just wont stay put.   Not only this, but the email filters (which sort mail based on the sender's address), stopped working correctly.  They started dumping my email to the wrong folders.  Now I'm also getting frequent slowdowns or freezes.   I'll type a letter and 30 seconds later it appears on the screen.  When the machine locks up, there is no response to the keyboard or mousepad.  I have to do a hard restart.    The freezes usually start when I am running Firefox or Chrome browsers, or my Evolution email.    

I thought this was caused by a hardware issue.   This machine does get warm.  But I can boot into Windows 2K and run my machine until my eyeballs ache, and never experience any of these symptoms.

I thought that Ubuntu 12.04LTS may have become too demading of resources after an update.   So I booted the machine with a Lubuntu 13.10 Live CD.  The problems were immediately obvious.    I had been told that Lubuntu is light on resources.  

So is this a hardware problem?  Or just an incompatibility between my hardware and Ubuntu in general?

---

### Post by Impavidus on 2014-04-13
I don't think that Ubuntu 12.04 is heavier now than half a year ago. The security updates and bug fixes don't add much. So I think it may be a hardware error. Windows manages memory in a different way than Ubuntu, so it may be that Ubuntu gives problems when using faulty pieces of memory, whereas Windows never touches those pieces of memory.

---

### Post by Engineeringtech on 2014-04-13
Thanks for replying.   I've run memory tests many times.  No problem found.

---

### Post by tgalati4 on 2014-04-14
Time to open the machine up and clean it out.  Reseat connections.  Mouse problems are normally captured in /var/log/Xorg.0.log.  If this is a trackpad, try cleaning around the edges with a cotton swab and alcohol.  Let it dry thoroughly before using.  Turn "edge scrolling" off to see if that changes the behavior.

---

### Post by Engineeringtech on 2014-04-14
No mouse issues noted in Xorg.0.log.  I keep the trackpad clean.  And there is no jumping cursor, slowdown, or freeze. when I am booted into Windows 2K..

---

### Post by tgalati4 on 2014-04-14
I don't think Win2K uses edge scrolling.  Linux tends to turn it on and if you have debris on the right edge of the trackpad then it will jump around like a Mexican Jumping Bean.

Right after jumping mouse even open a terminal and post:

```
dmesg | tail -40
```

---

### Post by Engineeringtech on 2014-04-16
> **tgalati4 said:**
> I don't think Win2K uses edge scrolling.  Linux tends to turn it on and if you have debris on the right edge of the trackpad then it will jump around like a Mexican Jumping Bean.

Right after jumping mouse even open a terminal and post:

```
dmesg | tail -40
```


Thanks.  Right now the machine is not acting up.     I haven't head you say anything about my wierd email problems.....

---

### Post by dragonfly41 on 2014-04-17
I also have a dual boot Ubuntu + Windows Vista running on an old Inspiron laptop.

The process of elimination I use in pinning down such problems is to get a number of reference points where the system works without problems.

e.g. you've established that your Windows works smoothly.

Now booting into Ubuntu try creating a new user account to see if that creates similar problems.

Try selecting Gnome Classic theme at user login.

If no problems arise then you have some package in your main account causing problems.

One by one start launching your apps in the newly created user account.

Start with your email client.

---

### Post by Engineeringtech on 2014-04-22
> **dragonfly41 said:**
> I also have a dual boot Ubuntu + Windows Vista running on an old Inspiron laptop.
The process of elimination I use in pinning down such problems is to get a number of reference points where the system works without problems
e.g. you've established that your Windows works smoothly.
Now booting into Ubuntu try creating a new user account to see if that creates similar problems.
Try selecting Gnome Classic theme at user login
If no problems arise then you have some package in your main account causing problems.
One by one start launching your apps in the newly created user account.
Start with your email client.


Thanks for your reply. Sorry I didn't respond quicker.   The holiday and family took precedence.    
I get what you're saying, but what about the fact that I booted with a Lubuntu Live CD and experienced the same problems? Since both Ubuntu and Lubuntu have the problems, but Windows 2K does not, doesn't this mean an incompatibility exists between my laptop and Linux?

---

