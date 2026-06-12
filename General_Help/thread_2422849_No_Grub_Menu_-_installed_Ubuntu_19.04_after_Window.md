---
title: "No Grub Menu - installed Ubuntu 19.04 after Windows 10"
date: 2019-07-13
forum: General Help
---

### Post by Hyenaz on 2019-07-13
Hello,

I have a new Lenovo Thinkpad T440p which had Windows 10 preinstalled.

I installed Ubuntu 19.04 - the installation was easy but I can never see the Grub menu - even after running boot repair and installing a low latency kernel.

Here is the boot repair report: [http://paste.ubuntu.com/p/Z7K5vrNfZ2/](http://paste.ubuntu.com/p/Z7K5vrNfZ2/)

It is still possible for me to access Windows by hitting F12 at the bios screen and selecting the windows boot loader from there. Nevertheless sometimes Grub is useful to me so I would like to have it available.

Any help you can provide would be awesome. Thank you !

Adrienne

---

### Post by oldrocker99 on 2019-07-13
OK, here's how. Open a text editor. I use nano, already installed. Do this.
```
sudo nano /etc/default/grub
```
Nano doesn't act like other text editors, but every command is in the margins. To save, it's CTRL-O for Write (O)ut, for example. I use it because it's fast and effective.

You'll see this:
```
GRUB_DEFAULT=0
#GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
The GRUB_TIMEOUT=0 line should have '#' at the beginning, as shown above. Finish up by entering this:
```
sudo update-grub
```
Reboot, and you're done.

Hope this helps.

---

### Post by oldfred on 2019-07-13
So both Ubuntu & Windows boot ok, but you just do not have grub menu?

Have you tried:
sudo update-grub

But the fixes by boot-Repair should have also run that.

---

### Post by Hyenaz on 2019-07-18
Hi i have tried sudo update-grub  - it doesn't do anything.

Also the line "#GRUB_TIMEOUT=0" was not commented, but it was "GRUB_TIMEOUT=10", so I changed it to what you suggested - but it made no difference. I go from the Lenovo logo straight to Ubuntu

Here is my current grub file:
> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT=0
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

any other ideas?

x

A

---

### Post by oldfred on 2019-07-18
I use
GRUB_TIMEOUT=3

If you have it set to 0, then grub menu never shows. And it can be difficult to even use escape key if UEFI or shift key if BIOS to get grub menu as it is not shown. 

My use of 3 means I have to be quick if I want menu, but can get it. Default is 10 for 10 sec.

---

### Post by Hyenaz on 2019-07-18
Hi Oldfred

It was 10 before, now it's 0, and I just tried 3. No difference. Just the Lenovo logo for quite a long time and then Ubuntu boots.

---

### Post by Hyenaz on 2019-08-02
Hi. I solved the problem and am documenting it for other users.
You need to enable CSM support in the bios
1) Enter bios (hitting enter and pressing F1 on my Thinkpad T440p)
2) Go to Startup Menu
3) Under CSM support select "YES".

See attached image: [URL="https://ibb.co/QMWWkX9"]https://ibb.co/QMWWkX9


[/URL]

---

