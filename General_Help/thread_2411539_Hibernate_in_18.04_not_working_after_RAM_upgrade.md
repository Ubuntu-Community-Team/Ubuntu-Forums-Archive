---
title: "Hibernate in 18.04 not working after RAM upgrade"
date: 2019-01-31
forum: General Help
---

### Post by steve234 on 2019-01-31
Hi all,

I'm a bit stuck with getting hibernate (systemctl hibernate) to work on my 18.04 system. It is a laptop which I use for work, and the daily workflow goes something like:
[INDENT]
Open laptop for meeting > close laptop and do some site stuff > open again for quick meeting > close for more site stuff ... etc ... etc[/INDENT]

The laptop does not have enough battery life to suspend for the hours it is closed. 

Thing is, I think I used hibernate successfully (once, though it may have been suspend) before I upgraded the ram, and it worked ok. Now the system just boots as normal (e.g does not "resume"). 

I've tried resizing my swap file to 8GB following this tutorial - [https://bogdancornianu.com/change-swap-size-in-ubuntu/](https://bogdancornianu.com/change-swap-size-in-ubuntu/) but that hasn't worked.

Any help would be appreciated.

---

### Post by Impavidus on 2019-01-31
It is plausible that you can't hibernate because your swap is too small. How much ram and swap are reported:```
free -m
```
I don't know if this is completely up-to-date ([https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)), but it says that to hibernate you still need a swap partition, not a swap file.

---

### Post by steve234 on 2019-01-31
Sorry I probably wasn't clear in my first post. I followed the linked tutorial to increase the size of my swap file, but to no effect:

```
$ free -m              total        used        free      shared  buff/cache   available
Mem:           7975         834        6391          45         749        6843
Swap:          8191           0        8191

```

 Perhaps I should re-partition to get a swap partition?

---

### Post by steve234 on 2019-01-31
I've also just tried to use uswsusp as described here - [https://medium.com/@lzcoder/enable-hibernate-on-ubuntu-using-uswsusp-s2disk-ae0b71862eb5](https://medium.com/@lzcoder/enable-hibernate-on-ubuntu-using-uswsusp-s2disk-ae0b71862eb5) - no change

---

### Post by #&amp;thj^% on 2019-01-31
I think that link left out a few steps, please show us this:
```
ls -lh /swapfile
```

---

### Post by steve234 on 2019-01-31
Cheers 1fallen  - is that a dogue de bordeaux in your profile pic! nice

```
$ ls -lh /swapfile-rw------- 1 root root 8.0G Jan 31 14:38 /swapfile

```

Looking at that output from a nOOb perspective, is the ownership wrong - presumably my user would want to write to it, unless hibernate is reserved for those with greater powers?

---

### Post by #&amp;thj^% on 2019-01-31
> **steve234 said:**
> Cheers 1fallen  - is that a dogue de bordeaux in your profile pic! nice


Yes. :) That's Jake he's quite a heathen at times. LOL! He really is a good family pet and member.(I'd be lost without him )
> **steve234 said:**
> 
```
$ ls -lh /swapfile-rw------- 1 root root 8.0G Jan 31 14:38 /swapfile

```

Looking at that output from a nOOb perspective, is the ownership wrong - presumably my user would want to write to it, unless hibernate is reserved for those with greater powers?
Nope just as it should be ROOT.
I should have asked for one more thing here>>this:
```
cat /etc/fstab
```

---

### Post by steve234 on 2019-01-31
Hehe, my brother has one, she is the same at times, but mostly a big softie...

```
 $ cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=00cd8ba7-d899-4f9a-8ece-6b90b03bd409 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0

```

---

### Post by #&amp;thj^% on 2019-01-31
well it seems we both have an oppertunity to learn here I just tried on my 18.04 with a swapfile, hibernating (to disk) will no longer work out of the box when using a swap file. This can be done but I can't test it because resuming from hibernation didn't work on my system.

But i was able to hibernate with:
```
resume=UUID=70e26944-69e8-4d18-8a7a-4da66ee8ca6c
```
I added that to "/etc/default/grub" from the output "cat /etc/fstab"
So it now looks like:
```
cat /etc/default/grub 
# GRUB boot loader configuration

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="Arch"
GRUB_CMDLINE_LINUX_DEFAULT="quiet 
resume=UUID=70e26944-69e8-4d18-8a7a-4da66ee8ca6c ipv6.disable=1 
nogpumanager"
GRUB_CMDLINE_LINUX=""

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable booting from LUKS encrypted devices
#GRUB_ENABLE_CRYPTODISK=y

