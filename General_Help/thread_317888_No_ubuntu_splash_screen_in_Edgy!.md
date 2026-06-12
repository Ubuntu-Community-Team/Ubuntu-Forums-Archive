---
title: "No ubuntu splash screen in Edgy!"
date: 2006-12-13
forum: General Help
---

### Post by jamesoz91 on 2006-12-13
To anyone else with this problem:
1. At terminal, put in:
sudo gedit /boot/grub/menu.lst
and press enter/return.
2. Scroll down to the end of the file and look for a line that says:
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 etc. etc.
3. After the above line, there should be some variables. One should be vga=xxx where xxx is a number given from the below table.
If you are not getting a boot screen, and do not have a vga variable in that string, try putting in the variable, and try different numbers from the table. Usually you should not go higher than 8 bit colour.
4. Restart computer, and wait until it is booting up, instead of just looking at the shutting down. When this happened to me, the solution did not appear until the computer was actually rebooting.
5. If you would like a log of what's happening in the booting process, then remove the variable "quiet" in the above line.

Thanks to buck for his help.

```
                      640x480  800x600 1024x768 1280x1024 1600x1200
-----------------+---+--------+----------+-----*----+----------+---------
256 (8 bit)       |  769        771        773          775          796
32,768 (15 bit) |  784        787        790          793          797
65,536 (16 bit) |  785        788        791          794          798
16.8M (24 bit)  |  786        789        792          795          799
```

--------------------------------------------------------------------
Hi. I just installed Edgy on my external hard drive on my Dell Dimension 2400. And there is one thing that really annoys me. Although the system loads fine and as yet I havent encountered any major life threatening bugs, there's no splash screen when its booting up. I e that ubuntu logo, with the list of things to do, and the OK or FAIL next to them.
While I realise that compared to other people's problems, this is just a trivial thing, but it is really annoying.:mad:  And when I shut down I have the same problem and have to guess the time when I am supposed to press Enter to shut it off.
Does anyone know why this is caused? Is there any workaround?

---

### Post by strabes on 2006-12-13
paste the output of this commmand in Applications -> Accessories -> Terminal:

```
cat /boot/grub/menu.lst
```

---

### Post by jamesoz91 on 2006-12-31
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=50bf27ad-b7a8-4146-897c-e63dcd8d25ec ro
# kopt_2_6=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


Sorry that I took so long. I was on holiday.

---

### Post by maheshjagadeesan on 2007-01-05
Have you got a solution to this problem? I'm facing it too, and am now trying to get the splash screen back.

---

### Post by Buck2348 on 2007-01-06
I've just been through this problem and with quite a bit of time solved it with help from several threads here (search on "usplash").  I would suggest you install sum (Startup Manager) and see what screen resolution it defaults to.  Set it to no higher than 800x600 and 8 bits color depth.  Make sure the resolution in /etc/usplash/conf agrees with that and that the "kernel" line for the kernel you boot to in /boot/grub/menu.lst has an entry near the end of the line like "vga=771".  Here is the full line from my menu.lst:
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 vga=771 ro splash
I think sum should set both of these but it or some command I entered garbled that line in my menu.lst and I had to edit it manually.  It was after doing that that I got my usplash back.

Here is the full table for those vga codes--but as I said, sum ought to set it to agree with the resolution you have set there.
```
                      640x480  800x600 1024x768 1280x1024 1600x1200
-----------------+---+--------+----------+-----*----+----------+---------
256 (8 bit)       |  769        771        773          775          796
32,768 (15 bit) |  784        787        790          793          797
65,536 (16 bit) |  785        788        791          794          798
16.8M (24 bit)  |  786        789        792          795          799
```

Hope this helps.

Buck

---

### Post by jamesoz91 on 2007-01-06
Thanks for your help so far.
I have got my USPLASH back using this StartUp-Manager, and I've set it to 640x480 at 8 bit.
But it has some issues.
For one thing, the main UBUNTU sign is off centre, and then the orange loading bar underneath that is slightly to the right of the centre. And I havent even got a log thing of what is going on in the boot itself.
I think I might have to configure some stuff.. I do remember seeing some log in another resolution, but I've always had the off-centre problem.
Any ideas with this?

---

### Post by jamesoz91 on 2007-01-06
I've fixed the problem. Turned out I needed to have it at 1024x768 resolution and at 8 bit colour for it to give me a screen.
I have altered the post at the beginning of this thread to hopefully help anyone who also has this problem.
Thanks buck!

---

### Post by dingley_del on 2007-07-31
Thanks for the info......this has sorted out my problem of my Samsung SyncMaster displaying unsupported mode where the Ubuntu progress boot up splash screen should have been.  I used vga=771.  I also now have boot down screen....bonus!

thanks again
Dingley_del

---

