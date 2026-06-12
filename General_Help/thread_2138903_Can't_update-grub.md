---
title: "Can't update-grub"
date: 2013-04-25
forum: General Help
---

### Post by caffeinated blood on 2013-04-25
I can't edit the /etc/default/grub file and use the 'update-grub' command successfully. When I do I get the response '/usr/sbin/grub-mkconfig: 11: /etc/default/grub: --: not found' ,even though the edited file has been saved. However, if I run the 'update-grub' command prior to editing the file it works properly. 

I am running Ubuntu 12.04 alongside Windows 7 and I want to set W7 as the default OS. Not working! Also tried the command 'grub-mkconfig -o /boot/grub/grub.cfg' and get the same response.

---

### Post by ajgreeny on 2013-04-25
Let's see the output of ```
cat /etc/default/grub
``` to make sure firstly that you have such a file, and secondly to see if its content is correct.

---

### Post by caffeinated blood on 2013-04-25
ajgreeny, here is the output of 'cat /etc/default/grub'

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

---

### Post by oldfred on 2013-04-26
It is early morning in England, so AJ may not be up.

I do not see anything. 
Is this before or after you have edited it?

Grub has gotten more particular about typos and even some applications, not sure about grub, consider extra spaces at the end of a line or extra blank lines at the end as errors which we cannot see.

---

### Post by ajgreeny on 2013-04-26
It all looks good to me as well, but can you repost the whole file again, but this time using the code tags in the toolbar of the reply window.

Copy the file to your reply, highlight the whole pasted text, including any empty lines or spaces, and then click on the # in toolbar.

PS: @ oldfred.

I have an empty line at the end of my /etc/default/grub file, which must have been there at installation time, and certainly does not have any effect on its use; update-grub works fine for me.

---

### Post by caffeinated blood on 2013-04-27
Here is the full output of the requested command. When I edit this file the changes I make will be saved, but 'update-grub' command always returns the 'not found' response. Yet, if I run 'update-grub' with the original/unedited file the command WILL update-grub.```
steve@PC2010:~$ cat /etc/default/grub
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
steve@PC2010:~$ 

```

---

### Post by dino99 on 2013-04-27
finding the issue reason(s) can be a pain sometimes; so open synaptic and purge everything related to grub
then with nautilus, be sure there is no more *grub* or menu.lst (legacy grub) around

finally reinstall grub-pc

---

### Post by caffeinated blood on 2013-04-27
dino99: Are you suggesting I purge anything related to  grub version 1.99-2 installed showing in synaptic?

May this issue I'm having possibly have to do with the fact that I have grub installed in the MBR instead of the / partition or a /boot partition(did not create one during installation)?

---

### Post by dino99 on 2013-04-27
yes i mean the installed ones inside synaptic (indeed dont shutdown at that time)
grub is installed into the MBR with bios system, can be different with uefi/gpt (see the grub link below)

---

### Post by caffeinated blood on 2013-04-27
dino99: I removed/reinstalled grub-pc/grub-common using synaptic. I searched for grub on the file system and had about 20 files/folders showing in various locations, but was unable to delete/remove them. Thought I should have used teminal to manually get rid of them, but wasn't sure.

After reinstalling grub-pc/grub-common I am still having the same issue. Again, if I install grub in the / partition do you think this would make a difference?

---

### Post by dino99 on 2013-04-27
installing into the partition is not the default grub choice and might be avoided.
Why have you so many related grub files across the system ? is that due to multi distro installation ? (by the way, restart with something clean (sudo rm ...)

or try:
sudo dpkg-reconfigure grub-pc  (to set it into mbr only)

note: do you clean the system from time to time ? (clean/autoclean/autoremove/gtkorphan/bleachbit)

---

### Post by caffeinated blood on 2013-04-27
dino99: I have no idea why there are so many file/folders for grub on my system - this is a FRESH and clean install. Yes, I normally clean my system. Tried your most recent suggestion - didn't work.

---

