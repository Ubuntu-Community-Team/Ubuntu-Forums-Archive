---
title: "Remember brightness"
date: 2020-02-28
forum: General Help
---

### Post by dynvec on 2020-02-28
I have a laptop installation (not live). Unless I'm an environments so bright I have difficulty distinguishing what's on my display, I like to have minimum brightness. However, it doesn't seem to remember what brightness I had and every-time I'm at the lockout screen, I have to set it to minimum again. Is there a way for Ubunto to remember the brightness?

*Optionally*, I think the minimum brightness is a little too bright for me (not too much). Is there a way to change the settings so the the minimum brightness is even lower?

Thank you kindly

---

### Post by CelticWarrior on 2020-02-28
Many settings depend on the hardware. Such is the case, probably, with the minimum brightness. 

But other than that it should "remember"the setting. I just tested in 2 different computers with standard Ubuntu (Gnome) 19.10 and the selected value was kept.

If you have Nvidia Graphics likely you need to install proprietary drivers for better performance.

---

### Post by dynvec on 2020-02-28
> **CelticWarrior said:**
> If you have Nvidia Graphics
It's an U46E-1AWX, I doubt it has that.

---

### Post by CelticWarrior on 2020-02-28
> **dynvec said:**
> It's an U46E-1AWX, I doubt it has that.

Correct. It has an old integrated Intel Graphics. Therefore nothing to do with drivers.


Let's try what has been suggested for similar Asus models...

[LIST]
[*]Open /etc/default/grub -> ```
sudoedit /etc/default/grub
```
[*]Move to the line where "quiet splash" is and add an additional parameter, 'acpi_backlight=vendor'. It should look like this: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=#ff0000]acpi_backlight=vendor[/COLOR]"
``` 
[*]Save, exit, then run ```
sudo update-grub
```
[*]Reboot.
[/LIST]

---

### Post by dynvec on 2020-02-28
This is the terminal content of my attempt
> william@william-U46E:~$ sudoedit /etc/default/grub
[sudo] password for william: 
william@william-U46E:~$ sudoedit /etc/default/grub
sudoedit: /etc/default/grub unchanged
william@william-U46E:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-40-generic
Found initrd image: /boot/initrd.img-5.3.0-40-generic
Found linux image: /boot/vmlinuz-5.3.0-18-generic
Found initrd image: /boot/initrd.img-5.3.0-18-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
william@william-U46E:~$ sudoedit /etc/default/grub
sudoedit: /etc/default/grub unchanged
and I did reboot then did a few things then left the system unattended a few mins and the lockout screen behaved as before (had brightness higher than the minimum).

Please note that the command sudoedit had at the top > /var/tmp/grub.XX[6 characters] ([6 characters] wasn't that, it was something like *dT0k3u*) and since the terminal indicated it's unchanged, I'm wondering if I did something wrong.

---

### Post by CelticWarrior on 2020-02-28
Unchanged means exactly that: Changes weren't saved.

BTW, use CTRL+O to save and CTRL+X to exit.

---

### Post by dynvec on 2020-02-28
I don't know what's going on but following your instruction I rebooted yet running sudoedit still show the changes, the appending of the red in your post. The top still show something similar to my previous post (/var/tmp/grub.XX[6 characters]). Also in my attempt (which I referred to in my last post), the program had something like "# lines written" at the bottom; so I assumed it was changed and when I ran sudoedit a 2nd time the appending was still there, so I assumed it was indeed saved.

**Update 1:** I also used the GUI environment to open the file and the change was there.

---

### Post by CelticWarrior on 2020-02-28
Did you run 'sudo update-grub'?

---

### Post by dynvec on 2020-02-28
Yes, it's the 5th line in post #5 1st quote.

---

### Post by CelticWarrior on 2020-02-29
Sadly I have no other suggestion.

Years ago I would install Indicator Brightness - did it in a couple of laptops without dedicated brightness control keys - but that software isn't being updated - probably because it was meant for Unity - and the Gnome brightness control we have now should do the same and yes, it should "remember".

I suggest googling your model plus Ubuntu plus brightness to see what comes up.

---

