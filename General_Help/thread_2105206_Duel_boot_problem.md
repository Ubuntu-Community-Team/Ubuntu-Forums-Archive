---
title: "Duel boot problem"
date: 2013-01-15
forum: General Help
---

### Post by maxalman on 2013-01-15
Hi, I have a Dell Inspirion 600 running Windows xp and duel booting Ubuntu 12.10
I am new to linux and I think I have messed something up because when i get my duel boot screen and I click on Ubuntu it doesn't boot up as it used to, I now get a page of numbers and writing which clears and then gives me a page with this message.
fsck from untill Linux 2.20.1 /dev/sda5, clean 390863/1823248 files, 4890064/7278848 blocks. mount: wrong fs type, bad option, bad superblock on/remote ip/remote-dir
Mountall: mount media/remote/remotemachine(479)terminated with status 32
The disk drive for /media/nfts is not ready or present. 
Keys: continue to wate, or press s to skip mounting or m for manual recovery.

I press S and Ubuntu loads and works ok, but I would like to get back to the way it was before ie: select Ubuntu on the boot screeen and loads automatically. 
Can anyone help me please to resolve this problem, thanks

---

### Post by mikewhatever on 2013-01-16
Can you post the output of **cat /etc/fstab**. It looks like you try auto-mounting partitions that don't exist, which, of cause, produce errors.

---

### Post by maxalman on 2013-01-16
> **mikewhatever said:**
> Can you post the output of **cat /etc/fstab**. It looks like you try aoto-mounting partitions that don't exist, which, of cause, produce errors.

alan@alan-Inspiron-6000:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=f2e7671d-ab51-4b0b-967f-8ea2657bac82 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=18f79797-e2ee-44a9-9456-3f76f295f697 none            swap    sw              0       0
UUID=791957C576AE1E67 /media/ntfs ntfs umask=000,utf8 0 0
//remoteIP/remote-dir /media/remotemachine cifs credentials=/etc/samba/cred,noperm,uid=1000,gid=1000 0 0
alan@alan-Inspiron-6000:~$
Thanks, I hope this helps you to resolve my problem.

---

### Post by mikewhatever on 2013-01-16
Thank you for the output. In a terminal window, run **gksu gedit /etc/fstab** and comment out the last two lines, then save and exit. The end result should look like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda5 during installation
UUID=f2e7671d-ab51-4b0b-967f-8ea2657bac82 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=18f79797-e2ee-44a9-9456-3f76f295f697 none swap sw 0 0
#UUID=791957C576AE1E67 /media/ntfs ntfs umask=000,utf8 0 0
#//remoteIP/remote-dir /media/remotemachine cifs credentials=/etc/samba/cred,noperm,uid=1000,gid=1000 0 0
```

That should take care of the boot time errors.

---

### Post by maxalman on 2013-01-16
Hi thanks, here is a copy of cat /etc/fstab after I did what you said, does this look right now?
There is an improvement I still get the rolling screens with numbers and writing after clicking on Ubuntu on the purple screen but I don't have to press S to skip or M for manual recovery option, and Ubuntu now starts on its own, also when I shut down my laptop I get lots of numbers and writing rolling down the screen.

  alan@alan-Inspiron-6000:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=f2e7671d-ab51-4b0b-967f-8ea2657bac82 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=18f79797-e2ee-44a9-9456-3f76f295f697 none            swap    sw              0       0
#UUID=791957C576AE1E67 /media/ntfs ntfs umask=000,utf8 0 0
#//remoteIP/remote-dir /media/remotemachine cifs credentials=/etc/samba/cred,noperm,uid=1000,gid=1000 0 0 
alan@alan-Inspiron-6000:~$

---

### Post by mikewhatever on 2013-01-16
Yep, that looks alright. As for the screes with numbers and writings, that is purely cosmetic, but let's look at the output of **cat /proc/cmdline** anyway. Perhaps we can do something about it.

---

### Post by maxalman on 2013-01-16
> **mikewhatever said:**
> Yep, that looks alright. As for the screes with numbers and writings, that is purely cosmetic, but let's look at the output of **cat /proc/cmdline** anyway. Perhaps we can do something about it.

Here you go,
alan@alan-Inspiron-6000:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-21-generic root=UUID=f2e7671d-ab51-4b0b-967f-8ea2657bac82 ro =1
alan@alan-Inspiron-6000:~$ 

Alan

---

### Post by mikewhatever on 2013-01-16
Exellent! Thank you for such a prompt reply.
Please run **gksu gedit /etc/default/grub**, and find the folloing line:
```
GRUB_CMDLINE_LINUX_DEFAULT=""

```

Add the two words, **quiet splash**, in between the quotes. Save and exit, and then run **sudo update-grub**.

You should not see the boot sequence any more.

---

### Post by maxalman on 2013-01-17
> **mikewhatever said:**
> Exellent! Thank you for such a prompt reply.
Please run **gksu gedit /etc/default/grub**, and find the folloing line:
```
GRUB_CMDLINE_LINUX_DEFAULT=""

