---
title: "Display resolution ratio choices"
date: 2016-04-15
forum: General Help
---

### Post by ray36 on 2016-04-15
Hi everyone. I recently installed xubuntu as dual-boot, after trying it a while in virtualbox and liking it a lot. The problem is, the display ratio is not right. My monitor is an acer p191w, the correct resolution should be 1440x900. The display choices are only 1280x1024, 1024x768, 800x600 and 640x480.  

I googled arounda bit and tried**  sudo xrandr -s **to set it properly, it just said "Size 1440x900 not found in available modes" to that one. I have tried xorg and both nvidia drivers available in additional drivers. Not sure what to try next. Seeing my screen squashed like this is giving me a headache lol. Thanks in advanced for any pointers.

---

### Post by echotech2 on 2016-04-16
Could it be the video card is not capable of that resolution?

---

### Post by howefield on 2016-04-16
Thread moved to the "*General Help*" forum.

---

### Post by him610 on 2016-04-16
Hello ray36. My monitor is similar, a Hanns-G HW19D, and I also have an nvidia gfx. Maybe we can provide a fix for you.
How about providing the results, enclosed within the code tags...
```
inxi -b
```
```
cat /etc/default/grub
```

---

### Post by ray36 on 2016-04-16
The program 'inxi' is currently not installed. You can install it by typing:
sudo apt-get install inxi


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


Thanks for taking the time to help by the way. My gfx card is a gtx960 in case that info would be helpful.

---

### Post by ray36 on 2016-04-16
Installed inxi now that I know what it is.

Kernel: 3.16.0-70-generic x86_64 (64 bit) 
           Desktop: Xfce 4.11.8 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: ASRock model: B75M-DGS R2.0 Bios: American Megatrends version: P1.20 date: 07/12/2013
CPU:       Quad core Intel Core i5-2500 CPU (-MCP-) clocked at 1605.656 MHz 
Graphics:  Card: NVIDIA GM206 [GeForce GTX 960] 
           X.Org: 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1440x900@59.9hz 
           GLX Renderer: GeForce GTX 960/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 352.63
Drives:    HDD Total Size: 3500.7GB (0.7% used)
Info:      Processes: 194 Uptime: 6 min Memory: 862.6/15989.0MB Client: Shell (bash) inxi: 1.9.17

After installing inxi and rebooting, it seems to have fixed itself somehow lol. I guess inxi is magic, or maybe it was from the apt-get upgrade I just ran. Not sure which.

---

### Post by him610 on 2016-04-16
Ok, we know what you have now. 
This line in your /etc/default/grub file, "#GRUB_GFXMODE=640x480" means that your gfxmode is set to auto. What we are going to do is try to force your monitor to 1440x900 resolution. Be careful you will be using 'sudo' to accomplish this. Note: this may or may not work for you.

With your editor of choice, open /etc/default/grub 
Find the line that reads, "#GRUB_GFXMODE=640x480"
Change it to read, "GRUB_GFXMODE=1440x900" (without the crunch and quotes)
Save the file and exit.
Execute *update-grub* then reboot

If all goes as expected, your display should now be set at 1440x900 resolution.

---

