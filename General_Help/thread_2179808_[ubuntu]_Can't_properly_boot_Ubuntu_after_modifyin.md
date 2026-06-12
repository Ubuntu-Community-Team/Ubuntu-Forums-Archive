---
title: "[ubuntu] Can't properly boot Ubuntu after modifying grub file"
date: 2013-10-10
forum: General Help
---

### Post by FDRmz4Y on 2013-10-10
I can reach the grub menu (I think that's what it's called) (I run a Windows7/Ubuntu 12.04 Dual boot), but after I select Ubuntu, I get stuck at a purple screen. I was following these instructions:

> [COLOR=#000000]for all you novices like me i will try to give you a step by step[/COLOR]
[COLOR=#000000]open your console (for kde, go to start button >systems> terminal)[/COLOR]
[COLOR=#000000]$ type "[/COLOR][B]gksudo dolphin" 
or type "[B]gksudo nautilus"
this command brings up your default file explorer. you will be prompted for your admin password.

once password is entered the explorer windows will come up. go to /etc/default/ open file called grub. it will be automatically opened in an editor
find the line 
GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash” 
change it to

GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash nomodeset i8042.nomux 

save the file and close
on terminal, type sudo update-grub
then reboot[/B][/B]

Except I forgot to add in the i8042.nomux part, and now I can't boot into Ubuntu. Help on how I can be able to dim my screen or how to modify the grub file back to what it originally was please?

---

### Post by grahammechanical on 2013-10-10
1) At the Grub boot menu select Recovery mode.
2) At the Recovery menu select network. That will establish a network connection using the existing configuration files. It will also put the file system into read/write mode, which is needed if we are to edit a system file.
3) When back at the Recovery menu select root. That will get you to a command prompt. Run

```
 nano /etc/default/grub
```

That should open an editor called nano and place the grub file in its editing window. There will be some instructions in using Ctrl+W to writeout (save) and Ctrl+X to exit or something like that. I am writing from memory. Check for yourself.

Regards.

---

### Post by FDRmz4Y on 2013-10-10
Hi grahammechemical, thanks for the reply.

Unfortunately, I am unable to get into recovery mode. I can't get past the black screen that spits out a bunch of text telling you what is being loaded or what Ubuntu is trying to process. I think I am getting a udevd error related to my graphics card. What can I do now?

---

### Post by oldfred on 2013-10-10
If you get grub menu, on Ubuntu entry press e for edit and scroll to Linux line. You can then add your entries next to or inplace of splash quiet. This is a one time change to test boot parameters or let you boot. Then you can make it permanent if boot parameters work by editing /etc/default/grub.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by varunendra on 2013-10-10
> **FDRmz4Y said:**
> I was following these instructions:
> **GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash” **
change it to

**GRUB_CMDLINE_LINUX_DEFAULT=[COLOR="#FF0000"]“[/COLOR]quiet splash nomodeset i8042.nomux **
If the instructions are copy-pasted and not a typo on your part here, then the closing double-quote is missing after i8042.nomux. That maybe what is causing it to stuck. Besides what oldfred suggested (and he's the best person for help on these), you can boot with a live cd/usb and correct that. To be extra sure, just copy-paste the existing double-quotes, instead of typing them (some keyboard layouts type a non-acceptable type of double-quote which gives errors later).

For screen dimming issue, you should start a new thread. Different threads for different topics is a general rule of thumb for getting and offering best kind of help. :)
As a quick shot, you may try (without quotes) "acpi_osi=" boot option (see [post=10069997]here[/post] for details). If that doesn't help, start a new thread and post back the details of the problem, as well as the output of command suggested in [post=12809083]this[/post] post, might get you quicker help.

---

