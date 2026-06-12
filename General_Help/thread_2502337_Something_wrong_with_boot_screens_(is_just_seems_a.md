---
title: "Something wrong with boot screens (is just seems an aesthetic problem)"
date: 2024-11-10
forum: General Help
---

### Post by massimiliano-polito on 2024-11-10
I've just installed Ubuntu Studio 24.04 from a bootable USB stick. Everything is working well besides this "aesthetic" problem.

When I turn on the PC I run through 5 different boot screens but two of them contains an empty rectangular frame, see below.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294498&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294499&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294500&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294501&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294502&stc=1[/IMG]

Any idea about how to get rid of screens 2 and 4 above?

Thanks.

Ciao,
Max

---

### Post by oldfred on 2024-11-10
Please only attach screen shots or photos, not post in line.
If you use the Forum's Go advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

From grub menu remove the quiet splash to see it that helps.
I always remove it, but then see the entire boot process. It used to help as it was slow enough to see issues. But now with SSD and faster systems, it goes by very quickly.
It that helps, you can make it permanent by editing /etc/default/grub and updating grub.

---

### Post by massimiliano-polito on 2024-11-16
Thanks for your reply and sorry for the bad images management.

I tried o remove "quiet splash" both temporarily (from the grub boot menu) and permanently (by modifying updating /etc/default/grub and running update-grub) but only the second occurrence of that blank box disappeared, the first one is still there.

Any idea about how to remove the first one also?

Ciao,
Max

---

### Post by oldfred on 2024-11-16
Did you change other settings like timeout in grub?
As it looks like it is the grub screen asking you to choose, but then blank.

Post this in code tags:
cat /etc/default/grub

---

### Post by massimiliano-polito on 2024-11-17
> **oldfred said:**
> Did you change other settings like timeout in grub?
As it looks like it is the grub screen asking you to choose, but then blank.

No, I only removed "quiet splash", see below.

> **oldfred said:**
> 
Post this in code tags:
cat /etc/default/grub

```
[FONT=monospace][COLOR=#000000]# If you change this file, run 'update-grub' afterwards to update [/COLOR]
# /boot/grub/grub.cfg. 
# For full documentation of the options in this file, see: 
#   info -f grub -n 'Simple configuration' 

GRUB_DEFAULT=0 
GRUB_TIMEOUT_STYLE=hidden 
GRUB_TIMEOUT=0 
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu` 
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
# 16/11/2024: modified to remove blank box on boot 
GRUB_CMDLINE_LINUX_DEFAULT="" 
GRUB_CMDLINE_LINUX="" 

# If your computer has multiple operating systems installed, then you 
# probably want to run os-prober. However, if your computer is a host 
# for guest OSes installed via LVM or raw disk devices, running 
# os-prober can cause damage to those guest OSes as it mounts 
# filesystems to look for things. 
#GRUB_DISABLE_OS_PROBER=false 

# Uncomment to enable BadRAM filtering, modify to suit your needs 
# This works with Linux (no patch required) and with any kernel that obtains 
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) 
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef" 

# Uncomment to disable graphical terminal 
#GRUB_TERMINAL=console 

# The resolution used on graphical terminal 
# note that you can use only modes which your graphic card supports via VBE 
# you can see them in real GRUB with the command `vbeinfo' 
#GRUB_GFXMODE=640x480 

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
#GRUB_DISABLE_LINUX_UUID=true 

# Uncomment to disable generation of recovery mode menu entries 
#GRUB_DISABLE_RECOVERY="true" 

# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1"
[/FONT]
```

This is the file that came with the installation, I didn't make any change besides the one reported above.

Ciao,
Max

---

### Post by oldfred on 2024-11-17
You changed grub timeout to 0. 
That is not normally suggested as then you cannot get to grub menu. I change default of 10 to 3 so menu only appears for 3 sec.

I also like to see menu so change hidden to menu.

---

### Post by massimiliano-polito on 2024-11-17
I didn't change the timeout to 0, as I said I only modified [FONT=monospace]GRUB_CMDLINE_LINUX_DEFAULT setting it to "" (removing "quiet" and "splash"), al the rest comes from Ubuntu installation.

Anyway, I've also tried modifying [/FONT][FONT=monospace]GRUB_TIMEOUT to 10 but the frame is still there. I also set [/FONT][FONT=monospace]GRUB_TIMEOUT_STYLE to "menu" to see if anything changed but the empty frame is always there (and I couldn't see any new menu appearing).[/FONT]

Apparently, neither [FONT=monospace]GRUB_CMDLINE_LINUX_DEFAULT nor [/FONT][FONT=monospace]GRUB_TIMEOUT nor [/FONT][FONT=monospace][/FONT][FONT=monospace]GRUB_TIMEOUT_STYLE are of any help to make it disappear.

Ciao,
Max
[/FONT]

---

### Post by massimiliano-polito on 2024-11-17
Just to give you a piece of information more, I've tried this:

I selected "Advanced options for Ubuntu" in the first screen so I was presented another menu where I had a couple of choices among which kernel to load.

I just hit "enter" (so the first choice was selected) and the boot process continued.

Following this sequence no empty frame appears.

Ciao,
Max

---

### Post by oldfred on 2024-11-17
The recovery mode uses nomodeset.
Instead of quiet spash try nomodeset on standard Ubuntu entry to see if it is the same as recovery mode.

Nomodeset is normally a temporarily setting because of video issues or proprietary video driver is not installed.

---

### Post by massimiliano-polito on 2024-11-21
I modified again grub.cfg, this time I used:

```

[FONT=monospace]GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"[/FONT]

