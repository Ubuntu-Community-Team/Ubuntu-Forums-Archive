---
title: "A quick queston regarding grub"
date: 2007-03-04
forum: General Help
---

### Post by abierstedt on 2007-03-04
hello i finally got ubuntu installed with my x800 card which was a pain, and now i have another issue i need to get worked out


i have a dual boot set up and i have installed ubuntu on a separate hard drive than windows vista( which was already installed).  I boot into ubuntu no problem now but vista isnt loading correctly


here is the end of my grub file could someone tell me what is wrong??

(on install it automatically detected the name vista longhorn but they dont work, they just ask for the disk to fix the mbr)


right under the end default options is the part  where i tried to put the windows loader

## ## End Default Options ##
title           Windows Vista
root            (hd2,0)
makeactive
chainloader	+1


title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1




thanks for the help im sure its something easy but im not familiar with the hd1,2,0 titles

ill post more info if needed

---

### Post by abierstedt on 2007-03-04
bump im really stuck here


i can not get into vista and i have no acess to the internet via ubuntu right now because of wireless

i have been reading howto ater howto and same problem 

i really need to resolve this please anyone help!!

---

### Post by JohnPhys on 2007-03-04
So which of the two vista grub entries are you booting?

---

### Post by abierstedt on 2007-03-04
ubuntu added 3 at the bottom


i dont know why and i just followed this howto


[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)



the one at the top is the the only thing i added and it doesnt work

what should i do??



thisone that is



## ## End Default Options ##
title Windows Vista
root (hd2,0)
makeactive
chainloader +1



i know that is wrong because i am not sure which hd is which


i have 1      40 gb ata drive with the windows installed

1 250 that has the partition which ubuntu is installed on

---

### Post by abierstedt on 2007-03-05
is it safe to asume the hd1  which is my 1st ide harddrive   is supposed to be hd0 in the grub menu?  because i read that the 1st hard drive is 0 and the first parition is 0 also

so that confuses me, i am losing it here


and from this guys post it looks like i might by screwed


is that true???


[http://forum.myspace.com/index.cfm?fuseaction=messageboard.viewThread&entryID=2263315&adTopicID=6&categoryID=35&IsSticky=0&Mytoken=9587FB01-FE69-432F-A2A58D2651F3F6B9553109](http://forum.myspace.com/index.cfm?fuseaction=messageboard.viewThread&entryID=2263315&adTopicID=6&categoryID=35&IsSticky=0&Mytoken=9587FB01-FE69-432F-A2A58D2651F3F6B9553109)

---

