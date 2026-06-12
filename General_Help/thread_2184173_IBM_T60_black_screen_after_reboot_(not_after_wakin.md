---
title: "IBM T60: black screen after reboot (not after waking up)"
date: 2013-10-27
forum: General Help
---

### Post by glucazeau on 2013-10-27
Hello,

I've just installed Ubuntu 12.04.3 LTS on a Thinkpad T60, and when I boot from the harddrive I get a black screen.

I've installed it using a bootable USB key, the first time when restarting the system to complete the installation I had this black screen and thought something was wrong so I've reinstalled. Then, somehow it worked (I've entered the Bios or pressed some keys) and I've been able to finalize the installation and configure the user account.

But now everytime I restart the computer I have this:
1. Thinkpad welcome screen (the one saying "press the Thinkvantage button to enter the Bios configuration" or something like that)
2. Purple screen (Ubuntu colour) for a few seconds
3. Black screen
4. I can hear the percussions meaning that Ubuntu has started

Then, I just close the laptop and it goes to sleep. I reopen it and then I see my wallpaper and the login screen. Every time.

It seems to me like a really weird issue, I would more expect the opposite, usually problems occur after waking up the computer.

Any help would be greatly appreciated, even just to diagnose the cause, I've looking at some system logs but didn't see anything special.

Thanks! :)

---

### Post by tgalati4 on 2013-10-27
Perhaps set nomodeset as a kernel boot parameter.  There are several settings for graphics when coming out of sleep.  You can see them:

Open a terminal:

```
cat /etc/default/acpi-support
```

It's possible that the graphics are not initializing correctly at boot, but a different graphics mode is used coming out of sleep.

What graphics card do you have?

```
lspci | grep VGA
```

---

### Post by glucazeau on 2013-10-28
Hi,

thank you for your reply, here is my graphic card:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

I've added **nomodset** to the kernel following this [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) and restarted two times without having the problem.

Thank you for your help!! :)

Edit: I couldn't find how to tag a thread solved

---

### Post by tgalati4 on 2013-10-28
Glad that you got it fixed.  Upper Right in light grey is a pull down menu called "Thread Tools".  Marked as Solved should be there.

---

