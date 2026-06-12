---
title: "GRUB doesn't find theme in Ubuntu 22.04.2"
date: 2023-06-18
forum: General Help
---

### Post by S0h3iL on 2023-06-18
Hi.
Installed Ubuntu 22.04.2, haven't been aroud since 18.04, man o man!  Ubuntu sure has changed a lot and has a lot of bugs even though it's an  LTS version! I've been configuring it like for a week now and still it's  not the Ubuntu I want it to be... Just btw. But I'm gonna stay on Ubuntu coz it's the best! :guitar:I tried installing several GRUB themes with grub-customizer, got this problem. Also tried it manually, same thing happens. When I run *sudo update-grub* or *sudo update-grub2* I don't get the:

 ```
Found theme: /boot/grub/themes/*theme*/theme.txt

``` output in the output of the command... Tried some things that came to mind, googled, but no luck!
 Thanks in advance.

---

### Post by Rubi1200 on 2023-06-18
Hi,

Apps like Crub Customizer and Burg often cause more harm than good.

There are a couple of routes you can consider:

1. lots of information here on customizing GRUB:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://ubuntuforums.org/showthread.php?t=1195275](https://ubuntuforums.org/showthread.php?t=1195275)

2. another user we helped with the same issue used this tutorial to add a theme:
[https://ostechnix.com/change-grub-theme-in-linux/](https://ostechnix.com/change-grub-theme-in-linux/)

Hope this helps and good luck.

---

### Post by S0h3iL on 2023-06-19
Thanks. But no, didn't help. Problem still exists.
I installed kde (kubuntu-desktop) first thing when I installed Ubuntu, maybe that's why this problem occurs? I'm saying this because kde replaced the default plymouth booting screen, before installing kde it was a Lenovo logo with Ubuntu logo under it and now it's kubuntu logo... and I'm letting go of kde plasma, I don't need it anymore (as always kde didn't satisfy me...) I'm trying removing it now to see if it fixes this problem.
I also installed xfce4 but I don't think this is the issue.
I booted into a live Ubuntu 22.04.2 to try to install and customize grub from there but it was giving me errors. but something I observed in the live ubuntu was that it changed the cursor size in settings but I can't do this (change cursor size) in my installed version...
Somewhere since I installed ubuntu I did something/somethings that I shouldn't have done, but Idk what I did that caused so much trouble! I'll remove kde plasma and report back either it fixes the problem or not.  
Please help me, I did a lot of configuration and GUI customization in this install so I really don't want to install it all over again, linux has a benefit that u can fix anything in it, I'm hoping I can fix my problems.

---

### Post by dragonfly41 on 2023-06-19
Until you can sort out your Grub issues I suggest that you add rEFInd and then in your Bios settings choose rEFInd as first in line for booting. But read about it first. OldFred has published some links.  I use rEFInd for my own multi boot purposes. It runs alongside usual Grub.

---

### Post by S0h3iL on 2023-06-19
I made some progress, at least I figured out why the 'Found theme: ...' line doesn't appear.
I ended up installing a fresh install of Ubuntu! I edited the /etc/default/grub file and installed the theme the usual way by hand (manually) (by adding GRUB_THEME and etc) and when I comment the line Grub console like this:
```
#GRUB_TERMINAL=console
```
it shows me the: 
```
Found theme: /boot/grub/themes/*/theme.txt
```
line.
But when I remove the # at the first of the line, it no longer shows the found theme line.
And the thing is when I do this and reboot it doesn't show the grub menu at all, neither with theme nor without theme!
So far we know the problem is probably because of this damn 'GRUB_TERMINAL=console ' line. So with that in mind, any idea why this happens? 

Seriously, I wonder why nobody has had this problem before! When I first ran into it I Googled and expected that I'll find a good link that people had this issue and somebody explained how to fix it but Probably I'm the first person who reports this issue!
Please help, no linux problem has taken me this long to fix and I've been on GNU/Linux for about 15years now and that's why it's a pain in my ass that I can't figure out the fix...

---

### Post by Dennis N on 2023-06-19
> And the thing is when I do this and reboot it doesn't show the grub menu at all, neither with theme nor without theme!
Do you have **GRUB_TIMEOUT_STYLE=menu** ?
With the menu option used, you must also have a value >0 for GRUB_TIMEOUT=
Otherwise, no grub menu displays when Ubuntu is the only OS detected. Having a theme won't change this.
Also,
**GRUB_TERMINAL=console** is commented out on my system.
And, this may not matter, but my grub theme is installed in /usr/share/grub/themes.

---

### Post by S0h3iL on 2023-06-19
Idk man it's driving me crazy!
Here's my grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="menu"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""



# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#export GRUB_COLOR_NORMAL="light-gray/black"
#export GRUB_COLOR_HIGHLIGHT="magenta/black"

#GRUB_GFXMODE=1920x1080
#GRUB_THEME="/boot/grub/themes/grubby-terminal/theme.txt"

GRUB_THEME=/boot/grub/themes/descent/theme.txt
GRUB_GFXMODE=1280x800
```
With this config, the output of update-grub gives me the found theme line but grub doesn't show at all, theme or no theme.
Please edit my file the way you think it would fix the problem and post it for me here, appreciate your help.

---

### Post by S0h3iL on 2023-06-20
Did you see my last post? Sorry but you're my only hope for beating this problem... Thanks in advance.

---

### Post by S0h3iL on 2023-06-20
> **Dennis N said:**
> Do you have **GRUB_TIMEOUT_STYLE=menu** ?
With the menu option used, you must also have a value >0 for GRUB_TIMEOUT=
Otherwise, no grub menu displays when Ubuntu is the only OS detected. Having a theme won't change this.
Also,
**GRUB_TERMINAL=console** is commented out on my system.
And, this may not matter, but my grub theme is installed in /usr/share/grub/themes.

Did you see my last post? Sorry but you're my only hope for beating this problem... Thanks in advance.

---

### Post by Dennis N on 2023-06-20
Here is my /etc/default/grub so you can compare with yours:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1080,auto

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_THEME="/usr/share/grub/themes/vimix/theme.txt"

```

I downloaded my vimix theme from here:
[https://www.gnome-look.org/p/1009236/](https://www.gnome-look.org/p/1009236/)
From the download choices, I downloaded **Vimix-1080p.tar.xz**

It installs with a script, so you don't have to think about what goes where.

A screenshot of the grub menu with this theme is attached &#8595;

---

### Post by MAFoElffen on 2023-06-20
I have been watching the progress of this. You are not getting anywhere and seem to be spinning in circles.

Another approach to asking and matching things up:
```

ls -l /boot/grub/themes/descent/theme.txt
grep . /boot/grub/themes/descent/theme.txt

```
Because you say Grub2 is having a problem finding your theme file.

With that line in the /etc/default/grub file (for Grub2 theming), Grub2 does not care where it is located, as long as it can find it, and read it. It does not need to be located in a specific directory tree. But the path-to and filename need to be correct and accessible. It also needs to be on a filesystem that Grub2 can read natively. 

Please confirm that you can do this manually, before gong on...

---

