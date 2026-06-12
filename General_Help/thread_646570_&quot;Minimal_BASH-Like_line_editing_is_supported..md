---
title: "&quot;Minimal BASH-Like line editing is supported...&quot; message on start up"
date: 2007-12-21
forum: General Help
---

### Post by StephX on 2007-12-21
My Ubuntu 7.04 was working fine last night (and for several weeks), but this morning I'm getting this message while trying to boot:

"[ Minimal BASH-Like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename. ]"

and Ubuntu wont load. Ubuntu is my only OS on that computer and my linux skills are quite rudimentary so I have no idea what to do.

I appreciate any suggestions,
Alex

PS I'm still using 7.04 because when I tried upgrading to 7.10 my screen was an unreadable, blurry mess.

---

### Post by tehet on 2007-12-21
You could try this:
[http://gentoo-wiki.com/HOWTO_Fix_Grub_it_can't_find_a_kernel](http://gentoo-wiki.com/HOWTO_Fix_Grub_it_can't_find_a_kernel)

---

### Post by StephX on 2007-12-21
> **tehet said:**
> You could try this:
[http://gentoo-wiki.com/HOWTO_Fix_Grub_it_can't_find_a_kernel](http://gentoo-wiki.com/HOWTO_Fix_Grub_it_can't_find_a_kernel)

thanks for the link, but the suggestions on that page aren't solving my problem. i entered in the commands as the link directed (though i have know idea what, exactly, they were for) but i wasn't getting the same output as the link, and i'm still having the same issue.

thanks for the suggestion though.

---

### Post by StephX on 2007-12-21
> **tehet said:**
> You could try this:
[http://gentoo-wiki.com/HOWTO_Fix_Grub_it_can't_find_a_kernel](http://gentoo-wiki.com/HOWTO_Fix_Grub_it_can't_find_a_kernel)

after googling a bit i changed the input to:

root (hd0,0)/boot
setup (hd0,0)

and finally got something to happen:

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.

Ubuntu still will not load normally though.

Any ideas folks? I'm totally at a loss here.

thanks,
Alex

---

### Post by StephX on 2007-12-21
well, i guess i'm just going to reinstall ubuntu since i can't figure out what's going on.

can anyone at least give me an idea as to why this may have happened, so that i can avoid this occurring in the future?

thanks,
alex

---

### Post by pyronaut on 2007-12-21
well ...couple of things first ... Do u even get the GRUB  menu when you boot up or no??.. if you do then you might be able to boot into the recovery mode and look at syslog or dmesg | tail... another thing might be to use the live cd and reinstall grub .. since you are online I would try to burn a live CD before reinstalling since that can always be pain and you can always reinstall grub if thats been messed up

---

### Post by StephX on 2007-12-21
> **pyronaut said:**
> well ...couple of things first ... Do u even get the GRUB  menu when you boot up or no??.. if you do then you might be able to boot into the recovery mode and look at syslog or dmesg | tail... another thing might be to use the live cd and reinstall grub .. since you are online I would try to burn a live CD before reinstalling since that can always be pain and you can always reinstall grub if thats been messed up

thanks for the reply - i appreciate it.

isn't what i'm describing in my first post the grub menu, or am i misunderstanding something?

i'll google the recovery mode/syslog/dmesg you suggested and try to figure that out.

i'm actually using a different computer because my ubuntu computer is pretty much useless, but i do have the live cd i originally installed ubuntu with and i have used it to boot the computer in question since this began - i copied as many of my docs as i could (some of them have little 'x's next to their filenames and i can't seem to copy them).

i'm not sure if it's the grub that's the problem. the computer seems to be halting in grub and not loading ubuntu.

what really gets me is that the computer was working fine last night and i've done nothing to my computer between then and this morning (there was one update i downloaded and installed yesterday though...).

---

### Post by pyronaut on 2007-12-22
well if you see the boot up screen with the list of kernels etc then that would mean the GRUB menu is up and so then you choose the recovery --mode from there... let me knowif you dont see that screen .. alos might help if you know which package you updated... it shouldnt be a  issue unless of course its a drive failure or something

---

### Post by StephX on 2007-12-22
i don't notice any list of kernels (i've only got ubuntu on this machine). when booting it just goes from "loading grub..." to the "[ Minimal..." message i quoted in my first post and it gives me a:

grub>

i don't know how to enter in recovery mode from here (and googles not helping just yet)

---

### Post by pyronaut on 2007-12-22
ok first ... if you have a live cd.... use that to get into /boot/grub and theres a file called menu.lst .. can you post a copy of it here.. or take a look at it.. If you updated your kernel last night then it might have written a newline to this file making that the default kernel.... look at the line with the highest kernel version and compare that to the earlier ones and see if there are any changes

---

### Post by pyronaut on 2007-12-22
Also this might help you understand the grub command line better [http://www.linuxjournal.com/node/4622/print](http://www.linuxjournal.com/node/4622/print)

---

### Post by pyronaut on 2007-12-22
specifically try this 
grub> configfile (fd0)/boot/grub/menu.lst 

replace fd0 with you hard drive name... if you are not sure you can look it up once you boot the live CD..

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> ok first ... if you have a live cd.... use that to get into /boot/grub and theres a file called menu.lst .. can you post a copy of it here.. or take a look at it.. If you updated your kernel last night then it might have written a newline to this file making that the default kernel.... look at the line with the highest kernel version and compare that to the earlier ones and see if there are any changes

not really sure what i'm looking at here...

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> Also this might help you understand the grub command line better [http://www.linuxjournal.com/node/4622/print](http://www.linuxjournal.com/node/4622/print)

thanks for the link. i've been reading about grub quite a bit tonight, but i hadn't found that link yet (and it looks pretty comprehensive and comprehensible)

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> specifically try this 
grub> configfile (fd0)/boot/grub/menu.lst 

replace fd0 with you hard drive name... if you are not sure you can look it up once you boot the live CD..

i just tried this using "(hd0)" and it said something like ~cannot find partition...

so i tried (hd0,0) and it hung for about 20 sec than reset to a new "grub>" clearing everything else from the screen.

i'll try "reboot" now...

back to grub>

---

### Post by pyronaut on 2007-12-22
well try this for starters ... hit esc once you are past the bios-setup page.. shoud bring up the grub menu :)... if that doesnt work can you edit the grub menu?? .. if you can then change 3 things .. find the following lines and edit them (italics original in file bold my recommendations)
1) first the default kernel
 2) The timeout  before the automatic choice is loaded
