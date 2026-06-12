---
title: "Bootscreen not visible anymore, default gnome wallpaper appearing briefly."
date: 2013-06-19
forum: General Help
---

### Post by Reding on 2013-06-19
Hey everybody,

I'm trying to solve a bug which is been annoying me lately. I don't get any "Ubuntu" bootscreen anymore, instead i get a blue fullscreen for a few seconds which switches right away to the default gnome wallpaper just before i get to the logon screen (which shows my normal wallpaper).

I would like to get the default behaviour back with the classic Ubuntu logon screen which should bring me directly to the logon screen.

I hope my explanations are clear enough and that somebody can help me :)

I'm on Ubuntu 13.04 with gnome 3.6

Cheers

Red

---

### Post by MidnightGrey on 2013-06-19
by boot screen do you mean:

[the GRUB menu](http://www.databook.bz/wp-content/uploads/2009/07/GrubMenu00.png), or;
[Ubuntu loading screen](http://1.bp.blogspot.com/_4B7ZWQHqMpk/TMcEEwqP88I/AAAAAAAAAEc/uVUzQyc32Ik/s1600/boot1.png).

Can you copy-paste the output to this:
```
cat /etc/default/grub 
```

---

### Post by Reding on 2013-06-19
I mean the Ubuntu Loading Screen. Thanks for the quick answer.

> # If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by MidnightGrey on 2013-06-19
can you copy/paste the output to this:
```
cat /lib/plymouth/themes/default.plymouth
```

---

### Post by Reding on 2013-06-19
Here we go

> [Plymouth Theme]
Name=Ubuntu GNOME Remix Logo
Description=A theme that features a blue blinds animated background.
ModuleName=script


[script]
ImageDir=/lib/plymouth/themes/ubuntu-gnome-logo
ScriptFile=/lib/plymouth/themes/ubuntu-gnome-logo/ubuntu-gnome-logo.script


---

### Post by MidnightGrey on 2013-06-19
Looks like you've altered the default theme to *Ubuntu GNOME Remix Logo*.
You can set your theme by using this command:
```
sudo update-alternatives --config default.plymouth
```
The default ubuntu logo theme is called ubuntu-logo.

after choosing the theme use the following command to save changes.
```
sudo update-initramfs -u
```

---

### Post by Reding on 2013-06-19
Thanks a lot, the Ubuntu Loading Screen is back ! The gnome wallpaper disappeared as well :)

I still briefly have the blue fullscreen before the Ubuntu Loading Screen appears though.

---

### Post by MidnightGrey on 2013-06-19
> **Reding said:**
> I still briefly have the blue fullscreen before the Ubuntu Loading Screen appears though.

The blue screen is caused by GRUB loading silently. Your grub-script however does not show any indication of causing this so i am not sure what is happening.
You can try this code:
```
sudo update-grub
``` 
to rebuild grub and see if the blue screen goes away.

---

### Post by Reding on 2013-06-19
Wow, it worked !

Thanks a lot :)

---

### Post by Reding on 2013-06-26
Hey everybody, i'm back with the same problem but thime I can't solve it the way explained below.

Results after, [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/default/grub[/FONT][/COLOR]

> # If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
[COLOR=#000000][FONT=Ubuntu Mono]
And after

cat /lib/plymouth/themes/default.plymouth
[/FONT][/COLOR]
> [Plymouth Theme]Name=Ubuntu GNOME Remix Logo
Description=A theme that features a blue blinds animated background.
ModuleName=script


[script]
ImageDir=/lib/plymouth/themes/ubuntu-gnome-logo
ScriptFile=/lib/plymouth/themes/ubuntu-gnome-logo/ubuntu-gnome-logo.script


It seems like Ubuntu Gnome Remix is the UbuntuLogon Screen which is supposed to be seen after installing Ubuntu Gnome 13.04 but why isn't showing up. Worst case scenario, i'd be happy to have the default one.

I tried to restore it like taught before but it doesn't work, i get that message.

> There is only one alternative in link group default.plymouth (providing /lib/plymouth/themes/default.plymouth): /lib/plymouth/themes/ubuntu-gnome-logo/ubuntu-gnome-logo.plymouth
Nothing to configure.

Any ideas, thanks !

---

### Post by Reding on 2013-06-27
Up !

---

