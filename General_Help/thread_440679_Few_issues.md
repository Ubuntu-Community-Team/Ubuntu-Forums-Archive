---
title: "Few issues"
date: 2007-05-11
forum: General Help
---

### Post by Yoguess on 2007-05-11
Hi
My wireless don't work so I have posted it in the wireless section

In terminal I can't use "CTRL + copy, past stuff"
On webpages i can't use page down or up or the up and down keys on so and not on the others

Also when I use backspace to go to last page, all it does is takes me to the top of the page and not back, How to fix this?

also at the (Dual) boot i get option for more then one linux option and windows
top 4 are linux with 2 being safe modes and other 2 different kernels
How do I remove the others?

Then there is other stuff that Ubuntu won't let me uninstall, like softphone or image scanner and more. How do I remove this?

I posted this last request on a different forum but I can't remember where so Im asking on Ubuntu:
How do I remove unneeded stuff? files,  programs, junk
kinda like windows disk clean up

Also earlier i used to see"IBM" option in add/remove but now that I have an IBM I dont see the IBM option in add/remove
thanks for your help

---

### Post by juxtaposed on 2007-05-11
> In terminal I can't use "CTRL + copy, past stuff"

I think you have to right click and do copy or paste in gnome-terminal, I don't think xterm works with that at all (from my experience).

> How do I remove unneeded stuff? files, programs, junk

"sudo apt-get autoremove" is something that gets rid of some unneeded things, not i'm not an expert on ubuntu, so... :P

---

### Post by divague on 2007-05-11
> In terminal I can't use "CTRL + copy, past stuff"

You have to press CTRL+SHIFT+c to copy thing from the terminal

---

### Post by Yoguess on 2007-05-11
yes you are right about right click to copy and paste in terminal, thats what I am using now

thanks for the autoremove, that just cleared up about 50 megs

---

### Post by skwishybug on 2007-05-11
> **Yoguess said:**
> 
My wireless don't work so I have posted it in the wireless section

What type of wireless card do you have?

> **Yoguess said:**
> 
On webpages i can't use page down or up or the up and down keys on so and not on the others

Also when I use backspace to go to last page, all it does is takes me to the top of the page and not back, How to fix this? 

Which browser are you using, and which version?

> **Yoguess said:**
>  also at the (Dual) boot i get option for more then one linux option and windows
top 4 are linux with 2 being safe modes and other 2 different kernels
How do I remove the others?


```
 gksu gedit /boot/grub/menu.lst
```Will let you remove the entries from the list.

---

### Post by Yoguess on 2007-05-11
> **skwishybug said:**
> What type of wireless card do you have?
IBM thinkpad  a/b/g/n

here's my post on wireless issue
[http://ubuntuforums.org/showthread.php?t=440666](http://ubuntuforums.org/showthread.php?t=440666)


> Which browser are you using, and which version?
Firefox 2.0.0.3



```
 gksu gedit /boot/grub/menu.lst
```> Will let you remove the entries from the list.

below is the result I get at startup
i see what you mean by removing the entries, but what about 2.6.17.10? are there 2 kernels? if so how to remove it from the OS or is it not possible?

Thanks for the help


```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by strabes on 2007-05-12
To change the backspace behaviour in google, go to "about:config" and find the preference name "browser.backspace_action" and change it to 0.

To remove old kernels (and have them removed automatically from your /boot/grub/menu.lst) simply remove the packages with aptitude or apt-get. They're called linux-image-2.6.xx-xx-generic. Just remove the old versions. If you wanted to remove 2.6.20.14, you would run this: ```
sudo aptitude remove linux-image-2.6.20-14-generic
```

Just make sure you don't remove the one you're using right now. To find out which kernel you're using right now, run this: ```
uname -r
```

Here's a page that will tell you how to clean up unnecessary files: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Yoguess on 2007-05-12
Thanks for the help

now only thing left is wireless

Looks like if I removed WPA then it should connect to my router but using WPA it is not working

---