3) making the grub menu visible :)
lines below from the menu.lst file


*default 0*

**default 2**


## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
*timeout 3*

**timeout 10**
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)

*hiddenmenu*

**#hiddenmenu**

---

### Post by pyronaut on 2007-12-22
now that should bring up the grub menu for you to look at and choose the 2.6.15 kernel to see if it boots up. If it does then there is something wrong with the kernel update

---

### Post by StephX on 2007-12-22
hitting ESC is just getting me to a Boot Menu (ie, floppy, cdrom, hdd0....etc).

as far as editing the grub menu...do i do that from the live cd? should i edit the menu.lst file?

---

### Post by pyronaut on 2007-12-22
yes the edits that i mentioned are for your menu.lst file from the /boot/grub/ folder

if that doesnt work then we'll go ahead an boot from the grub menu :)

---

### Post by StephX on 2007-12-22
i'm getting a message saying i don't have permission to save the file after i make the changes... :(

---

### Post by pyronaut on 2007-12-22
the way  you would make changes is by opening a terminal and typing  sudo gedit and once gedit opens go to the folder and open the file and then edit it :)

---

### Post by StephX on 2007-12-22
when i open the Boot folder through gedit it doesn't show the Grub folder...? it shows the other misc files, but not the Grub folder.

---

### Post by pyronaut on 2007-12-22
you are opening the boot folder on your Live CD :)
do this type sudo mount -a in your terminal and see if it mounts you hard drive on the desktop .... then you can go to the boot folder on your hard drive

---

### Post by pyronaut on 2007-12-22
ok ...lets get you booted in first try this when  you to the boot prompt
grub> root (hd0,0)
grub > kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash

the above are lines i copied from your menu.lst so it should work :).. basically those are the exact same commands that grub runs when booting up

---

### Post by StephX on 2007-12-22
i've actually already got my hard drive (shows as "disk") sitting on my desktop. i just tried sudo mount -a, but nothing new seemed to happen.

i'm trying to figure out how to fish around in my harddrive via gedit right now...

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> ok ...lets get you booted in first try this when  you to the boot prompt
grub> root (hd0,0)
grub > kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash

the above are lines i copied from your menu.lst so it should work :).. basically those are the exact same commands that grub runs when booting up

ok, i'll try this

---

### Post by pyronaut on 2007-12-22
well if your hard drive shows up on ur desktop then right click on it and it should show where its mounted for eg. /media/disk   then just use gedit to go o that foldet and then go to boot ...grub.. menu.lst

---

### Post by pyronaut on 2007-12-22
oops after right click select properties

---

