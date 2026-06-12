---
title: "automatically deb-postinstall proceeding possible?"
date: 2008-06-18
forum: General Help
---

### Post by bs0d on 2008-06-18
Hi

I have customized system and after every upgrade of many packages like wine, kernel I need to alter some settings.

Is it possible to set trigger for install some deb packages to make these changes after every upgrade of package?

Example: after install of new kernel I need to remove "quiet splash"  from kernel options in /boot/grub/menu.lst

there are several such changes, how to tell dpkg/apt to proceed my post-instll script?

thanks

---

### Post by ibuclaw on 2008-06-18
Not sure if there is, but you can make a script that checks the files you alter and corrects them if some specific lines are different, then puts them back the way you want it.

ie:
To check  for, then remove all instances of "quiet splash" from the menu.lst file would be the command
```
sed -i '/quiet splash/s/quiet splash//g' /boot/grub/menu.lst
```

Although, to have such a script to be ran after every upgrade I don't think is possible, so you'll have to run it yourself manually.

Regards
Iain

---

### Post by ibuclaw on 2008-06-18
I've been corrected. (thanks Vor :D)

Yes, you can have a script run automatically after installing/upgrading packages.

Read this thread here about [Prelinking]("http://ubuntuforums.org/showthread.php?t=74197").

Regards
Iain

---

### Post by bs0d on 2008-06-18
thanks!

DPkg::Post-Invoke {

do the trick

---

### Post by geirha on 2008-06-18
> **bs0d said:**
> 
Example: after install of new kernel I need to remove "quiet splash"  from kernel options in /boot/grub/menu.lst


A note on this particular case. When the kernel is updated, a post-installation script will run a script called "update-grub", which will recreate the kernel-list, and reset all options to what the commented options at the start of the AUTOMAGIC KERNELS LIST is:
```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

```

Further down, you'll find this line:
```
# defoptions=quiet splash
```
change it to read
```
# defoptions=
```

Then run ```
sudo update-grub
``` and you'll see that the kernels no longer use those options (and they won't at next kernel update either), so there you have a permanent fix for that particular problem. No need for a triggered script.

---

