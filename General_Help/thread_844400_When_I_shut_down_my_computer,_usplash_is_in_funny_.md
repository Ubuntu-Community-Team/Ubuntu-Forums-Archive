---
title: "When I shut down my computer, usplash is in funny colors"
date: 2008-06-29
forum: General Help
---

### Post by Redrazor39 on 2008-06-29
When I turn on my computer with Ubuntu, usplash shows the right colors; red, orange, black, yellow. When I shut it down, it's all swirly green and purple, like when you put a magnet to a TV. 

I used startup manager to change a few things, but I don't think I did anything that would screw this up.

Please help. I don't know what could have caused this or how to fix it.

---

### Post by jualin on 2008-06-29
That's because you have the Ubuntu Rainbow Shutdown Edition. Just kidding with you pal, I have never heard of such thing as your question, maybe you changed some configuration on your tweaking. I will look up a solution when I get home. Hang in there buddy!

---

### Post by jualin on 2008-06-29
[http://ubuntuforums.org/showthread.php?t=440971]("http://ubuntuforums.org/showthread.php?t=440971") Some one of that thread suggested reinstalling usplash-theme-ubuntu, maybe that will do the trick. Hope this helps

---

### Post by Redrazor39 on 2008-06-29
lol.

I'm experimenting with different settings on Startup-Manager. Maybe it's because I changed the resolution from 800x600 to 1024x768 (I have a 1280x800 monitor, but the splash doesn't even have a background, so I don't think that matters)

Gonna restart now. I hope it's fixed!

---

### Post by Redrazor39 on 2008-06-29
nope, nothing worked. 

Changing the resolution just uncentered it, then i had to reinstall usplash and usplash-theme-ubuntu and now I'm right back where I started.

Maybe it has something to do with this new kernel... I'm using 2.6.24-19, when the old one was -16. I set startupmanager to hide that kernel. Maybe I should stick to the old one...

---

### Post by Redrazor39 on 2008-06-29
nope, still didn't work :(

Tell me, is there a way to clean install ubuntu with the live CD without deleting the ubuntu partitions? I have an ext3 and swap partition for ubuntu as well as a partition for Vista and a recovery partition for Vista. Is there a way to put in the Live CD and choose which partitions I want?

Do I just click on install and click on "Manual" and choose the partitions? Does it work like that?

---

### Post by jualin on 2008-06-29
Do you have a different "home" partition? You can choose the partition that you want to install Ubuntu to, just like you said just choose "manual". But if you don't have a different "home" partition you will need to make one. Look up in the forums there was a guide somewhere that explained how to do that. 
You can keep your "home" partition untouched since the operating system only installs on the "/" partition.

---

### Post by Redrazor39 on 2008-06-29
I don't even have anything important in my home folder, so I don't care. 

The only problem with doing a clean install is that I have to spend over an hour downloading 205 updates.

---

### Post by jualin on 2008-06-30
If you don't mind spending time downloading the updates and if your internet doesn't have a time or data limit then I would say go for the clean install. Now someone else might have a better solutiion for this which doesn't involve reinstalling.

---

### Post by damis648 on 2008-06-30
I am having this exact same problem. Nobody has any solutions?

---

### Post by Redrazor39 on 2008-07-01
I can't believe it. I guess it must be a bad burn or something. I did install with a CD-RW, but I did that the first time I got ubuntu and it worked fine! CD-RWs work just fine the first time for me!

This is so annoying... I would hate to waste another CD. Maybe I should wait until the point release to burn another image. When does 8.04.1 come out again?

---

### Post by jualin on 2008-07-01
I think in comes out some time in July

---

### Post by damis648 on 2008-07-02
> **jualin said:**
> I think in comes out some time in July

You already have it if you have the pre-release repos enabled. Check your GRUB.
@OP: No need for that. I reinstalled twice and I constantly get this bug after a while. (Maybe update related?) Anyway, what Graphics do you have? Maybe someone should file a bug on launchpad?

---

### Post by damis648 on 2008-07-02
Found bug report: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/197937](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/197937)

EDIT: one more: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/43223](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/43223)

I will try removing the vga=775 from my GRUB and I will check if it fixes it or if I change it to 791. It appears this happens to people with high resolutions and the vga line.

---

### Post by damis648 on 2008-07-02
It worked! All I had to do was remove vga=775 from the kernel line, which startupmanager automatically adds. I suggest you do the same. [SOLVED]!:popcorn:

---

### Post by Redrazor39 on 2008-07-02
Ok, I'll try that as soon as I get on my ubunu laptop. Thanks! I knew there was a problem with the vga in some way because in openSUSE I messed with that to get the right resolution and totally killed my bootsplash.

This is great! I hope it works!

---

### Post by jualin on 2008-07-02
> **damis648 said:**
> Found bug report: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/197937](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/197937)

EDIT: one more: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/43223](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/43223)

I will try removing the vga=775 from my GRUB and I will check if it fixes it or if I change it to 791. It appears this happens to people with high resolutions and the vga line.

You should comment on launchpad about the solution, maybe more people can solve their problem thanks to your solution.

---

### Post by damis648 on 2008-07-02
> **jualin said:**
> You should comment on launchpad about the solution, maybe more people can solve their problem thanks to your solution.

The solution was on the launchpad bug report.

---

### Post by jualin on 2008-07-02
Then nevermind pal. Thank you for putting it on the forums. :lol:

---

### Post by Redrazor39 on 2008-07-03
mine says vga=771, but I'll delete that anyway. I hope it's safe.

---

### Post by Redrazor39 on 2008-07-03
hmmm

I removed vga=771 in the line that showed the title for Ubuntu 8.04. Maybe I removed the wrong one... There is one but it's a comment (a # before the line)

---

### Post by damis648 on 2008-07-03
> **Redrazor39 said:**
> hmmm

I removed vga=771 in the line that showed the title for Ubuntu 8.04. Maybe I removed the wrong one... There is one but it's a comment (a # before the line)

Hm... can you post your menu.lst?

---

### Post by Redrazor39 on 2008-07-03
Ok, I changed the vga to 791 (I just typed it back in) and when I shut it down, the bootsplash was perfect. When I started it up again, my starting bootsplash was not centered; it was up and to the left. It's so annoying because it looks really glitchy when it's like that.

Here's menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=076a12d3-3d55-4fcc-9df0-08362a3affc2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet vga=771

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=076a12d3-3d55-4fcc-9df0-08362a3affc2 ro splash quiet vga=791
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=076a12d3-3d55-4fcc-9df0-08362a3affc2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=076a12d3-3d55-4fcc-9df0-08362a3affc2 ro splash quiet vga=791
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=076a12d3-3d55-4fcc-9df0-08362a3affc2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Business (recovery mode)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista Business
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by damis648 on 2008-07-03
Sorry, I wish I could be of more help. It worked for me.

---