# Uncomment to enable Hidden Menu, and optionally hide the timeout count
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

# Uncomment to disable graphical terminal
#GRUB_TERMINAL_OUTPUT=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=auto

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you want GRUB to pass to the Linux kernel the old parameter
# format "root=/dev/xxx" instead of "root=/dev/disk/by-uuid/xxx"
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true

# Uncomment and set to the desired menu colors.  Used by normal and wallpaper
# modes only.  Entries specified as foreground/background.
#GRUB_COLOR_NORMAL="light-blue/black"
#GRUB_COLOR_HIGHLIGHT="light-cyan/blue"

# Uncomment one of them for the gfx desired, a image background or a gfxtheme
#GRUB_BACKGROUND="/path/to/wallpaper"
#GRUB_THEME="/path/to/gfxtheme"

# Uncomment to get a beep at GRUB start
#GRUB_INIT_TUNE="480 440 1"

# Uncomment to make GRUB remember the last selection. This requires to
# set 'GRUB_DEFAULT=saved' above.
#GRUB_SAVEDEFAULT="true"


```
Also UEFI Secure Boot needs to be turned off for this to work.
I have to dash to work, but Ill check back if time permits today.
Good Luck

---

### Post by steve234 on 2019-01-31
So... I've gone back to the "stock" setup by reversing the stuff I did following the uswsusp tutorial. I have: 


- apt removed uswsusp; and
- gone on a steep learning curve about removing systemd override files to get rid of my changes to systemd-hibernate.service


I then made the changes you helpfully pointed to above and did grub-update. My etc/default/grub file is now: 


```
 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet resume=UUID=00cd8ba7-d899-4f9a-8ece-6b90b03bd409 ipv6.disable=1 nogpumanager"
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

Now when I

```
 $ systemctl hibernate 
```

It looks like it's going for a hibernation, gives some message about an IRQ vector and shuts down. On reboot it say some stuff about recovering a journal and then boots to lxdm. Once I log in, it's a fresh session, nothing is recovered from the hibernate.

---

### Post by #&amp;thj^% on 2019-02-01
Whoops I meant only the resume line (resume=UUID=00cd8ba7-d899-4f9a-8ece-6b90b03bd409) so it might prove beneficial to remove the 2 options I have=(ipv6.disable=1 nogpumanager)
Plainly put yours should read as follows:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet resume=UUID=00cuswsusp d8ba7-d899-4f9a-8ece-6b90b03bd409"
```
This is providing that the "UUID" is correct.
And with any changes to grub, you'll need to tell grub of the change with:
```
sudo update-grub
```
I probably wouldn't hold my breath for hibernation to work as hoped (Coming out of hibernation) with 18.04. :(
A friend just sent me a link, see if this helps: [https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file/](https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file/)
he also mentioned that he had to install uswsusp a few times.
Good Luck and I will check back later.>>>>(I owe, I owe, it's off to work I go.;) )

---

### Post by steve234 on 2019-02-01
Didn't get anywhere initially, but eventually nailed it - to resume from disk following hibernate in Lubuntu 18.04 you need to set the offset for the swap file in grub (and a bunch of other stuff):

That tutorial worked for me [https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file/](https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file/)

Cheers for your help 1fallen (and Jake)

---

### Post by #&amp;thj^% on 2019-02-01
> **steve234 said:**
> Didn't get anywhere initially, but eventually nailed it - to resume from disk following hibernate in Lubuntu 18.04 you need to set the offset for the swap file in grub (and a bunch of other stuff):

That tutorial worked for me [https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file/](https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file/)

Cheers for your help 1fallen (and Jake)

Good Job! :)
I should have tested it myself thoroughly but I trust him, and I have a SSD Drive and didn't want the extra wear and tear on my drive. 
It really isn't significant (Unless you hibernate 8 or more times a day) but I abuse the crap out of my drives as is.
Jake and I both Thank You for your kindness.
Best Regards

---

