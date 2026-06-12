---
title: "Computer won't shut down after installing Kubuntu"
date: 2007-05-02
forum: General Help
---

### Post by reedness on 2007-05-02
I just installed Kubuntu Desktop from the Synaptic Package Manager, (was using Gnome and Ubuntu until now)  and I now cannot shut down or reboot my computer correctly.  All it does is go the shutdown screen with the Kubuntu logo and the status bar stays black and then the screen will flicker, and it stays at a standstill again for like 10 seconds, flickers again, then sits there for 10 seconds, etc... until I hold the power button.  The last time I did it my wallpaper wasn't saved.  Any suggestions?  By the way, I am using Feisty 64-bit if that helps.  It was working fine until now.  Do I need to uninstall GDM or Ubuntu-desktop or what?

---

### Post by ezuli on 2007-05-08
> Do I need to uninstall GDM or Ubuntu-desktop or what?No help, I have same issue with no Gnome-stuff at all. Regular Ubuntu with Gnome did shutdown well, but no Kubuntu.

---

### Post by masonfoley on 2007-05-14
I am unable to shut down Kubuntu as well.  After I click the Restart icon, the shell will unload to a black screen...then the lcd panel just "bleeds" white...it's rather odd.  I've tried to reboot several times now and it never proceeds past this screen that looks like my LCD on my laptop is going to melt.

I installed from the Kubuntu Feisty 7.04 ISO.

---

### Post by FSHero on 2007-05-20
Hi all,

I have a similar problem. First, some info:

Processor: Pentium 2 333MHz (Yes, it's old!)
RAM: 384MB
Ubuntu distro: Kubuntu Feisty Fawn

What happens is: when I go to K Menu --> Logout --> Turn Off, the black bar fills up, but the computer does not shut itself automatically. I hear the hard disk 'click' as if it is 'retiring'. I have to manually shut the computer down.

If I press Ctrl+Alt+F1 while the black bar is filling, then I see a variety of shut-down messages. The final one, at which my hard disk 'clicks', reads something like: System Halted. (Basically, something saying that the computer has indeed closed everything.)

I don't know if this has anything to do with anything, but there is some start-up message that mentions something about my power or ACPI. (I press Ctrl+Alt+F1 when the blue bar loads, at start-up.) I have attached the output of dmesg. I cropped the last few lines because I went over this forum's file size limit by 0.2 KB! Grrr...

I can't remember exactly what is shown on the screen, but I'll post back later.

For the record, this computer's power button seems to be the 'new style' button: it is not an on/off push-in/push-out switch, but the one where the button feels the same to the touch regardless of whether you are turning the comp. on or off.

Furthermore, the same problem occurs in Edgy Eft. Also, restarting the computer is okay with Feisty Fawn: I don't have to press the reset switch myself or anything like that. Finally, with Knoppix 4.0 and 5.1, the computer **does** turn off automatically, which I choose the equivalent shut-down option.

Could the problem be that the power features on our computers are not being detected (at all / correctly)?

---

### Post by jbysmith on 2007-05-20
I've only toyed with Kubuntu once, but I had a similar problem when I was distro-hopping and had a couple do that to me.

Is the kernel using ACPI?  Not sure which boot loader Kubuntu uses, but the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=428197&highlight=acpi+power+off) will probably cover you.

---

### Post by FSHero on 2007-05-21
jbysmith,

I followed the instructions given in [that link]("http://ubuntuforums.org/showthread.php?t=428197&highlight=acpi+power+off"), but there is no change. I edited my /etc/grub/menu.lst as described.

You asked if my kernel is using ACPI; how do I check?

Also, this is what I see on startup:
```

[0.000000] ACPI: Unable to locate RSDP
[<something... can't remember>] PCI: Failed to allocate mem resource #6:10000@f000000 from 0000:01:00.0
```

That second line looks kind-of serious, but my computer seems to work near-perfectly (some problems with Amarok, but fixable ones).

Thanks for the link. I'll read the rest of the thread; I only read the first few posts :P

---

### Post by FSHero on 2007-06-13
Sorry to revive this thread, but I thought that the following might help people:

I read on [this  blog]("http://www.understated.co.uk/blog/2004/automatic-shutdown-in-ubuntu/") that adding the following line to the file /etc/modules:
```
apm power_off=1
```

fixed my problem. That is, before when I clicked shutdown I had to press the power button to cut the power to my PC, but now I don't.

Hope this helps.

---

### Post by reedness on 2007-07-10
Thanks!  If I go back to Kubuntu I will try this.  I have been hopping around from distro to distro.  PCLinuxOS has been the best to me so far.  Right now I am installing Ubuntu Ultimate.  It looks AWESOME!!!  :guitar:

---

