---
title: "URGENT: Help!"
date: 2008-04-27
forum: General Help
---

### Post by 3xist1 on 2008-04-27
I installed Ubuntu on my laptop & did like a full install I completely wiped out my Vista OS.

I like this OS, But doesn't do what I need :(( and I can't go back to Vista or XP! please help! I don't know what to do 

3xist.

[SOLVED]

---

### Post by dondad on 2008-04-27
> **3xist1 said:**
> I installed Ubuntu on my laptop & did like a full install I completely wiped out my Vista OS.

I like this OS, But doesn't do what I need :(( and I can't go back to Vista or XP! please help! I don't know what to do 

3xist.

If you did, in fact use the whole disk for Ubuntu, then the Windows stuff is gone and not recoverable. The only way to fix it is to reinstall Windows.

---

### Post by tamoneya on 2008-04-27
Sorry about your problems with nuking your windows install but the only way to get it back would be to reinstall it because you erased your partition when you installed linux.  

What is it exactly that isnt working for you?  We would be glad to help you resolve this problem or if you wish to help you get windows running on your laptop again.

---

### Post by 3xist1 on 2008-04-27
Thanks for your responses.

Yes, I am an idoit. I wiped out the entire partition & I have no Vista CD to install it back. The way I reformat on my laptop is do a system recovery on boot (F11), and reformat from there.

If I press F11, It loads straight to Ubuntu. I really like this but yeah I am a Teenager and just want Vista back...

Already tried XP CD I had for my old PC but it couldn't find a hardisk/partition. 

Thanks for your support guys!

3xist

---

### Post by mrsteveman1 on 2008-04-27
Those recovery things that come with most systems are usually separate partitions, so i hope you didn't delete that as well.

Are you sure that ubuntu is taking up the entire disk?

---

### Post by tamoneya on 2008-04-27
if you dont have a vista install dvd there is no way to reinstall vista.  I believe however the problem with the xp cd is your harddrive settings in the bios.  try to set the IDE or SATA controller to compatibility mode.  This should fix the install problem with XP and get you running quickly.  The other option is to try and find a vista DVD from a friend but use your license key which the PC manufacturer probably stuck on the back of the computer.  
By the way I am a teenager as well and that has nothing to do with a persons ability or inability to use either linux or XP or vista

---

### Post by 3xist1 on 2008-04-27
> **tamoneya said:**
> if you dont have a vista install dvd there is no way to reinstall vista.  I believe however the problem with the xp cd is your harddrive settings in the bios.  try to set the IDE or SATA controller to compatibility mode.  This should fix the install problem with XP and get you running quickly.  The other option is to try and find a vista DVD from a friend but use your license key which the PC manufacturer probably stuck on the back of the computer.  
By the way I am a teenager as well and that has nothing to do with a persons ability or inability to use either linux or XP or vista


Alright no worries.

I will leave this topic open until I change my BIOS settings & see how XP goes as you recommended.

YES I did delete the 2nd portion. Ubuntu taking up entire disk, But I will try BIOS first & get Vista of a friend off myn as the alternative. 

Yeah, I I didn't mean "Hey I'm A teen I can't cope" Sorry you got it in the wrong way. I'll post back tomorrow and tell you guys how things go. 

One more Quick Q: I installed qtorrent and can't find it anywhere? I know how to install stuff but how do I find my files?

Cheers,
3xist

---

### Post by tamoneya on 2008-04-27
do you mean the files you downloaded or the files that you installed.

---

### Post by 3xist1 on 2008-04-27
> **tamoneya said:**
> do you mean the files you downloaded or the files that you installed.

Files I installed.

---

### Post by tamoneya on 2008-04-27
they could have been installed into a variety of places.  Take a look in /usr/bin/qtorrent.  Also look at ~/.qtorrent.  If you just want to run qtorrent you can hit ALT-F2 and type ```
qtorrent
```

---

### Post by 3xist1 on 2008-04-27
> **tamoneya said:**
> they could have been installed into a variety of places.  Take a look in /usr/bin/qtorrent.  Also look at ~/.qtorrent.  If you just want to run qtorrent you can hit ALT-F2 and type ```
qtorrent
```

How do I get to this:??

**/usr/bin/qtorrent** 

3xist

---

### Post by jocko on 2008-04-27
> **3xist1 said:**
> How do I get to this:??

**/usr/bin/qtorrent** 

3xist

Not sure what you mean here? How to "get to" what?
If you want to start the program, just click alt+f2 and type qtorrent.
The actual program file is called qtorrent and it's located in the folder /usr/bin.

But have you checked that you don't have a shortcut under Program --> Internet?

---

### Post by Seks on 2008-04-27
If gparted is not already installed, install it. If your windows(ntfs) partition still exists then you can find it there, and change its flag to "boot" and in turn remove the boot flag from ubuntu. If it's not, you can at least create a ntfs partition for it from there.

---

### Post by mrsteveman1 on 2008-04-27
Be careful with that bios setting, it basically causes the SATA chip to emulate an IDE chip so that older operating systems, like XP, can install correctly, because they don't have sata drivers on the CD for most of these chips.

The problem there is if you do this and then switch it back later, XP still won't have an sata driver and will fail to boot, and it can be difficult to find the sata driver to install later.

---

### Post by CREEPING DEATH on 2008-04-27
If it's still under warranty the manufacturer will usually send you the original OS DVDs for free or low money.  Just make sure they know you have a valid license and only need a copy of the software.

CD

---

### Post by 3xist1 on 2008-04-28
Issue Resolved!

I changed my BIOS settings for SATA to disabled, I put Boot to CD first in order, and now I wiped out Uburtu and XP is on my machine working great.

Thanks for all your help!

Josh

---

### Post by mrsteveman1 on 2008-04-28
Just remember if you ever change that sata setting back to native, XP is going to fail to boot. You can fix it by leaving it on compatibility mode/ ide mode

---

