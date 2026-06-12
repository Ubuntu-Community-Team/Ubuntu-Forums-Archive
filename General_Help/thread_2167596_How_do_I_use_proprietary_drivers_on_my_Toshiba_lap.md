---
title: "How do I use proprietary drivers on my Toshiba laptop? Fan makes noise!"
date: 2013-08-14
forum: General Help
---

### Post by g00d-l on 2013-08-14
Hello everyone,

This is my very first post, and I am still very new to Ubuntu 12.04.
My fan makes a lot of noise while the temperature is just 36 degrees.
It almost immediately starts ventilating, also when I don't run any application at all.

So I've read a few posts on this forum and it seems to be a regular problem having to do with getting the right drivers.

My question is how do I solve this? As already said before, I'm not yet very familiar with things like sudo and all of that...

My computer is a Toshiba Satellite L300D-01N Laptop Computer - AMD Athlon 64 X2 Dual-Core QL-60 1.9GHz.

I have installed Ubuntu 12.04 next to Windows XP professional, dualboot.

Something else that I've noticed is that my battery doesn't seem to get charged. Any suggestions are welcome.

Thanks for your answers,
JP

---

### Post by slickymaster on 2013-08-14
> **g00d-l said:**
> Hello everyone,

This is my very first post, and I am still very new to Ubuntu 12.04.
My fan makes a lot of noise while the temperature is just 36 degrees.
It almost immediately starts ventilating, also when I don't run any application at all.

So I've read a few posts on this forum and it seems to be a regular problem having to do with getting the right drivers.

My question is how do I solve this? As already said before, I'm not yet very familiar with things like sudo and all of that...

My computer is a Toshiba Satellite L300D-01N Laptop Computer - AMD Athlon 64 X2 Dual-Core QL-60 1.9GHz.

I have installed Ubuntu 12.04 next to Windows XP professional, dualboot.

Something else that I've noticed is that my battery doesn't seem to get charged. Any suggestions are welcome.

Thanks for your answers,
JP

Hi g00d-l, be very welcome to the forums.

To try to solve your fan issue, you can try the following:
Open a terminal window by hitting Ctrl+Alt+T keys and run the command bellow:```
gksu gedit /etc/default/grub
```it will prompt for your password so you have to type it in. Once the file is open, you have to edit it and replace the line **GRUB_CMDLINE_LINUX=""** with **GRUB_CMDLINE_LINUX="acpi=off"**. Then save the file and close it. Back again at the terminal you have to run the following command:```
sudo update-grub
```once again you'll be prompted for your password so enter it. And that's it, hopefully next time you boot your laptop its fan is managed correctly, going up and down on speed whenever it is required.

---

### Post by g00d-l on 2013-08-14
Hey Slickymaster,

I've followed your instructions, but now I can't boot up at all in ubuntu. 

So I am now writing this message when in Windows XP.

First of all the opening screen where you can choose which os you want to use, previously had an automatic countdown. Now it hasn't (after I applied the changes you suggested). So I have to choose.

What happens next is I get a screen with 'common problems', missing modules ls/dev
ALERT /dev/disk/by-uuid and then a long code , does not exist
Dropping to a shell

Busybox v 1-18-5

Enter help for a list of built in commands
-----
When I do that indeed I get a long text with commands.

Only problem is, I don't know which command to pick.

So I am a bit in trouble now.

Have you any idea?

Thanks anyway,
JP

---

### Post by slickymaster on 2013-08-14
Hmm, I wonder what might had gone wrong.
Well, in order to recover your normal boot, you'll have to follow this how-to over here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) in particular the section **_How to restore the Ubuntu grub bootloader (9.10 and beyond)_**

Please keep us posted.

---

### Post by g00d-l on 2013-08-14
Well... thanks slickymaster. 
I'm sorry to say that you're advise was not helpful at all.

---

### Post by slickymaster on 2013-08-14
Did you manage to recover your boot? Are you still dealing with problems to boot your Ubuntu?

---

### Post by g00d-l on 2013-08-15
Well then, after a lot of fiddling around it's all up and running again without data loss and somehow the fan noise has also disappeared. But I just did a complete re-install over the previous install from cd.