```

but the first blank frame is still there.

I'm thinking that I have to renounce to having a perfect Linux box and live with this empty frame :)

Ciao,
Max

---

### Post by tea for one on 2024-11-21
> **massimiliano-polito said:**
> 
I selected "Advanced options for Ubuntu" in the first screen so I was presented another menu where I had a couple of choices among which kernel to load.
I just hit "enter" (so the first choice was selected) and the boot process continued.
You could set this as grub default, if you wish.
Just to be clear, this is not the recovery mode?
You are referring to a line similar to [COLOR="#0000FF"]Ubuntu, with Linux 6.11.0-9 generic[/COLOR]

---

### Post by massimiliano-polito on 2024-11-22
The first line in the menu I access after choosing "Advanced options for  Ubuntu" has two options, the first one is for the normal boot and the  second one allows to boot in "recovery mode".

When I selected the first  one (which is also the default one as it has the "*") I happen what I  described i the text you quoted, i.e. the boot processed continued without  showing any empty frame.

Ciao,
Max

---

### Post by tea for one on 2024-11-22
Let's try and set the first entry in Advanced Options as default
Open a terminal and enter:-
```
sudo nano /etc/default/grub
```
Change the following line
```
GRUB_DEFAULT="1>0" # This line is probably set at 0
```
Ctrl o to save and Ctrl x to exit
```
sudo update-grub
```

Grub counts from 0 hence GRUB_DEFAULT=0 is the first line of the Grub menu, which will boot the latest installed kernel.
GRUB_DEFAULT="1>0"
The 1 is the second line of the Grub menu i.e. Advanced Options for Ubuntu.
The 0 is the first option within Advanced Options
Don’t forget to run sudo update-grub after editing the file.

---

### Post by massimiliano-polito on 2024-11-22
Done it.

Now when it starts the highlighted boot menu entry is the second one ("Advanced options for Ubuntu") and then at the second menu the first entry is chosen which is the normal boot (I know because once booted I ran 'runlevel' and it returned 5 which means it's not in recovery mode).

The frame still appears but now there are a couple of log lines in it so at last there is a reason for it to be there.

Anyway that's not want I wanted...

I want a vanilla-PC that when turned on highlights the first menu entry (plain "Ubuntu") and then starts without any frame.

Now there is at least a reason for the frame to be there, it contains a couple of lines of log messages, but it's not working as it is supposed to do :P

Ciao,
Max

---

### Post by Dennis N on 2024-11-23
> I want a vanilla-PC that when turned on highlights the first menu entry (plain "Ubuntu") and then starts without any frame.
Your screenshot in post #1 shows you have a grub theme in use. The frame with the wide border is part of the theme. If you disable the theme, you will have the default grub menu.

The theme is usually specified in the /etc/default/grub file with a line like this:
```
GRUB_THEME="/usr/share/grub/themes/ubuntu-custom/theme.txt"
```
Add a # at the beginning of the line to disable the theme:
```
#GRUB_THEME="/usr/share/grub/themes/ubuntu-custom/theme.txt"
```
After this, run **sudo update-grub** to rebuild the grub.cfg file.

---

### Post by tea for one on 2024-11-23
Just to add to the suggestion from Dennis N, it would probably be pertinent to also return /etc/default/grub to its original default.
```
GRUB_DEFAULT=0
```

---

### Post by massimiliano-polito on 2024-11-23
Guys... I made a couple of hours of attempts, this is a summary of the result.

There is no GRUB_THEME in my [FONT=courier new]/etc/default/grub[/FONT] file but (I thought) if there is a variable to select a theme it means the theme is not something built in, I can change it. So I decided to change the theme and see what happened.

Wandering in the file system I found a directory [FONT=courier new]/boot/grub/themes/[/FONT] with a [FONT=courier new]ubuntustudio[/FONT] directory in it. Apparently that directory contains the graphics shown when my system boot.

I downloaded another theme and copied it in the same directory, modified [FONT=courier new]/etc/default/grub[/FONT] to load the new them through the GRUB_THEME parameter and run update-grub.

I rebooted the PC but nothing changed, the old theme with the blank frame was still there. So I had a look at the grub.cfg (the file built by update-grub, I guess) and realised that the new theme had been taken into consideration, some variables in that script actually referred to my new theme but unfortunately some lines below the same variables were overwritten with the old theme so it seems it is impossible to change the theme through GRUB_THEME because something in grub.cfg always points to the original theme.

To work around this funny thing I renamed the [FONT=courier new]ubuntustudio[/FONT] directory (the original theme) in [FONT=courier new]/boot/grub/themes/ [/FONT]to [FONT=courier new]ubuntustudio.orig[/FONT] and the directory with the new theme to [FONT=courier new]ubuntustudio[/FONT].

I rebooted the system and this time the new theme was loaded, and this theme doesn't have the problem of the blank frame!

So the problem is solved, the blank frame disappeared, the theme is far nicer than the original one but unfortunately it is an Ubuntu theme (it only reads "Ubuntu") so I've lost the possibility to see "Ubuntu Studio" while booting.

I don't like it so much, I'd rather fix the original theme and have the original Ubuntu Studio 24.04 theme but Ubuntu is a sibling of Ubuntu Studio so it's not too bad either.

The real solution would be understanding where that blank frame is defined in the original Ubuntu Studio theme and fix it but I'm not so good at these sort of things and it'd take too much time...

Thanks for your support... it's not perfect but it's far better than before.

Ciao,
Max

---

### Post by Dennis N on 2024-11-23
> So the problem is solved, the blank frame disappeared, the theme is far nicer than the original one but unfortunately it is an Ubuntu theme (it only reads "Ubuntu") so I've lost the possibility to see "Ubuntu Studio" while booting.

The "Ubuntu" name in the new theme might be an image file stored in the theme folder. You could replace it with another image file with the same file name and dimensions (or approximate) which displays "Ubuntu Studio" instead.  Inkscape is a good tool for creating it

---