### Post by StephX on 2007-12-22
tried it twice (that's a lot of googlygoop to type in) and got "Error 27 : Unrecognized command" both times

i'm referring to booting from grub> here

---

### Post by pyronaut on 2007-12-22
ok lets try this again
grub >root (hd0,0)
grub >kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash
grub>initrd /boot/initrd.img-2.6.20-15-generic
grub > boot

see if this works.. sorry for the gobbledy gook

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> well if your hard drive shows up on ur desktop then right click on it and it should show where its mounted for eg. /media/disk   then just use gedit to go o that foldet and then go to boot ...grub.. menu.lst

ahh, ic. 

i made the changes to the file as per your directions and have rebooted

---

### Post by pyronaut on 2007-12-22
did it work??

---

### Post by StephX on 2007-12-22
is that a space after kernel? maybe that's the problem...

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> did it work??

not that i can tell. still booting to "grub>"

---

### Post by pyronaut on 2007-12-22
well did u edit your menu.lst file?? yes it should be a space after kernel

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> ok lets try this again
grub >root (hd0,0)
grub >kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash
grub>initrd /boot/initrd.img-2.6.20-15-generic
grub > boot

see if this works.. sorry for the gobbledy gook

that was a space - my bad!

now it's booting :)

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> well did u edit your menu.lst file?? yes it should be a space after kernel

i did, but when i rebooted nothing new happened.

but i'm back into ubuntu thanks to all that gobleygook you suggested!

---

### Post by StephX on 2007-12-22
sweet

you're awesome!

I really appreciate you taking the time to help me out.

any chance you can tell me what just heppened?

did we load an ealier kernel?

---

### Post by pyronaut on 2007-12-22
yes we did ... if you go backa now and sudo gedit your menu.lst you cna check if you have the changes made.. My advice would be that your new kernel is not installed properly or something so you should go ahead and remove it all together the version is 2.6.20-16-generic
   i dont know what the issue is since that kernel works great for me :).. if you want to experiment with it then keep it, but remember to make the changes i told you in the menu.lst file... they are simple youn change the default kernel... the timeout of the menu so that it stays on long enough for you to choose and then the hidden part making it visible......:)
   good luck ... keep the commands written down if you decide to play around with keeoing the new kernel :).... thats why I love linux cos you can fix it urself and not have to shell out big bucks for something this siimple :)

---

### Post by StephX on 2007-12-22
is it safe to turn off my computer now? i suppose i can just redo what you just had me do if this happens again.

now i'm afraid to install the updates...

---

### Post by pyronaut on 2007-12-22
oops excuse my typos :)

---

### Post by pyronaut on 2007-12-22
can you post your menu.lst again so i can take a look

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> yes we did ... if you go backa now and sudo gedit your menu.lst you cna check if you have the changes made.. My advice would be that your new kernel is not installed properly or something so you should go ahead and remove it all together the version is 2.6.20-16-generic
   i dont know what the issue is since that kernel works great for me :).. if you want to experiment with it then keep it, but remember to make the changes i told you in the menu.lst file... they are simple youn change the default kernel... the timeout of the menu so that it stays on long enough for you to choose and then the hidden part making it visible......:)
   good luck ... keep the commands written down if you decide to play around with keeoing the new kernel :).... thats why I love linux cos you can fix it urself and not have to shell out big bucks for something this siimple :)

yeah, the changes are still there in the menu.lst file.

thanks again, i really appreciate all your help.

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> can you post your menu.lst again so i can take a look

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
default		2

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by pyronaut on 2007-12-22
you are welcome.. in case you get the grub menu again you know what to do .. good night :)

---

### Post by pyronaut on 2007-12-22
looks good... try rebooting it

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> looks good... try rebooting it


back to grub>  :(

but i can just reload the old kernel again...

maybe updating: my update window showed some new kernel looking stuff

---

### Post by StephX on 2007-12-22
man, i wish there were a way to cut and paste all that junk...

---

### Post by pyronaut on 2007-12-22
ok try that i would also remove the kernel with the version i mentioned earlier :).. the newest one in grub

---

### Post by pyronaut on 2007-12-22
sorry .... but that the drive id.... u dont need to turn off ur computer you know this is linux :)

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> ok try that i would also remove the kernel with the version i mentioned earlier :).. the newest one in grub

i'm quite linux ignorant (just been a user for several months now)...don't know how to remove a kernel

---

### Post by StephX on 2007-12-22
ug

after updating and rebooting i'm back to grub>

looks like i'll have to delete that kernel

---

### Post by pyronaut on 2007-12-22
ok if you know how to use synaptic you should find something like kernel-2.6... etc and you can click on uninstalling it. If you google the unoffiical ubuntu users guide fiesty.. there will be a lot of very good info for noobs on there basic stuff.

