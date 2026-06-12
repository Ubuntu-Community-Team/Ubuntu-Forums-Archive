---
title: "boot problem (error 17)"
date: 2007-04-21
forum: General Help
---

### Post by dedmonds on 2007-04-21
I noticed yesterday that I could not boot into Windows using Grub on my laptop. An error message was shown (Error 17: Cannot mount selected partition) when I selected the option to boot into Windows. (Unfortunately, I have no idea when this became a problem because I don't use Windows often.) I did notice that there was an older copy of the /boot/grub/menu.lst file in the directory named menu.lst~ and the diff showed that the only difference between the backup and the one being used was the following line at the end of the file.

kernel /boot/vmlinuz-2.6.17-10-386 root=/dev/hda2 ro quiet splash acpi=off

I tried commenting out the line and was able to successfully boot into Windows. I haven't notice any problems running Ubuntu either. However, I am a bit concerned that this man not be wise, since I do not understand what the line I removed does.

Can any of you tell me whether it makes sense to use the laptop as I have it now (with the line commented out in the menu.lst file)? If it makes more sense to make some other change to correct the original Windows boot problem, please point me in the right direction. Thanks.

---

### Post by acormack on 2007-04-21
As far as I am aware the lines in menu.lst are in blocks and you don't normally have just one line on its own.

Was the line you commented in the same section as your windows boot option?  

Below is the section of my menu.lst file that specifies the windows boot.  There certainly isn't a kernel line.

[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1
[/B]

Overall,  if it works with the line commented out I would leave it as it is and not worry!


Alec

---

### Post by dedmonds on 2007-04-21
Yes, the line I commented out is either in the same section as the Windows boot option or just after. The end of the modified menu.lst file is included below:


[B][INDENT]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1

# kernel /boot/vmlinuz-2.6.17-10-386 root=/dev/hda2 ro quiet splash acpi=off[/INDENT][/B]


Until this morning, I had never manually edited the menu.lst file, which is why I'm a bit concerned since I don't really know what I'm doing.

---

### Post by acormack on 2007-04-21
Somehow or other an update to that file didn't work as it should.

However the error happened that line ahouldn't be there so commenting or deleting it won't do any harm

---