Thanks to countless crashes I've become a real backupper, Acronis and all that... but Déja dup is great. So that's good to know.

However... I am still really wondering why it went wrong slickymaster?

I have followed your instructions to the T of course, so maybe you check it. Then the pages about the boot recovery may be easy to understand when you're very experienced with linux, but for somebody new like myself it's more that it adds to the confusion. That's why I just did the re-install in the end.

Why now the fan noise has stopped, is another mystery... I have no idea. Just looked at the Disk Utility and there is the same message about the state of the disk and the same low temperature. So I can't see the answer there. But of course I am not complaining :o

Anyway, live and learn, so this has been a valuable lesson... no harm done, just a bit of time.

All the best and thanks for your help,
JP

---

### Post by slickymaster on 2013-08-16
> **g00d-l said:**
> Well then, after a lot of fiddling around it's all up and running again without data loss and somehow the fan noise has also disappeared. But I just did a complete re-install over the previous install from cd.

Thanks to countless crashes I've become a real backupper, Acronis and all that... but Déja dup is great. So that's good to know.

That's the best practice/policy when fiddling with one's system.

> **g00d-l said:**
> However... I am still really wondering why it went wrong slickymaster?

I have followed your instructions to the T of course, so maybe you check it. Then the pages about the boot recovery may be easy to understand when you're very experienced with linux, but for somebody new like myself it's more that it adds to the confusion. That's why I just did the re-install in the end.

You are completely right and I owe you a huge apology. I've reviewed my instructions and there's a small detail with a big importance that I forgot to mentioned, which is that before editing the **/etc/default/grub** file it's necessary to first boot up the computer and during the boot-up hold down the Shift key; once at the grub menu, select Ubuntu and press **e** for edit and then append the linux line with the boot option (acpi=off) and press Ctrl+x to boot. After that and once booted in Ubuntu, that's when it's edited the **/etc/default/grub** file like I said.

Again I apologize for all the inconvenience I causes you, by missing that small but very important step.

> **g00d-l said:**
> Why now the fan noise has stopped, is another mystery... I have no idea. Just looked at the Disk Utility and there is the same message about the state of the disk and the same low temperature. So I can't see the answer there. But of course I am not complaining :o

Anyway, live and learn, so this has been a valuable lesson... no harm done, just a bit of time.

All the best and thanks for your help,
JP

Maybe it was just a misconfiguration parameter somewhere that got solved with your fresh install. Anyway, I'm glad you, one way or the other, got things fixed.

---

### Post by g00d-l on 2013-12-17
Hi slickymaster,

The noise is back again...
Could you please write your instructions once more, but in a step by step way. The above confuses me.
So STEP ONE, STEP TWO etc.

Thanks,
JP

---

### Post by slickymaster on 2013-12-18
[LIST=1]
[*]Turn on your computer and during the boot process, press and hold the left Shift key. This will bring up the Grub2 menu from where you select "Ubuntu".
[*]Press the 'E' key for edit
[*]Append the linux line with the boot option: ```
GRUB_CMDLINE_LINUX=""
```
[*]Press Ctrl+X to boot
[*]Once booted, open a terminal window by hitting Ctrl+Alt+T keys and run the following to obtain a root prompt: ```
sudo -i
```
[*]Enter your password and at the root prompt, run the following: ```
gedit /etc/default/grub
```
[*]Once the file is open, replace the line GRUB_CMDLINE_LINUX="" with **GRUB_CMDLINE_LINUX="acpi=off"**
[*]Save the file and close it
[*]Again at the terminal run: ```
update-grub
```
[*]Close the terminal and reboot your computer
[/LIST]

_**NOTE:**_
Please do keep in mind that this will disable ACPI completely, thus disabling a lot of useful (or even needed) features, like.. fans. And may not work with all computers.
Be careful with this option, it might cause your machine to overheat if the fans no longer turn. Think of this as a last resort.

---

### Post by g00d-l on 2013-12-19
Thanks a lot for this clear overview slickymaster!!!
All the best,

JP

PS I'll be careful:guitar:

---

