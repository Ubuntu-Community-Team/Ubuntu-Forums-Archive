---
title: "Vista missing from dual boot"
date: 2013-11-08
forum: General Help
---

### Post by christon74 on 2013-11-08
Hello every Ubunter :)

I updated ubuntu this morning (**Ubuntu 12.04 LTS**). I had a partition with both **vista** **and Ubuntu.** It now seems vista has gone. I think I have done something wrong but I do not know what. Is there a 'restore' to previous state? How do I know my partition has been suppressed ? 
I really want to have _**both OS**_ on this machine. 
A million thanks in advance for useful tips.

Chris.

---

### Post by speartip on 2013-11-08
Updating Ubuntu, shouldn't affect Vista. Reading your post it looks like you are saying that Ubuntu & Vista are on the same partition. Is that correct or are they on separate partitions?
Assuming the later, try a simple: ```
sudo update-grub
``` Then reboot & see if Vista is still missing.

---

### Post by christon74 on 2013-11-08
Hello Speartip :)
There was a partition this morning. Something a bit complicated with slashes and 'dev6' or something like that. On start up it was possible to choose from several options : recovery mode, vista on dev6 etc.. Not any longer. Here are the results:
christophe@hp1:~$ sudo su
[sudo] password for christophe: 
root@hp1:/home/christophe# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-20-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-20-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Ubuntu 10.04.2 LTS (10.04) on /dev/sdb5
done
root@hp1:/home/christophe#

---

### Post by christon74 on 2013-11-08
Ok, I have just done that and Vista is still missing :(

---

### Post by christon74 on 2013-11-08
I mean that on startup it is only Ubuntu 12.04 loading by default. I can no longer see the page where I once had different options (previous versions of ubuntu/ recovery mode/ vista/ Memory test, etc....

---

### Post by speartip on 2013-11-08
Updating grub has seen Vista on /dev/sda1, so it looks like its still there.
When you reboot what are you seen in the grub menu?

---

### Post by christon74 on 2013-11-08
I am sorry I do not know what the grub menu is. Is it the different options you normally see diplayed on screen? If so, they  are no longer there.

---

### Post by speartip on 2013-11-08
OK. Our posts must have crossed. In a terminal run: ```
sudo gedit /etc/default/grub
```
On about the 9th line you will see "GRUB_TIMEOUT=XX".
Change it too "GRUB_TIMEOUT=10" without the "". Then run: ```
sudo update-grub
``` and reboot.

---

### Post by christon74 on 2013-11-08
christophe@hp1:~$ sudo su
[sudo] password for christophe: 
root@hp1:/home/christophe# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
root@hp1:/home/christophe#

---

### Post by speartip on 2013-11-08
You're posting too fast without giving anyone a chance to reply.
Follow my instructions in post #8, & see if that works.

---

### Post by christon74 on 2013-11-08
Should I  'apt-get install grub' as suggested? :confused:

---

### Post by christon74 on 2013-11-08
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
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

---

### Post by speartip on 2013-11-08
Please stop posting so fast. You're not giving me time to reply.
All looks good, so carry on following the instructions in post 8, & your issue will be solved.

---

### Post by christon74 on 2013-11-08
Thank you Speartip !!! it works, it works!! You really rock !!!=D>\\:D/

---

### Post by christon74 on 2013-11-08
I still have one more question though: Next time I update/upgrade Ubuntu using the terminal (because the other method does not always work) Is there a something (a line) in particular to which I should pay special attention?

---

### Post by speartip on 2013-11-08
> **christon74 said:**
> I still have one more question though: Next time I update/upgrade Ubuntu using the terminal (because the other method does not always work) Is there a something (a line) in particular to which I should pay special attention?
Not really. I don't really know what happened other than grub lost it's 10 second time out. I have had this happen occasionally, just keep that post handy in case it ever happens again.

---

