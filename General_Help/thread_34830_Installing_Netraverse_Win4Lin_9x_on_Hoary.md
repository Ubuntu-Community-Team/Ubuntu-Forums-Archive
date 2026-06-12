---
title: "Installing Netraverse Win4Lin 9x on Hoary"
date: 2005-05-16
forum: General Help
---

### Post by jpmcc on 2005-05-16
[Win4Lin 9x](http://www.win4lin.com/index.php?option=com_content&task=view&id=61&Itemid=98)  is a commercial product from [Netraverse Inc](http://www.netraverse.com) which lets you run Microsoft Windows 9x as an application under Linux.  Ubuntu is not officially supported by Win4Lin, but Win4Lin can be installed under Ubuntu without too much difficulty.

Pre-requisite: the *win4lin-install* program uses an old version of *libgtk*, which you need to install by doing:
```

sudo apt-get install libgtk1.2

```
You can then run *win4lin-install* until it stops with: *Unfortunately, your system is running a kernel directly supported by Win4Lin*. The easiest solution is to replace the Ubuntu kernel with a Netraverse one. This isn't as drastic as it sounds. It's easy to switch kernels between Ubuntu's and Win4Lin's, so you won't "break anything"  :) 

Download the appropriate [Netraverse Generic Binary Kernel](http://www.netraverse.com/member/downloads/kernel_generic.php#26) - I used *Kernel-Win4Lin3-NeTraverse1.0_2.6.8.1-03 .i586.rpm*

Install the downloaded file using:
```

sudo alien --install Kernel-Win4Lin3-NeTraverse1.0_2.6.8.1-03 .i586.rpm

```
You now need to add this kernel as an option at boot time. Add the following lines to the end of */boot/grub/menu.lst*
```

title Win4Lin
root (hd0,0)
kernel /boot/win4lin root=/dev/hda2 ro quiet splash pci=noacpi ide=reverse

```
*Note:*  check the other entries for the correct *root* - you may have root *(hd0,1)* or some other variant; and
make sure that the menu is **not** hidden by commenting out the *hiddenmenu* option:
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```
You should now reboot your PC. When it boots, select the Win4Lin kernel, and you should be able to complete the Win4Lin installation successfully. 

I suggest using the Win4Lin kernel by default - Win4Lin will not run if you select an Ubuntu kernel. However, if you do run into problems, just select the Ubuntu kernel at next boot.

It is possible build your own Ubuntu kernel with the Win4Lin patches. However, if you do this, you end up with something neither Netraverse nor Ubuntu will support officially.

Good luck :)

---

