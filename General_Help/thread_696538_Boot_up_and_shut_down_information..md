---
title: "Boot up and shut down information."
date: 2008-02-14
forum: General Help
---

### Post by C. Wizard on 2008-02-14
Hello.
Just installed Kubuntu 7.10 amd64 a few days ago and so far Ubuntu/Kubuntu has been very  impressive.
However, having ran Slackware for a number of years I'm use to watching the boot up information fly by on the screen and would like to do the same thing in Kubuntu.
Is that possible, and if so, how do I go about it?
Thank you very much.

---

### Post by erginemr on 2008-02-14
Pressing Alt+F3 when Ubuntu splash screen lets you view the boot messages temporarily (that is, for this boot only). But the look is an ugly text screen, unlike the beautiful colored text flowing with a Tux logo that I have seen in some other distros (Knoppix comes to mind).

---

### Post by erginemr on 2008-02-14
To make it permanent, you need to edit /boot/grub/menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

Find the lines which load your normal Ubuntu system to the end of the file:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03c365eb-f779-4ba0-be78-3d8000f75ead ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
and remove the word "splash" from the line
```
kernel	/boot/vmlinuz-2.6.22-14-generic root=UUID=03c365eb-f779-4ba0-be78-3d8000f75ead ro quiet [COLOR="Red"]**splash**[/COLOR]
```

There are however better looking boot-up screens (PCLinuxOS and Zenwalk comes to mind). I also wonder how (of whether) we can also use such snazzy boot text messages under Ubuntu.

---

### Post by erginemr on 2008-02-14
I found much better! If you remove the word "quiet" instead of "splash" as in  
```
kernel	/boot/vmlinuz-2.6.22-14-generic root=UUID=03c365eb-f779-4ba0-be78-3d8000f75ead ro [COLOR="Red"]**quiet**[/COLOR] splash
```
then you can have a much better screen (see the attachment). Nice!

You can also check you options on the fly by editing grub settings during the boot. Select the grub entry you use for normal boot, enter the edit mode with "e", find the line with "kernel", press "e" again, remove "quiet" and press "b" to boot (do not press Esc). To make it permanent, again edit your "/boot/grub/menu.lst" file.

I hope this is what you are looking for.

---

### Post by C. Wizard on 2008-02-14
Thank you very much!  
The information is greatly appreciated and has been put to use.  By changing the Grub script, as you so kindly suggested, the splash screen at shutdown is also eliminated.
Thanks, again!.=D>
:)

---

### Post by azelter on 2008-02-15
Related to this - once the machine has actually booted up - is there any way to see the messages that were posted during bootup. The output on tty1 cannot be scrolled, and /var/log/messages does not contain the same information.

---

### Post by nick_h on 2008-02-15
Type:
```
dmesg
```

---

### Post by azelter on 2008-02-15
Thanks, I know this command. Perhaps all the info is there (one would expect it to be - right), I'm just curious what the line that flashes by me when I'm booting says. There is an ALERT in there somewhere but it goes by too fast to read. dmesg shows no line with the word alert in it. Is there anyway to actually write what is printed to screen at boot up to a log file?

---

### Post by erginemr on 2008-02-15
You should be able to have enough time to view the warning if you press Alt+F3 during the booting process. Pressing the Pause button on your keyboard may (or may not) help, too. 

You may also have a glance at system logs under Main Menu ->System -> Admin

---

### Post by C. Wizard on 2008-02-16
> **azelter said:**
> Related to this - once the machine has actually booted up - is there any way to see the messages that were posted during bootup. The output on tty1 cannot be scrolled, and /var/log/messages does not contain the same information.
Yes, go to the /var/log directory and look at the text file labeled, dmesg
:)

---