---

### Post by StephX on 2007-12-22
> **pyronaut said:**
> ok if you know how to use synaptic you should find something like kernel-2.6... etc and you can click on uninstalling it. If you google the unoffiical ubuntu users guide fiesty.. there will be a lot of very good info for noobs on there basic stuff.

sounds easy enough (i know how to use synaptic). i think you've already got me through the tough part. 

i've been dead tired for the last hour or so now, so i'm off to bed (and i'm sure you've had enough of this as well).

once again, i really appreciate your help. i'm sending some good karma your way.

good night
al

---

### Post by pyronaut on 2007-12-22
good nigth and merry Xmas.... 3am here by the way :)

---

### Post by StephX on 2007-12-22
haha only 12am here, and i'm beat!

have a good holiday

---

### Post by StephX on 2007-12-22
well...i've removed the other kernel (2.6.20-16) through synaptic and it no longer show in the grub menu, but it's still not autoloading. i still have to manually type in all that junk when booting halts on "grub>"

i even tried reinstalling grub through synaptic - but to no avail.

pyronaut got me back in and i've copied all my importants docs and such, so i can just do a full reinstall if necessary...

but i'm just wandering if anyone has any other ideas as to how to solve this problem?

thanks,
alex

---

### Post by StephX on 2007-12-22
i just ran "update-grub" ...so lets see if that helps...?

---

### Post by cksubs on 2007-12-22
This exact same thing happened to me this morning... I'm triple booting OSX, XP, and Gutsy on my MBP and this GRUB thing took out both my XP and Ubuntu boots. Does that indicate a larger problem or will the same fixes here work? It's strange, I installed ubuntu, it was working fine for about a day, and then without changing anything this starts happening.

Also, I'll probably end up reading through this whole thread but if it was one specific thing that helped you fix it do you think you could post/wiki the solution? It would probably save a lot of time and frustration for linux newbies like myself. Thanks.

---

### Post by meierfra on 2007-12-23
StephX:

The correct code to reinstall Grub is:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

---

### Post by meierfra on 2007-12-23
cksubs:  Start your own thread (include Grub in the title, then I will see it) and post the output of

```
sudo fdisk -lu
```
(Type this in a terminal in the LIveCD)

---

### Post by StephX on 2007-12-23
> **cksubs said:**
> This exact same thing happened to me this morning... I'm triple booting OSX, XP, and Gutsy on my MBP and this GRUB thing took out both my XP and Ubuntu boots. Does that indicate a larger problem or will the same fixes here work? It's strange, I installed ubuntu, it was working fine for about a day, and then without changing anything this starts happening.

Also, I'll probably end up reading through this whole thread but if it was one specific thing that helped you fix it do you think you could post/wiki the solution? It would probably save a lot of time and frustration for linux newbies like myself. Thanks.

my ubuntu was working fine for months...i'd tell you how to fix it if i could, but mine still isn't working properly. i have no idea what this indicates, but i'm hoping someone does and lets us  know.

if you just need to get back into ubuntu, i may be able to help you manually get in (as pyro helped me), but i'm still not 'fixed'.

---

### Post by StephX on 2007-12-23
> **meierfra said:**
> StephX:

The correct code to reinstall Grub is:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

so this is better than using synaptic to reinstall? i'll give it a try.

---

### Post by StephX on 2007-12-23
well that didn't work either

any other ideas?

this is my last cry for help before i just reinstall....

---

### Post by meierfra on 2007-12-23
Did you get any error messages  while reinstalling grub? Try again, copy the content of the terminal (before you type quit) and post it here.

Also post the output of

```
sudo fdisk -l
```

and your current "menu.lst"

---

### Post by StephX on 2007-12-23
sudo grub is no longer working for me

