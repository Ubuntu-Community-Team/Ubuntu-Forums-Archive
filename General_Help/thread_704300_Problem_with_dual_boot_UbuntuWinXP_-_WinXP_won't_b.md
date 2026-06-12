---
title: "Problem with dual boot Ubuntu/WinXP - WinXP won't boot"
date: 2008-02-22
forum: General Help
---

### Post by ismarj on 2008-02-22
Hallo everybody,

I have problem with installing Ubuntu 7.10 and Windows XP dual boot.
There was Windows XP installed already on a single NTFS partition. I've tried to install Ubuntu 7.10 and to setup dual boot. I followed installation instructions, and in patritioning menu i've selected first option ("Resize IDE master partition..."). Installation ended fine. 
The problem occurred after restart. GRUB seemed to be installed OK, i've got OS selection screen with Ubuntu and Windows XP on it. But when I selected WinXP i've got windows screen which asked me to choose between safe mode or starting windows normaly (standard WinXP screen which appears after hard restart or something similar). If i chose "Start Windows normaly..." i get windows startup screen for few seconds and then computer restarts. If I chose "Start Windows in Safe Mode" it also starts booting and restarts after couple of seconds.
Ubuntu works fine.
I've tried accessing Win partition from Ubuntu, that also works - i can see all my folders and files.

I realy need to be able to boot windows too, so if anybody expirienced similar problem please advice me how to make it work.
Thanks in advance!

Best regards,
Ismar

---

### Post by gobbles414 on 2008-02-22
ismarj,

Did you do a defrag and error check of your hard drive(s) in Windows before installing Ubuntu? Resizing a hard drive is tricky enough, even without having to worry about a fragmented disk. Here is what I suggest that you do:

1. Enter Windows in Safe Mode and create backups of as much of your data as you can.

2. Use a copy of [GWSCAN]("http://support.gateway.com/support/drivers/search.asp?param=gwscan&st=kw") or a similar utility to totally erase your hard drive(s). Warning: This may also erase any system restore utilities that exist on your computer.

3. Reinstall Windows. If you have a real Windows XP operating system disk (not a system restore disk), you can create a partition for Windows and another for Ubuntu. In all my years as a computer tech, I have only encountered one system restore utility that allowed partitioning.

4. If you were not able to create partitions while reinstalling XP, do a defrag and error check now. Then install Ubuntu as you did before.

5. Reinstall Ubuntu. If you were able to create two partitions and the Ubuntu partition is larger, just chose the "use largest contiguous free space" option. If you have two partitions and the Ubuntu partition is smaller, I believe that you'll have to configure the disk formatting manually. Ubuntu 7.10 uses the ext3 disk format by default. Important: Don't forget to create a SWAP area on your Ubuntu partition as well. The general rule for the size of swap has been twice the amount of your physical RAM. But if you have a lot of RAM that rule doesn't always make a lot of sense. I've never had to manually configure a swap in Ubuntu, so I'm not an expert on it.

PS: You were correct to install Windows first and Ubuntu second. Installing Windows second would have trashed GRUB -- hiding your Ubuntu installation from you.

---

### Post by ismarj on 2008-02-24
gobbles414,

Thank you for your reply, it was very informational. I was hoping to somehow restore my existing Windows partition because my computer (with Windows instalation) was part of the large domain, so reinstalling will mean setting it up again (and messing with very hard-to-contact domain admin :)).
Your suggestion about disk fragmentation was probably the key problem in my case. Disk was very fragmented before i installed Ubuntu. I've tried to defragment it, but defragmenting tool couldn't do it all the way (it defragmented it only partialy). Installation of Ubuntu probably damaged Win partition. If i didn't have to keep the Win settings i would have erase everything and do it as you said. But i messed it up :(. 
But this is also learning expirience (unfortunately the bad one :)). Thank you on your time.

Ismar

---

### Post by gobbles414 on 2008-02-25
Ismar,

You might be able to get a 3rd party defrag program to run in Windows' safe mode. I personally like [Auslogics Disk Defrag]("http://www.auslogics.com/en/software"). For the fastest defrag time in ADD, be sure to set its preferences to highest speed.  But I've never tried to run ADD in safe mode. Let me know if this works for you.

---

