---
title: "Can no longer boot with HDMI dongle"
date: 2022-10-29
forum: General Help
---

### Post by icach0 on 2022-10-29
Hi, I'm running Ubuntu 22.04 on my home server. It doesn't have a monitor plugged in but it does have one of those headless HDMI display dongle emulators or whatever they're called. That used to work flawlessly until a few days ago. 

Now, if the computer has a real monitor plugged in it boots without a hitch. But if the headless dongle is plugged in it won't boot at all. Or at least I assume since SSH and RDP aren't working. If I connect the real monitor again and hard reset it works.

After getting into the Ubuntu desktop, I can swap the monitor for the HDMI dongle and everything works until I reboot or shutdown. It also won't finish the shutdown when the HDMI dongle is plugged in.

I'm almost sure the problem appeared when I decided to update grub (had an older version from a previous install).

Tried this method which seemed to work for some people but didn't work for me [https://www.reddit.com/r/Ubuntu/comments/v0ff1r/ubuntu_2204_server_wont_boot_without_hdmi_plugged/](https://www.reddit.com/r/Ubuntu/comments/v0ff1r/ubuntu_2204_server_wont_boot_without_hdmi_plugged/)

Please let me know if I need to post additional information.

Any help would be highly appreciated.

Edit: Added /etc/default/grub code below.

---

### Post by MAFoElffen on 2022-10-29
Please post your /etc/default/grub file within Code Tags.

---

### Post by icach0 on 2022-10-29
```


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console


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

### Post by MAFoElffen on 2022-10-29
Please make these changes:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]-- nomodeset 3[/COLOR]"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console


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
Then after modified and saved:
```

sudo update-grub

```

---

### Post by icach0 on 2022-10-29
Thanks again for the reply!

I did as you suggested but then as soon as Ubuntu started booting video stopped completely. I plugged in the HDMI into the iGPU HDMI and to my surprise the computer was waiting at a console login. So I was able to revert back for the time being.

I'm sorry for not mentioning it sooner, I'm using a dedicated GPU (Nvidia 660Ti), I'm guessing that is relevant now. Using Nvidia driver 470.141.03

---

### Post by MAFoElffen on 2022-10-30
That is why "nomodeset" would help... "3" puts it into runlevel 3, console only (no graphics).

---

### Post by icach0 on 2022-10-31
Ubuntu was set to auto-login using the desktop environment and the dedicated GPU. But when I used the nomodeset 3 option it just sat waiting at the login window. How can I get it to load the desktop environment and login automatically again? Will dedicated graphics work once in the desktop? Thanks again for your help!

---

### Post by MAFoElffen on 2022-10-31
For server / console=only, do this:
```
sudo systemctl edit getty@tty1.service
``` 

  This will the create a blank getty service file (if neccessary... meaning if it doesn't exist, it will create it and it's structure) and open it an editor. Add the following, **replacing [COLOR=#ff0000]user_name[/COLOR] with your user name**:
```

[Service]
ExecStart=
ExecStart=-/sbin/agetty --noissue --autologin [COLOR=#ff0000]user_name[/COLOR] %I $TERM
Type=idle

```
  This will:

  
[LIST]
[*]Create the folder /etc/systemd/system/getty@tty1.service.d if necessary 
[*]Create the file /etc/systemd/system/getty@tty1.service.d/override.conf if necessary 
[/LIST]
     
This will autologin the User that you edited that getty service file for... with that [COLOR=#ff0000]user_name[/COLOR] that you put into that service file.

---

