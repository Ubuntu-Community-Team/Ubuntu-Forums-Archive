---
title: "Suse GRUB for Ubuntu"
date: 2008-04-24
forum: General Help
---

### Post by Polk on 2008-04-24
Hi everyone,

I'm trying to make Ubuntu grub as nice looking as in SUSE. Specifically:
1. small nice looking font
2. some logo on the background
3. colored font like the one on the right where it says [OK]

NOTE: I'm NOT talking about splash screen that's before the loader and described here [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=208855](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=208855) and here [http://ubuntuforums.org/showthread.php?t=181485](http://ubuntuforums.org/showthread.php?t=181485)

Does anyone know how to do that? I coudn't find anywhere.

Thanks.

---

### Post by jw5801 on 2008-04-24
There's a How-To here:
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

---

### Post by Polk on 2008-04-24
> **jw5801 said:**
> There's a How-To here:
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

Thanks for reply. Are you trying to score? Please, Read my question again, specially the NOTE!

Can anyone really help?

---

### Post by jw5801 on 2008-04-24
Apologies, but as far as I'm aware, that IS the grub that's used in Suse. Can you provide a screenshot of what you're after?

Hmm... I think I get it. You mean the screen that displays whilst the boot scripts are running, after you've selected an option in Grub but before you reach the login screen? That is, the screen that displays if you have 'nosplash' set. That isn't grub at all and is related to the kernel settings, which can be set by grub, but the two are otherwise distinct. Sorry for the misunderstanding, have I hit what you're after now? Those are called ttys, you can reach them by pressing ctrl+alt+F1 through to ctrl+alt+F6 (ctrl+alt+F7 will take you back to grub), and these are the terminals where the bootscript information is output.

You can change the fontsize by passing the kernel the option vga=791 (so add it to the end of the line corresponding to the kernel in /boot/grub/menu.lst), as for changing the colours, I'm not sure but I've often been curious!

---

### Post by Polk on 2008-04-24
> **jw5801 said:**
> 
You can change the fontsize by passing the kernel the option vga=791 (so add it to the end of the line corresponding to the kernel in /boot/grub/menu.lst), as for changing the colours, I'm not sure but I've often been curious!

Perfect! You are on the right track.
1. The font size worked by setting vga=0x317 (copied from SUSE), the vga=791 didn't work, but I see you got it from this table:

Screen   640x480     800x600     1024x768     1280x1024     1600x1200 
Colors    --------------------------- ------------------------------------------- 
256     | 769         771           773           775              796 
 32,768 | 784         787           790           793              797 
 65,536 | 785         788           791           794              798 
 16.8M  | 786         789           792           795              799 

2. now, how do we add colors to the terminal or whatever this called after grub. The reason I called it terminal is because I'm guessing once we turn the colors ON, then the terminal will be colorful too (like in Suse). Whe you do "ls -l", folders are one color and files the other... very cool.

PS: if anyone is wondering, I'm trying to make Ubuntu look and feel like Suse completely, and actually SUSE like Ubuntu (Debian) with Apt-get and stuff like that which SUSE lacks of. I just love these two distros.

---

### Post by nquinnathome1 on 2008-04-24
> **Polk said:**
> Thanks for reply. Are you trying to score? Please, Read my question again, specially the NOTE!

Can anyone really help?

The title of your topic is **definitely** "Suse **GRUB** for Ubuntu" - I'm guessing you'll get better responses from people if you make sure in future your thread titles are correct. ;)

---

### Post by Polk on 2008-04-24
> **nquinnathome1 said:**
> The title of your topic is **definitely** "Suse **GRUB** for Ubuntu" - I'm guessing you'll get better responses from people if you make sure in future your thread titles are correct. ;)

I wish I knew what this thing called after the grub when you see all the services loading with [OK] status...

Thank you everyone for help.

I hope to find the way to make Debian/Ubuntu CLI colorful like in SUSE. Anyone?

---

### Post by dfour on 2008-04-29
> **Polk said:**
> I wish I knew what this thing called after the grub when you see all the services loading with [OK] status...

Thank you everyone for help.

I hope to find the way to make Debian/Ubuntu CLI colorful like in SUSE. Anyone?

It's called a boot splash.

---

