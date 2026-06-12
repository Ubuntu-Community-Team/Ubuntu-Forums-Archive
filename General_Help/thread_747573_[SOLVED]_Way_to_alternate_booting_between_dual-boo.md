---
title: "[SOLVED] Way to alternate booting between dual-boot operating systems?"
date: 2008-04-06
forum: General Help
---

### Post by commonplace on 2008-04-06
Here's a weird question. I have a machine with Vista and Ubuntu installed on it in a dual-boot configuration, with GRUB handling the OS selection. It works great, so there's no problems there.

What I'm wondering is, is there anyway to make it so that if I'm in Ubuntu and I reboot, it goes into Vista, and if I'm in Vista and reboot, it goes into Ubuntu? Without having to manually select anything at the boot menu, I mean.

I realise this sounds weird, but I use the machine mostly via remote access (VNC and NX for Ubuntu, and Radmin for Vista) and if I'm in Ubuntu and need to get to Vista, I can't do that remotely. What I've done in the past is change the default OS to Vista in boot.lst, but then when I'm done with Vista and want to get back to Ubuntu, I'm stuck.

So, is there any way of doing this? It doesn't have to be pretty, just possible. :)

/Kevin

---

### Post by brian_p on 2008-04-06
> **commonplace said:**
> 
So, is there any way of doing this? It doesn't have to be pretty, just possible. :)

/Kevin

Look at the default option in /boot/grub/menu.lst. It's certainly not pretty.

---

### Post by commonplace on 2008-04-07
> **brian_p said:**
> Look at the default option in /boot/grub/menu.lst. It's certainly not pretty.

Alright, so if I'm in Ubuntu, I can change the default to Vista, and then reboot which would take me into Vista. Once I'm in Vista, though, how would I then change the default to Ubuntu so that rebooting would take me to Ubuntu?

/Kevin

---

### Post by brian_p on 2008-04-07
> **commonplace said:**
> Alright, so if I'm in Ubuntu, I can change the default to Vista, and then reboot which would take me into Vista. Once I'm in Vista, though, how would I then change the default to Ubuntu so that rebooting would take me to Ubuntu?

/Kevin

Return to the setting you had previously?

---

### Post by commonplace on 2008-04-07
> **brian_p said:**
> Return to the setting you had previously?

Right, okay, but how am I to edit the menu.lst from within Vista?

I'm starting to think I'm missing something quite obvious here... :-)

/Kevin

---

### Post by pseudo-random on 2008-04-07
So you need to be able to read/write to your ext3 partition?
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by brian_p on 2008-04-07
> **commonplace said:**
> Right, okay, but how am I to edit the menu.lst from within Vista?

I'm starting to think I'm missing something quite obvious here... :-)

/Kevin

No, it's me who is missing something. Reading the question properly helps! I'll give it another thought but don't expect a response any time soon.

---

### Post by commonplace on 2008-04-07
> **pseudo-random said:**
> So you need to be able to read/write to your ext3 partition?
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Okay, that would work. So in Ubuntu I'd edit the menu.lst to change the default OS to Vista, and in Vista, I'd do the same process in reverse to make Ubuntu the default. That'll work for what I'm doing.

There's no way to automate this, is there? Probably not worth the hassle...

Thanks everyone for your help!

/Kevin

---

### Post by Victormd on 2008-04-07
> **pseudo-random said:**
> So you need to be able to read/write to your ext3 partition?
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Unfortunately this won't give "write" capabilities...:confused:

I was thinking, not for too long not to start stinkin', but the only way would be a script that detected your last boot oprion (e.g. savedefault) and invert it, so it would always boot to a different option...

Now that the coast is clear here, I'll give it some more thought to see if we can come up with something.

---

### Post by commonplace on 2008-04-07
> **Victormd said:**
> Unfortunately this won't give "write" capabilities...:confused:

Ah. Well, that's a problem, then! I hadn't looked at it yet, so I guess I spoke too soon.

I guess I really am the only person out there who wants this functionality. haha

/Kevin

---

### Post by Victormd on 2008-04-07
Ok, I have an idea but can't be held responsible for anything going wrong...
There is a "fallback" option that you can use in grub that defines a second OS to boot in case the first one fails. So what you can try, is to set the default to Windows and Fallback to Ubuntu.  You'll have to mess with the windows boot (which is accecible by both windows and ubuntu).  When you want to boot into vista, leave the boot alone and when you want to boot into ubuntu, "mess up" your windows boot so that Grub falls back into ubuntu, and then from ubuntu, you can restore your windows boot.

I don't know how the fallback option works or how far it tries to boot before trying the second OS, but this might be a solution...

SOURCE: [http://www.gnu.org/software/grub/manual/grub.html#fallback](http://www.gnu.org/software/grub/manual/grub.html#fallback)
> 
13.1.2 fallback
&#8212; Command: fallback num...

    Go into unattended boot mode: if the default boot entry has any errors, instead of waiting for the user to do something, immediately start over using the num entry (same numbering as the default command (see default)). This obviously won't help if the machine was rebooted by a kernel that GRUB loaded. You can specify multiple fallback entry numbers.

---

### Post by Victormd on 2008-04-07
**[COLOR="Red"]Just to be clear, I don't know what files from windows' boot you'd have to mess up (a simple rename should suffice).  That's something that you'll have to play with... but I'm guessing that renaming your "ntldr" file should be enough...[/COLOR]**

To automate this, you could setup a simple *.bat routine to rename ntldr everytime you rebooted windows (I don't know if you can get around permissions for renaming it in a BAT file), and a script in ubuntu to restore the file...
This is all assuming that changing ntldr would cause GRUB to load the fallback OS.

***UPDATE***
Ok, so I thought I'd give it a shot on my comp. just to see what I was getting you into and here's what I found:
1. renaming ntldr to ntldr_tst:
     a. Windows fails to boot! Great, that's what we wanted...
     b. One of windows' famous "Keyboard not found, type F1 to continue" messages come up prompting you to reboot, so no luck here because it just tries again and fails to boot windows;
     c. Renaming ntldr_tst back to ntldr, system boots again.
2. renaming boot.ini to boot_backup.ini
     a. Windows still boots

What I've learned from this is that the failure has to come before windows starts to boot, i.e., change drive letter or partition or something like that so grub doesn't find it... but this has to be done from windows, so it will boot into ubuntu. Furthermore, you have to be able to bring it back from ubuntu, i.e., updating GRUB every time you boot into Ubuntu.

I don't think there's going to be an easy way to do this... I'll keep trying to think of something that hopefully won't bring your comp. to flames! :)

---

### Post by Victormd on 2008-04-08
Check this out:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by commonplace on 2008-04-19
Wow, you went above and beyond the call of duty! That was awesome, your testing of the fallback feature. Too bad it didn't work, but you (and thus, everyone else who reads this) learned a lot from your trial!

I think you're on the right track with the Ext2 driver for Windows. From there, I can access my Ubuntu partition and modify GRUB to boot back into Ubuntu by default. Not ideal, but hey, it works. THANK YOU!!!

/Kevin

---

### Post by Nameless Neko on 2008-04-22
Add savedefault 1 to your first boot option in menu.lst, and savedefault 0 to your second boot option (assuming you just have the two)

---

### Post by commonplace on 2008-04-23
> **Nameless Neko said:**
> Add savedefault 1 to your first boot option in menu.lst, and savedefault 0 to your second boot option (assuming you just have the two)

Thank you!!

/Kevin

---

### Post by MONODA on 2008-04-23
this is possible in OpenSuSE, you just select "boot another OS" and select the one you want, therefore this must be possible in ubuntu.

---

