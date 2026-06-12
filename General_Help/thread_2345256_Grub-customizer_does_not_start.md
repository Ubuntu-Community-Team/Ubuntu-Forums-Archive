---
title: "Grub-customizer does not start"
date: 2016-12-02
forum: General Help
---

### Post by Macamba on 2016-12-02
I installed grub-customizer like:```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

Now I want to change the boot order in my boot menu, so next step is:```
gksu grub-customizer
```

What happens is a login window appears where I have to enter my password. After entering my password and pressing enter the login window disappears and for the rest nothing happens. I'm back in my terminal, one line below the code to start the customizer. What gives?

---

### Post by kingneutron on 2016-12-02
--Try ' sudo grub-customizer ' and additionally, check to see if the window popped up on another virtual desktop? Also, (I don't know if you tried this) but I found that you can't put grub-customizer in the background with an '&' - it's a foreground-only program. Sudo is the way I launch it.

---

### Post by ajgreeny on 2016-12-02
> **kingneutron said:**
> --Try ' sudo grub-customizer ' and additionally, check to see if the window popped up on another virtual desktop? Also, (I don't know if you tried this) but I found that you can't put grub-customizer in the background with an '&' - it's a foreground-only program. Sudo is the way I launch it.
**NO! Do not use sudo for any GUI application, ever!**
You may find if you do so for some GUI applications that the ownership of certain files and folders in your home, which must be owned by you, are suddenly owned by root; if that happens you could find yourself unable to login as user.

You can either install the gksu package, which I assume you must already have done, which has now been deprecated but still works and use command ```
gksudo grub-customizer
``` or you can alternatively use command ```
sudo -H grub-customizer
``` both of which are safe to use.

I have never bothered with grub-customiser and make any edits to grub manually, so I have no experience of it as an application in use.

---

### Post by Macamba on 2016-12-03
After:```

sudo add-apt-repository ppa:adabbas/1stppa
sudo apt-get update
sudo apt-get install grub-customizer
```
I found out that:```

E: Unable to locate package grub-customizer

```

So I did not download it. Earlier this week I also installed Ubuntu 16.04 LTS and ran the installation and subsequent grub-customizer without a hitch. Anyone know what gives?

---

### Post by Macamba on 2016-12-04
@ ajgreeny

You said you manually edit grub. I looked around and found out that is possible with:```
sudo gedit /etc/default/grub
```

A grub (text?) editor opens. I see no entry for either Linux or Windows 10. So what should I change to get Windows 10 the first entry, and Linux the second?

The grub text file looks like:```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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
```

Not to self, do not forget a ```
update-grub
```afterwards.

---

### Post by ajgreeny on 2016-12-04
> **Macamba said:**
> @ ajgreeny

You said you manually edit grub. I looked around and found out that is possible with:```
sudo gedit /etc/default/grub
```

A grub (text?) editor opens. I see no entry for either Linux or Windows 10. So what should I change to get Windows 10 the first entry, and Linux the second?

The grub text file looks like:```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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
```

Not to self, do not forget a ```
update-grub
```afterwards.
There still are a few sites that tell users to run command **sudo gedit /filename** but they are incorrect, I'm afraid.
Please do not get into the habit of using **sudo** for any GUI app, including gedit; you will probably get away with it many times with some applications but you will almost certainly eventually lock yourself out of the system (see my last post) if you continue to use sudo for a few others of them. Either use **gksudo** or **sudo -H** instead.

I will have to deal with the manual edits of the file to get Windows or other OS as first boot OS later as I have no time at present, but I will point you to [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) which has a lot of info on how to edit that file.   See you later.

EDIT:
The part you want to read and act on is:-
```
GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric or "saved"

    GRUB_DEFAULT=0 - Sets the default menu entry by menu position. As Grub Legacy, the first "menuentry" in grub.cfg is 0, the second is 1, etc.
    GRUB_DEFAULT=saved - (Grub 1.98) Enables the "grub-reboot" and "grub-set-default" commands.
        This setting allows the use of the following commands to set a default OS. The default OS will not be set merely by an interactive selection of an OS from the menu.
        grub-set-default. Sets the default boot entry until changed.
            The format is "sudo grub-set-default X, with X being the menuentry position (starting with 0 as the first entry) or the exact menu string. Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.32-15-generic"
            To obtain the existing menuentry choice number (starting from 0) or the menuentry "string", run "grep menuentry /boot/grub/grub.cfg"

        grub-reboot. This command sets the default boot entry for the next boot only. The format of the command is the same as for "grub-set-default" (see above).
        For an example of how to enable the "saved" option with a custom menu, see the "Custom User Entries" section.

    GRUB_DEFAULT="xxxx" - An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"


GRUB_SAVEDEFAULT=true * If set to true this setting will automatically set the last selected OS from the menu as the default OS on the next boot. No commands need be run to set the default OS. For this entry to work, the GRUB_DEFAULT entry should be set to saved.
```
I have never needed to change the OS that I boot as default from the menu so I have no experience of what you want to do but it looks as if you need to edit the line to [COLOR="#FF0000"]GRUB_SAVEDEFAULT=true[/COLOR] and add [COLOR="#FF0000"]GRUB_DEFAULT=saved[/COLOR] to your file, then run **sudo update-grub**.

---

### Post by Macamba on 2016-12-05
@ ajgreeny: Thanks for your information. I've been playing around with it, but in the end decided to search the internet on the error message
> E: Unable to locate package grub-customizer

In the post [Ubuntu 16.04 - Can't install grub customizer]("http://askubuntu.com/questions/761563/ubuntu-16-04-cant-install-grub-customizer") user "K. Eoe" answered with
> This package does not appear in the default repositories. This is the PPA.

In short:
```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

This was another repository then my "ppa:launcpad-daily/ppa". I tried installing grub-customizer from this repository and succeeded in updating my grub menu.

---

