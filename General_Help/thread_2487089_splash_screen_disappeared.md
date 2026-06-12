---
title: "splash screen disappeared"
date: 2023-05-22
forum: General Help
---

### Post by bayou2 on 2023-05-22
Hi!

boot splash screen disappeared.
I do not know how to fix it.
I need your instructions.
Please.

lubuntu22.04   64bit    Dell Vosto1015

---

### Post by ne29914 on 2023-05-22
I think you need to provide a bit more detail.

---

### Post by guiverc on 2023-05-23
I'm not sure what is being asked either, but I'll provide the following

I assume by SPLASH screen you mean the Lubuntu plymouth screen, our logo in circle with circling/flashy type effect; the plymouth screen(s) are there to hide boot messages without just leaving you with a blank screen

Online support articles can be useful, eg. [https://askubuntu.com/questions/2007/how-do-i-change-the-plymouth-bootscreen](https://askubuntu.com/questions/2007/how-do-i-change-the-plymouth-bootscreen)

I had a quick look at the page, and first answer uses `aptitude` which I have installed on my box as I like its interactive capability, but you don't need it as the command `apt search plymouth-theme` will show the same detail (you just have to scroll up/down more as more detail is shown with blank lines between).

If you installed another plymouth screen, and don't like it, thus what you're asking is just how to change back, the following commands maybe what you're looking for

```

sudo update-alternatives --config default.plymouth

sudo update-initramfs -u

```

*Additional [picture] detail on plymouth screen:*
I searched online & found a picture here ([https://phab.lubuntu.me/T131](https://phab.lubuntu.me/T131))  which contains a link to this photo image ([https://photos.app.goo.gl/NWoNK7FxfxW5EKrC7](https://photos.app.goo.gl/NWoNK7FxfxW5EKrC7)) ... it'll look similar today (*not identical depending on your hardware as OEM logo can also now show*)

---

### Post by bayou2 on 2023-05-23
thank you , and sorry for my poor english.
 
when i boot lubuntu , splash screen (plymouth) does not appear , 
and many characters start flowing on the black console screen.
                                                    (some detailed descriptions)
and then , openbox start as ever.
when i shut down or reboot pc , splash screen (plymouth) does not appear , too .
so, there are no ploblems for using lubuntu(openbox) except this. except tjis.

---

### Post by guiverc on 2023-05-23
There can be many reasons for this, as I tried to cover in my prior post, you may have selected another `plymouth` screen which can be changed back using the commands provided in the prior step.

(FYI:  I boot a *live* Lubuntu [22.04.3* daily*] system as it is a quick way for me to see a generally unmodified system, it shows 3 choices at the `update-alternatives` dialog, my own system I'm using to reply shows many more as I've bloated my box down with other desktops)

You may also have modified your config to **not** show any plymouth at all; to check this I'd likely on next boot hit the <**E**> key to *EDIT* the grub entry and see if you see the values "quiet splash" on the linux kernel line. If they aren't there, you won't see the *plymouth splash* screen, and you've maybe made a change in /etc/grub.d/, or used `plymouth-disabler` which adds .override files to your system that prevent plymouth from running. I don't know what you may have done to prevent plymouth, so I'm guessing here (*I'd try and think back to what was done in the last session **before*** *it disappeared for clues; package installs can be explored via /var/log/apt/history.log, commands via .bash_history etc, even file timestamps can be searched for changes around a time/date but you do need to know roughly when change(s) were made*.

---

### Post by bayou2 on 2023-05-24
thank you for your kindness.
i tried this. &#65381;&#65381;&#65381;&#65381;&#65381;
    sudo gedit /etc/initramfs-tools/conf.d/splash[COLOR=#434A54][FONT=sans-serif] 
[/FONT][/COLOR]         wrote this and saved. &#65381;&#65381;&#65381;&#65381;&#65381;
&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;FRAMEBUFFER=y
    sudo update-initramfs -u
    
but this wasn't work.



i guess it has happend because of </etc/default/grub> &#65381;&#65381;&#65381;&#65381;&#65381;

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="saved"
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
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
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER="false"


GRUB_SAVEDEFAULT="true"
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-blue/black"
export GRUB_MENU_PICTURE="/usr/share/backgrounds/DELL/wp6836039-dell-computer-wallpapers.jpg"


&#65381;&#65381;&#65381;&#65381;&#65381;&#12288;i will try something more .

thank you.

---

