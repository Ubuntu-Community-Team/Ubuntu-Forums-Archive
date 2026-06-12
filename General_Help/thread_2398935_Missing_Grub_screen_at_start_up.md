---
title: "Missing Grub screen at start up"
date: 2018-08-19
forum: General Help
---

### Post by palimmo on 2018-08-19
Hi.
My system starts up, skips the grub screen, where I can (if needed) choose different kernels and options, and boots immediately Xubuntu 18.04.
I have no dual boot system but I want the grub screen anyway.
How can I restore it?
Thanks!

---

### Post by oldfred on 2018-08-19
If UEFI, you have to press Escape key (perhaps more than once) after UEFI and before grub would normally load. If UEFI fast boot on, you may not have time to press any key as it immediately boot. Often then cold boot nor warm reboot works.

If BIOS you press and hold shift key from BIOS until menu appears.

---

### Post by palimmo on 2018-08-19
It is an old pc, with no uefi.
After entering the bios, what should I do?

---

### Post by oldfred on 2018-08-19
To see grub you do not need to go into BIOS.
Just a reboot and hold shift key from the normal BIOS start up screen until grub menu appears.

---

### Post by palimmo on 2018-08-19
Great, thanks.
How to set it permanently, so that I have as usual a few seconds to choose what to boot?
Thanks

---

### Post by oldfred on 2018-08-19
I always have had multiple boots, so I set timeout to 3 sec just to not have grub menu for long.

       sudo nano /etc/default/grub 
    sudo update-grub

See this section, but also see issues at bottom. Comment this line out:
       GRUB_HIDDEN_TIMEOUT=0 
    [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

---

### Post by ajgreeny on 2018-08-19
You can edit the file /etc/default/grub (as root) and then run **sudo update-grub** to ensure that the grub menu shows at each boot which I have done on my main system.
I'm away from that machine this week and can  not remember exactly the changes you need but as soon as I'm back to that machine I will post my file content for you, but it is really simply changing the lines telling grub what to show to something like:-
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5  #(I have this et to 2 seconds only)
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="Lubuntu 18.04 Bionic" #(This line is changes to show the real OS name instead of default)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="" 
```
I think I may have missed a line in this but it will still work, I believe, though can be tweaked a little more.

---

### Post by palimmo on 2018-08-20
This is my output. Grub isn't showed yet (only if I press the shift button)
I do not have any *HIDDEN* option ... but *GRUB_TIMEOUT_STYLE=hidden* 
:confused: 

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
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
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by tea for one on 2018-08-20
> **palimmo said:**
> This is my output. Grub isn't showed yet (only if I press the shift button)
I do not have any *HIDDEN* option ... but *GRUB_TIMEOUT_STYLE=hidden* 
:confused: 

You still need to edit and save the grub file.

```
sudo nano /etc/default/grub
```

Put a comment # at the beginning of the line i.e. [B]#GRUB_TIMEOUT_STYLE=hidden
[/B]
If you wish for grub menu to display for longer, then change the next line from 5 seconds to, say 10 seconds i.e.**GRUB_TIMEOUT=10**

Example below:-

```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Please remember to run ```
sudo update-grub
``` to apply the changes.

---

### Post by ajgreeny on 2018-08-20
Please do not use **sudo** alone for GUI applications; you are possibly safe using gedit but other applications used that way may completely lock you out of your user account by changing ownership of files in your /home to root.
See Root-Sudo in my signature below for details

Either use the command line editor with ```
sudo nano /etc/default/grub
``` or if you prefer to use gedit use command ```
sudo -H gedit /etc/default/grub
``` which will not affect file ownership.

---

### Post by tea for one on 2018-08-20
> **ajgreeny said:**
> Please do not use **sudo** alone for GUI applications; you are possibly safe using gedit but other applications used that way may completely lock you out of your user account by changing ownership of files in your /home to root.
See Root-Sudo in my signature below for details

Either use the command line editor with ```
sudo nano /etc/default/grub
``` or if you prefer to use gedit use command ```
sudo -H gedit /etc/default/grub
``` which will not affect file ownership.

Thank you for the reminder, I've amended my post.

---

### Post by palimmo on 2018-08-24
great. thanks!

---

### Post by marko-ambrozic on 2019-01-10
> **tea for one said:**
> You still need to edit and save the grub file.

```
sudo nano /etc/default/grub
```

Put a comment # at the beginning of the line i.e. [B]#GRUB_TIMEOUT_STYLE=hidden
[/B]
If you wish for grub menu to display for longer, then change the next line from 5 seconds to, say 10 seconds i.e.**GRUB_TIMEOUT=10**

Example below:-

```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Please remember to run ```
sudo update-grub
``` to apply the changes.

You need to remove quiet splash from line GRUB_CMDLINE_LINUX_DEFAULT if you want to see boot process in terminal
My /etc/default/grub is like this:

GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT=""**
GRUB_CMDLINE_LINUX="yes"

Bye

---

