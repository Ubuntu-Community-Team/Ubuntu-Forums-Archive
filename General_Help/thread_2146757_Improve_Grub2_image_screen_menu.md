---
title: "Improve Grub2 image screen menu"
date: 2013-05-19
forum: General Help
---

### Post by gilloz on 2013-05-19
Prior to doing a clean install of my Windows 7 OS, my dual boot Ubuntu Grub2 menu screen looked pretty much normal as in past installations.  Now, the menu is wider, more spaces between letters and the border line is a broken dash line.  See enclosed image.  I have tried varies screen resolutions, font sizes and I am unable to get it back to the "normal" looking screen image.  Any help would be appreciated.  Thanks.

[IMG]http://imageshack.us/user/gilphilloz[/IMG]

Grub 2 menu shown below:


Grub2  Ver. 1.99


# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. 
# For full documentation of the options in this file, see: 
#   info -f grub -n 'Simple configuration' 

GRUB_DEFAULT="5" 
#GRUB_HIDDEN_TIMEOUT="0" 
GRUB_HIDDEN_TIMEOUT_QUIET="true" 
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
GRUB_GFXMODE="800x600" 

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
#GRUB_DISABLE_LINUX_UUID="true" 

# Uncomment to disable generation of recovery mode menu entries 
#GRUB_DISABLE_RECOVERY="true" 

# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1" 



export GRUB_COLOR_NORMAL="light-gray/black" 
export GRUB_COLOR_HIGHLIGHT="light-magenta/black" 

#UNNAMED_OPTION="" 
GRUB_FONT="/boot/grub/unicode.pf2"

---

### Post by ajgreeny on 2013-05-19
Try commenting out the line [B]
GRUB_GFXMODE="800x600"[/B]
with a # at the start to see if that helps.

---

### Post by gilloz on 2013-05-19
Thanks ajgreeny for your response.  Commenting out that line made the Grub2 menu extremely large font and made it difficult to see what line I was choosing.  Kinda like going from font 12 to font 36.

---

### Post by gilloz on 2013-05-20
OK.  I have solved my problem.  I downloaded a file showing what a normal standard Grub2 menu should look like for version 1.99 and I edited my grub file to match it.  Problem solved.

---

### Post by ajgreeny on 2013-05-20
So show us what the solution is, please.

It may help users in future.

---