```Add the two words, **quiet splash**, in between the quotes. Save and exit, and then run **sudo update-grub**.
 
You should not see the boot sequence any more.
 
Here is the result after editing and applying sudo update-grub
 
[FONT=Times New Roman][SIZE=3]alan@alan-Inspiron-6000:~$ sudo update-grub[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Generating grub.cfg ...[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found linux image: /boot/vmlinuz-3.5.0-21-generic[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found initrd image: /boot/initrd.img-3.5.0-21-generic[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found linux image: /boot/vmlinuz-3.5.0-17-generic[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found initrd image: /boot/initrd.img-3.5.0-17-generic[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found memtest86+ image: /boot/memtest86+.bin[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found Microsoft Windows XP Home Edition on /dev/sda1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]done[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]alan@alan-Inspiron-6000:~$ [/FONT][/SIZE]
 
And here is what my default grub looks like now.
 
[SIZE=3][FONT=Times New Roman][FONT=Times New Roman]GRUB_DEFAULT="4"[/FONT][/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman]#GRUB_HIDDEN_TIMEOUT="0"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_HIDDEN_TIMEOUT_QUIET="true"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_TIMEOUT=10[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_CMDLINE_QUIET_SPLASH_LINUX_DEFAULT="=1"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_CMDLINE_LINUX=""[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# This works with Linux (no patch required) and with any kernel that obtains[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Uncomment to disable graphical terminal (grub-pc only)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_TERMINAL="console"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# The resolution used on graphical terminal[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# note that you can use only modes which your graphic card supports via VBE[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# you can see them in real GRUB with the command `vbeinfo'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_GFXMODE="640x480"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT][/SIZE]
[SIZE=3] [/SIZE][/FONT]
I am sorry to say that I still see the boot sequence when loading and shutting down.
Alan

---

### Post by mikewhatever on 2013-01-17
Strange, but I don't know what ** GRUB_CMDLINE_QUIET_SPLASH_LINUX_DEFAULT="=1"** does. I also can not find any reference to it online. Any idea how it got there?

Try commenting it out like this:
```
# GRUB_CMDLINE_QUIET_SPLASH_LINUX_DEFAULT="=1"
```

...and paste **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** instead.

Run **sudo update-grub** when done.

---

### Post by maxalman on 2013-01-17
> **mikewhatever said:**
> Strange, but I don't know what **GRUB_CMDLINE_QUIET_SPLASH_LINUX_DEFAULT="=1"** does. I also can not find any reference to it online. Any idea how it got there?
 
Try commenting it out like this:
```
# GRUB_CMDLINE_QUIET_SPLASH_LINUX_DEFAULT="=1"
```
 
...and paste **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** instead.
 
Run **sudo update-grub** when done.
 
Sorry my mistake I miss understood you, I have now done what you said and it start and stops ok now thank you.
Should there be a hash infront of all the GRUB
 
[FONT=Times New Roman][SIZE=3]GRUB_DEFAULT="4"[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]#GRUB_HIDDEN_TIMEOUT="0"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_HIDDEN_TIMEOUT_QUIET="true"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_TIMEOUT=10[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_CMDLINE_LINUX=""[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# This works with Linux (no patch required) and with any kernel that obtains[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Uncomment to disable graphical terminal (grub-pc only)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_TERMINAL="console"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# The resolution used on graphical terminal[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# note that you can use only modes which your graphic card supports via VBE[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# you can see them in real GRUB with the command `vbeinfo'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_GFXMODE="640x480"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_DISABLE_LINUX_UUID="true"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Uncomment to disable generation of recovery mode menu entries[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_DISABLE_RECOVERY="true"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Uncomment to get a beep at grub start[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]#GRUB_INIT_TUNE="480 440 1"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]GRUB_SAVEDEFAULT="false"GRUB_GFXPAYLOAD_LINUX=None[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]GRUB_GFXPAYLOAD_LINUX=None[/FONT][/SIZE]
 
Alan

---

### Post by mikewhatever on 2013-01-17
> **maxalman said:**
> Sorry my mistake I miss understood you, I have now done what you said and it start and stops ok now thank you.
Should there be a hash infront of all the GRUB


No! The '#' symbol makes the system ignore that particular line (as if it was a comment).

---

### Post by maxalman on 2013-01-17
> **mikewhatever said:**
> Oh well, you've asked about reinstalling in [another thread]("http://ubuntuforums.org/showthread.php?t=2105337"), and may be now is a good time to apply that solution. It's somewhat drastic, but you'll, hopefully, get a clean system no one had messed around with.
 
 
Sorry I was updating my reply to you can you check it please.
 
Thanks Alan

---

### Post by maxalman on 2013-01-17
> **mikewhatever said:**
> No! The '#' symbol makes the system ignore that particular line (as if it was a comment).
 
Ok, thank you very much for all your help I do a appreciate it you are a life saver.
 
:)

---

### Post by mikewhatever on 2013-01-17
> **maxalman said:**
> Ok, thank you very much for all your help I do a appreciate it you are a life saver.
 
:)

Glad I could help, and see you around. ;)

---