probably because i installed grub2 from synaptic a few minutes ago as a last ditch effort before i reinstall linux (it didn't make any difference)

---

### Post by StephX on 2007-12-23
> **meierfra said:**
> Did you get any error messages  while reinstalling grub? Try again, copy the content of the terminal (before you type quit) and post it here.

Also post the output of

```
sudo fdisk -l
```

and your current "menu.lst"

z@buzzer:~$ sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

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
default		2

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ea1c448-f339-4dfb-9141-0ecb86f053f5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by meierfra on 2007-12-23
I don't  know anything about Grub2. Also Grub2 is still very experimental. So please reinstall Grub.

> sudo fdisk

The command is 

```
sudo fdisk -l
```
("l" is a lower case L, not the number one)

---

### Post by StephX on 2007-12-23
ooops, don't know how i missed that "l" alltogether...i'll do it correctly this time.

---

### Post by StephX on 2007-12-23
z@buzzer:~$ sudo fdisk -l
Password:

Disk /dev/hda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3577    28732221   83  Linux
/dev/hda2            3578        3736     1277167+   5  Extended
/dev/hda5            3578        3736     1277136   82  Linux swap / Solaris

---

### Post by StephX on 2007-12-23
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
      root (hd0,0)

grub>
      setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub>

---

### Post by meierfra on 2007-12-23
I don't see anything wrong. Try the "sudo grub" thing again and report any error messages. 
(Edit: Didn't  see your last post,  nothing wrong where either)

Does the Grub Menu appear at boot-up? The grub menu should look like this:

Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+

---

### Post by StephX on 2007-12-23
> **meierfra said:**
> I don't see anything wrong. Try the "sudo grub" thing again and report any error messages. 
(Edit: Didn't  see your last post)

Does the Grub Menu appear at boot-up? The grub menu should look like this:

Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+

try sudo grub again? but i just did that about 10 minutes ago and pasted the results above...why would it have changed since then?

i've never noticed the above grub menu during boot up.

---

### Post by meierfra on 2007-12-23
I didn't see your last post before my last one. No reason to try the "sudo grub thing" again.

---

### Post by StephX on 2007-12-23
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>


oooops too late

---

### Post by meierfra on 2007-12-23
Just let me know whether the grub menu appears at boot up.

---

### Post by StephX on 2007-12-23
> **meierfra said:**
> Just let me know whether the grub menu appears at boot up.

nope, it just says "loading grub 1.5" (or something like that, it goes kinda quick) and then it hangs at

grub>

and i've got to load the kernel and boot myself

---

### Post by meierfra on 2007-12-23
I'm at a complete loss. For some reason grub cannot find "menu.lst" at boot -up.

Maybe there is something wrong with your file sytem.   You might run  e2fsck from the LiveCD.  I don't know much about fsck and e2fsck but here is a nice post by Herman ([http://ubuntuforums.org/showthread.php?p=2690508#2]("http://ubuntuforums.org/showthread.php?p=2690508#2")

---

### Post by StephX on 2007-12-23
> **meierfra said:**
> I'm at a complete loss. For some reason grub cannot find "menu.lst" at boot -up.

Maybe there is something wrong with your file sytem.   You might run  e2fsck from the LiveCD.  I don't know much about fsck and e2fsck but here is a nice post by Herman ([http://ubuntuforums.org/showthread.php?p=2690508#2]("http://ubuntuforums.org/showthread.php?p=2690508#2")

well i'm tired of trying to fix it, so i'll just do a reinstall

i got all the important stuff thanks to pyro's help

I appreciate you taking the time to try and help and i'll check out that link and maybe learn a little something in case this happens again.

al

---

### Post by meierfra on 2007-12-23
> well i'm tired of trying to fix it, so i'll just do a reinstall

I guessed that  that's what you would do. Good luck.

---

### Post by StephX on 2007-12-23
just seems to make sense in terms of time loss. in the same time i've spent trying to fix this isue i could have reinstalled ubuntu and reinstalled all the misc programs i had as well.

i just hope this doesn't happen again. i thought linux systems were supposed to be more stable (not bashing here, i'm still a big linux/ubuntu fan) but in the year or less since i've been using ubuntu i've had to reinstall twice. this time, and once before when i tried to upgrade to 7.10 and the screen was an unreadable blurry mess. but hey, at least it's not microsoft.

it also seems that my firefox and general ubuntu settings are salvagable (according to some prompts i've received since beginning this reinstall) - if that's true i'll really be a happy camper.

thanks again for the help,
al

---

### Post by cksubs on 2007-12-24
I'm having this same problem, but after only using Ubuntu for a day. From the OP's experience here I'm just going to reinstall, seems like it will be much easier.

BUT

When I try to boot XP, I get the same grub error. My whole booting scheme might be rather complicated due to the fact that I'm triplebooting an EFI/dos(or whatever it is) mix on my Mac, but do you think the XP boot will be fixed with an Ubuntu reinstall? OS X is booting fine now, so I think that should be okay, but I'd much rather not have to reformat my XP partition...

---

### Post by robertchahine on 2008-04-26
> **pyronaut said:**
> specifically try this 
grub> configfile (fd0)/boot/grub/menu.lst 

replace fd0 with you hard drive name... if you are not sure you can look it up once you boot the live CD..

i had a backup for the menu.lst called menu.lstback, so i did configfile.../menu.lstback and it worked like a charm, thanks man

---

