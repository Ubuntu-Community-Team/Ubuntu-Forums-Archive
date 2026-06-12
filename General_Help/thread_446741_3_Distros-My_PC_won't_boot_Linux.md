---
title: "3 Distros-My PC won't boot Linux?"
date: 2007-05-17
forum: General Help
---

### Post by johnwillyums on 2007-05-17
Hi, I've been following this project since January and have posted encouragements before. However I became impatient and over the last week have tried to install Mandriva, Ubuntu and now Wubi and none of them will boot.
This is a long sad tale. I got a free dvd of Mandriva from a magazine and installed it. The installation seemed to go fine but it wouldn't boot. I got lots of help from the people on Mandriva Forum. They told me how to edit the boot line and suggested I add noapic nolapic and load_modules=off. I did this but still couldn't get through the boot. They suggested I try Ubuntu and by coincidence my Ubuntu 7.04 live cd from Shipit arrived so I tried that. I could not get that to boot either.
I have posted details about that on Ubuntu Forums Absolute Beginners section (Can't boot-is it my hardware?)
People on there suggested I edit the boot line in a similar way as before- adding noapic nolapic .This seemed to get me a bit further than before. It stopped on a page for about a minute then eventually stopped on one with several do_page_ fault lines and a couple of error code lines.
There was a line of these =========== and then some code-2e 65a etc and then-
[391.687622]EIP:[<c011ddac>]kmap_atomic+0x5c/0xa0 SS:ESP 0068=f37b3ebc
[391.687826]<6>note:udevd[6535]exited with preempt_count 1

I then tried the latest version of Wubi and it has installed fine but won't boot.
My pc is about 2 years old and consists of a Intel Celeron R 3.06 chip with 1gb of RAM plus two internal drives- a C. drive 80gb which has my Windows installation on it. This was partioned by Mandriva (about half of it). I have deleted all the non NTFS partions and removed Mandriva but the drive is still partioned and now shows in my computer as New Volume K. I tried to expand the C drive with Diskpart but it won't do it. I don't think this is crucial as it is now NTFS and I can access it. Wubi is installed there on the New Volume K drive. I also have a 120gb D drive which is 3/4 full of music and photos. I also have a Nvidia 6600 graphics card and a Canon printer.

Can you help? The Mandriva people seemed to think I have a hardware problem and suggested Ubuntu as it  has a newer kernel. When I try and boot Wubi I get to the splash screen but the progress bar only moves about half an inch. I got further with Ubuntu with noapic nolapic added but I can't seem to get a text boot by pressing F6 with Wubi.
Am I doomed to never experience Linux. Please help.
 John Williams

---

### Post by ago on 2007-05-17
When you say you installed wubi, do you mean that you went through windows AND rebooted AND went through all the blue screens with redprogressbars AND got stacked on second reboot, or do you mean that you finished the first part (windows) and got stacked on first reboot?

---

### Post by johnwillyums on 2007-05-17
Hi Ago. I think I mean I got stacked on first reboot. I went through the installation process and Ubuntu now appears in my boot menu. When I select I get a splash screen and progress bar but the bar only moves a few centimetres and then stops. As I say the Wubi folder now sits in my New Volume K. Following advice on the Ubuntu Absolute Beginners Forum I tried adding noapic nolapic and ide+nodma to the boot line on the live cd and booting that. This seemed to be succeeding and I sat for about an hour and a half watching text flow past, eventually I felt that it should not be taking this long, the numbers in the left hand column had reached 7800+.
Therefore I did a hard shutdown and have asked for advice on the Ubuntu Forum but none received yet. Should I have been more patient and waited longer? This seems to be the furthest I've got with any of my attempts but was showing no signs of ever ending and booting. I know you are dealing with Wubi and may have some advice on that but the above may be of some use. Thanks for listening, John Williams

---

### Post by ago on 2007-05-17
There are 2 different "splash" screens. One on a black background with a fancy Ubuntu logo like this

[img]http://www.mainardistefano.org/blog/wp-content/uploads/linux/usplash.png[/img]

and one not so fancy with a blue screen and some white text like the following

[http://www.linuxshots.com/main.php?g2_view=core.DownloadItem&g2_itemId=269&g2_serialNumber=2](http://www.linuxshots.com/main.php?g2_view=core.DownloadItem&g2_itemId=269&g2_serialNumber=2)

Which one do you mean?

---

### Post by johnwillyums on 2007-05-17
This is the one I get now but I think I had the blue one with the box originally when I first installed Wubi. Sorry to be unsure but I've been booting and rebooting both Wubi and Ubuntu and got confused. Certainlly the one you show is what i now get if I select Ubuntu in the boot menu. John Williams

---

### Post by ago on 2007-05-17
> **johnwillyums said:**
> This is the one I get now but I think I had the blue one with the box originally when I first installed Wubi. Sorry to be unsure but I've been booting and rebooting both Wubi and Ubuntu and got confused. Certainlly the one you show is what i now get if I select Ubuntu in the boot menu. John Williams

So the black one... That's good news since it means that the kernel was able to boot at least once...

You may want to edit c:\wubi\boot\grub\menu.lst, in the kernel lines remove "quiet splash", possibly append noapic & co. See where it jams and report the exact lines.

---

### Post by johnwillyums on 2007-05-17
I just tried that or at least what I think you meant. I opened the Wubi folder on my K. drive and then opened the GRUB folder. This revealed 2 files. I tried to open the one marked "menu.1st" but Windows won't let me giving the usual about not knowing what programme created it. Is that what you meant? If so what should I do? Thanks for your help, John Williams

---

### Post by ago on 2007-05-17
Yes that is the one and you can use notepad to edit it

---

### Post by johnwillyums on 2007-05-17
Sorry to be so stupid but I don't understand and have never used notepad. Is it a windows programme? Could you babytalk me through it? John Williams

---

### Post by ago on 2007-05-17
yes open notepad from accessories (or wordpad) and from that open and edit menu.lst

---

### Post by johnwillyums on 2007-05-17
Ok. I found notepad and dragged and dropped menu!st into it and it opened. There is a very long series of commands etc in there so I shall remove quiet splash and ad noapic nolapic and ide=nodma. I'll report back shortly. John Williams

---

### Post by ago on 2007-05-17
just "noapic nolapic" first

---

### Post by johnwillyums on 2007-05-17
Ok. I hadn't got your message so I tried all three additions first-noapic nolapic ide=nodma. When I deleted quiet splash a new word appeared- rooinitrd- the second o was rectangular rather than a regular o. Not knowing what to do I deleted that and added my three words. They did not seem to type in very well and the line kept jumping down to the next one. I then shut down and tried rebooting into Ubuntu. after the two rapid black text pages the black splash with Ubuntu logo appeared. Unfortunately the progress bar only moved about half an inch then stopped. I then went back into windows and got your message so I went back and deleted ide=nodma and tried again with exactly the same result. John Williams

---

### Post by ago on 2007-05-17
If you see the splash it means you have not deleted "quiet splash" or you have removed them from the wrong file/wrong place. Remove all of them.

---

### Post by johnwillyums on 2007-05-17
Hi. I've looked and there is no sign of quiet splash in the boot grub folder. I looked in both menu and menu1st. The line in menu1st now finishes boot/linux_setup_iso=ubuntu-7.04-alternate-i386.iso followed by noapic and then nola. The rest of the word(pic) has gone to the start of the next line even though there is room for it. Should I look in some other place in Wubi? John Williams

---

### Post by ecology2007 on 2007-05-17
Your reports are very detailled and containing every required information, but are very hard to read. 
Can you improve your layout in your next posts ?
Thanks forward.

---

### Post by ecology2007 on 2007-05-17
Ok, i have read the whole thread, i think we can solve your problem in two moves.
1st: post here the content of the 1st menu.lst (probably on "c:") and the content of the 2nd menu.lst (probably in k:\wubi\boot\grub)
2nd: we will adjust the command lines accordingly and post them here.

---

### Post by johnwillyums on 2007-05-17
Sorry but I seem to be having a problem with Firefox. Every time I press the return key it crashes. Consequently I cannot leave spaces, start new paragraphs etc. This is a new problem that I first noticed yesterday. John Williams.

---

### Post by johnwillyums on 2007-05-17
Can't find anything to do with Wubi on my C drive. The Wubi flder has installed on my New Volume K drive. Here is the entire contents of Menu1st-```
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        1

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso  noapic nolapic 

```Once again sorry about the layout. I just copied and pasted from Notepad and this is the way it turned out. John Williams

---

### Post by johnwillyums on 2007-05-17
Just ran a search for Wubi on my C. drive and found this- WUBI-7.04-test2 on my desktop, WUBI-7,04-TEST2-EXE-IC249....C:\WINDOWS\prefetch and WUBI-PWD,EXE-3908AE18.pf...C:\WINDOWS\prefetch

I can see the Wubi file on my desktop obviously but can't find the other two although they are somewhere in C. Is this where you meant?
John Williams

---

### Post by ago on 2007-05-17
```


default 0
timeout 1

## ## End Default Options ##

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux ro noapic nolapic 
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux noapic nolapic ro
initrd /wubi/boot/initrd

```

---

### Post by aqueous on 2007-05-17
hi, this is my frist time ever trying out linux. After the second reboot i would get the fancy ubuntu screen and after that some carbon fiber looking screen ( where the lighting would just fade in and out). When that screen appears my computer would totally freeze w/ my keyboard locking up. I can't do anything but a manual reboot. Any suggestions?

---

### Post by johnwillyums on 2007-05-18
Good Morning, do you mean me to delete everything after- #updatedefaultentry=false- and then add your ammended code?
Thanks for your tremendous support, John Williams

---

### Post by ago on 2007-05-18
> **aqueous said:**
> hi, this is my frist time ever trying out linux. After the second reboot i would get the fancy ubuntu screen and after that some carbon fiber looking screen ( where the lighting would just fade in and out). When that screen appears my computer would totally freeze w/ my keyboard locking up. I can't do anything but a manual reboot. Any suggestions?

If that is after the progressbar has fille up, it is probably an X configuration issue. You should check the general support forum for that.

---

### Post by ago on 2007-05-18
> **johnwillyums said:**
> Good Morning, do you mean me to delete everything after- #updatedefaultentry=false- and then add your ammended code?
Thanks for your tremendous support, John Williams

Just replace c:\wubi\boot\grub\menu.lst with the above.
PS I am not really convinced you did actually complete the installation...

---

### Post by johnwillyums on 2007-05-18
Hi. Ok I went into K:\wubi\boot\grub\menu1st and dragged it into notepad. I deleted everything and copied and pasted your ammended code. I'm afraid it doesn't seem to have made any difference. When I tried to boot I got a couple of rapid black with white text pages (as before) then the black splash page with the ubuntu logo and the orange bar. This only moved a few centimetres as before and then stopped. I don't seem to be getting anywhere it's most disappointing. Thanks and have you any more suggestions. John Williams

---

### Post by ago on 2007-05-18
> **johnwillyums said:**
> Hi. Ok I went into K:\wubi\boot\grub\menu1st and dragged it into notepad. I deleted everything and copied and pasted your ammended code. I'm afraid it doesn't seem to have made any difference. When I tried to boot I got a couple of rapid black with white text pages (as before) then the black splash page with the ubuntu logo and the orange bar. This only moved a few centimetres as before and then stopped. I don't seem to be getting anywhere it's most disappointing. Thanks and have you any more suggestions. John Williams


Can it be that you have another wubi folder on a different partition and that is used instead?

---

### Post by johnwillyums on 2007-05-18
I don't think so. I did a search and posted the result previously. I have the Wubi installer file on my desktop with the logo. If I try to open that I think it will install again. Just ran a search for Wubi on my C. drive and found this- WUBI-7.04-test2 on my desktop, WUBI-7,04-TEST2-EXE-IC249....C:\WINDOWS\prefetch and WUBI-PWD,EXE-3908AE18.pf...C:\WINDOWS\prefetch
I can't seem to locate the prefetch files but they are somewhere in C. The Wubi folder installed on K. New Volume which is a part of C.
John Williams

---

### Post by ago on 2007-05-18
All you have to do is open each drive: c:, d:, e:, f:, g:... and see if there is a wubi folder in there.
Also check the menu.lst that you find in the ROOT of each of those drives. It should only contain

default 0
timeout 1

title Ubuntu
find --set-root /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst

---

### Post by johnwillyums on 2007-05-18
Hello. Not sure exactly what you mean by ROOT but have searched all drives. I found the prefetch files in WINDOWS on the C.drive. Also opened the Boot Configuration Settings on the C.drive and found this
-[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
c:\grldr="Ubuntu"

Is this of any help? John Williams

---

### Post by johnwillyums on 2007-05-18
Just found a load of code in BOOT\Winboot. I tried to post it but it's too long. There was some mention of "not enough memory" and other seeming errors etc but mainly just code letters. Don't know whether this is important. John Williams

---

### Post by johnwillyums on 2007-05-18
Hi. Have to go to work now. Hopefully make more progress tomorrow afternoon. Thanks, John Williams

---

### Post by johnwillyums on 2007-05-19
Hi Guys. Hope there is somebody there. I've just run some exhaustive searches of my drives- C. D. and New Volume K. My other drives are cd and dvd removable media and if I try to open them I get "insert disk". Anyway no sign of Wubi except in the Wubi folder on K. However when I opened the Wubi folder and then GRUB there are two menu files in there. One is called menu LST file and the other is menu.1st ,with a little squiggle sign, LST file.
It is the menu.1st which I have altered as you suggested.
I tried to open the file marked menu and it opens with Open Office. There are three pages of code etc. in there the end part of which looks very much like the menu.1st file before I altered it to your suggestion. 
It's even got the "quiet splash" bit so thats probably why I still get the splash when I try to boot.
Should I delete this whole lot and replace it with your shorter suggestion?
I'd post it but I think it will be too long for this forum to accept.
Hope you haven't deserted me yet as I'm still determined to make this work if at all possible.
Thanks, John Williams

---

### Post by ecology2007 on 2007-05-19
```
default 0
timeout 10

## ## End Default Options ##

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux ro noapic nolapic 
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux noapic nolapic ro
initrd /wubi/boot/initrd
```

You can replace the content of /wubi/grub/menu.lst by that.
You can copy /wubi/winboot/menu.lst to c:\, d:\ and k:\

---

### Post by johnwillyums on 2007-05-19
Sorry, Not sure I understand. I already replaced the contents of \wubi\grub\menu.1st with this. Menu.1st is in the grub folder along with the menu file.

I have not done anything in the winboot folder
This contains - bzr.log.XP6HPr, COPYING FILE,grldr, grldr.mbr, grub, menu LST file and READMEGRUB4DOS Text Document.

There is no menu.1st file in the winboot folder.

Could you explain a bit more you want me to do please.
Sorry to be such a newbie, John Williams

---

### Post by ecology2007 on 2007-05-19
lst begins with a small L, not with a 1, not with a big i. Get sure it is menu.lst. It means menu list, not menu first.
 /wubi/boot/grub/menu.lst and wubi/boot/winboot/menu.lst have the same name but are not the same files.
menu.lst is the only file in wubi/boot/grub.

The one you have to replace is /wubi/boot/grub/menu.lst.

You can also probably see c:\menu.lst which is a copy of wubi/boot/winboot/menu.lst.

---

### Post by johnwillyums on 2007-05-19
Yes. The file I have replaced is menu.lst. Sorry, I had mistaken it for a one. Underneath it it says LST file 1kb in faint grey letters with squiggly horizontal punctuation lines

The other file in grub is just called menu Also an LST file 5kb but with no punctation.

 Does that one need changing? As I've said I already made those changes and no boot.

Thanks, John Williams

---

### Post by johnwillyums on 2007-05-20
Hi. I am no further forward here. You mentioned copying the menu file from K.\boot\winboot to my c. and d. drives.
Here is the content of the menu file from winboot-

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

## Pretty colours
#color cyan/blue white/blue

#### KERNEL PARAMETERS ####

# the /folder/path paramater must be matched in the following 3 lines:
#
#find --set-root /folder/path/linux
#kernel /folder/path/linux find=/folder/path/linux
#initrd /folder/path/linux
#
#you must replace /folder/path with the path where the files where installed
#do not use the same folder name on different partitions

## To specify the ISO (otherwise the first one in the folder will be used)
#setup_iso=setup.iso

## To specify the root harddisk image(otherwise root.img is assumed)
#root_virtual_disk=system.virtual.disk

## To specify the home harddisk image (otherwise home.virtual.disk is assumed)
#home_virtual_disk=home.virtual.disk

## To specify the swap harddisk image (otherwise swap.virtual.disk is assumed)
#home_virtual_disk=swap.virtual.disk

## To specify extra harddisk image (otherwise extra.virtual.disk is assumed)
#extra_virtual_disk=extra.virtual.disk

## Debug
#pause_for_debug debug

#### MENU ITEMS BELOW HERE ####

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst

When you say copy it to c. and d. drives what exactly do you mean?
Should I just drag and drop it into those drives?

Thanks for your help, John Williams

---

### Post by ago on 2007-05-20
> **johnwillyums said:**
> 
When you say copy it to c. and d. drives what exactly do you mean?
copy to c:\ and d:\. Toplevel folder.

---

### Post by johnwillyums on 2007-05-20
Ok. Tried that. Went into wubi\boot\winboot and dragged the menu file into my c. and d.drives.
No change I'm afraid. Got the fancy splash screen and the orange bar moved a few centimetres and then stopped. 
Exactlly as before.
I'm losing hope. What do you think?
John Williams

---

### Post by johnwillyums on 2007-05-21
Hi. Are you as stuck as I am? Should I give up on the idea? Yours, John Williams

---

### Post by ago on 2007-05-21
> **johnwillyums said:**
> 
I'm losing hope. What do you think?


I think that you have edited the wrong file because I do not see how you can have a graphical boot without an explicit "splash" argument. 

What you can do is to rename all the ?:\wubi\boot\grub\menu.lst files until you find the right one. If you rename the correct one you will get an error when you reboot. When you find the correct one comment hidemenu and set timeout to 10. So you will be shown a second boot menu. Then you can select both options and see what happens.

---

### Post by johnwillyums on 2007-05-21
Hello. I agree that it seems wrong that I should still be getting the splash screen when trying to boot and that the wrong file must have been edited. Two days ago ecology 2007 wrote:

> menu.lst is the only file in wubi/boot/grub.

The one you have to replace is /wubi/boot/grub/menu.lst.

You can also probably see c:\menu.lst which is a copy of wubi/boot/winboot/menu.lst

There is no menu.lst file in wubi/boot/winboot.
The file is just called menu and is just one page long-I posted it one day ago.

In wubi/boot/grub there are 2 files.
The first one is called menu and the second one menu.lst.
This menu file is nearly three pages long and is clearly not a copy of the menu file in winboot.
Also it does mention "quiet splash"- this is the final page:

kernel   /wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd    /wubi/boot/initrd.img- 2.6.20-15-generic
boot

title      /Ubuntu kernel 2.6.20-15-generic(recovery mode)
            find--set-root--ignore floppies/wubi/boot/linux
kernel  /wubi/boot/vmlinuz-2.6.20-15 generic find =/wubi/boot/linux ro single
initrd    /wubi/boot/initrd. img-2.6.20-15-generic

title       Ubuntu memtest86+
             find--set-root--ignore floppies/wubi/boot/linux
kernel    /boot/memtest86+bin

###END DEBIAN AUTOMAGIC KERNELS LIST

#This is a divider added to seperate the menu items below fro the Debian
#ones

title Ubuntu(Original Kernel)
find--set-root--ignore-floppies/wubi/boot/linux 
kernel/wubi/boot/linux find=wubi/boot/linux setup-iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd/wubi/boot/initrd
boot

As I say two different menu files (1 in wubi/boot/grub plus menu.lst file-1 in wubi/boot/winboot)

Could this be the problem?

I don't understand what you mean by this:

> What you can do is to rename all the ?:\wubi\boot\grub\menu.lst files until you find the right one. If you rename the correct one you will get an error when you reboot. When you find the correct one comment hidemenu and set timeout to 10. So you will be shown a second boot menu. Then you can select both options and see what happens.


Could you explain it a little more simply and thoroughly please?

Thanks for your patience and continued support, John Williams

---

### Post by ago on 2007-05-21
> **johnwillyums said:**
> 
In wubi/boot/grub there are 2 files.
Just make sure you have only 1 in there. And without quiet splash

```

kernel   /wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd    /wubi/boot/initrd.img- 2.6.20-15-generic
boot

```
that's it, edit this block and remove quiet splash



I now start suspecting though that you had issues with X resolution, not usplash... Anyway, one thing at the time...

---

### Post by johnwillyums on 2007-05-22
Thanks Ago. So shall I delete menu.lst and edit menu as you indicate above? Bear in mind I have already replaced the contents of menu.lst with your suggested code.The file just called menu is three pages long and I have only posted the last part above.
I just want to be clear that I am to delete menu.lst from wubu/boot/grub and edit menu.
Thanks, John Williams

ps. There are 2 mentions of "quiet splash" in the section of menu I have posted -one above and one below the divider should I remove any mention of it altogether?

---

### Post by ago on 2007-05-22
you only want to delete "splash" from within the long file and save.

---

### Post by johnwillyums on 2007-05-22
That will still leave me with 2 files in wubi/boot/grub? John Williams

---

### Post by ago on 2007-05-22
So be it (for next time make sure extensions are shown...)

---

### Post by johnwillyums on 2007-05-22
Hi Ago. Partial success! Well at least I've now got a text boot. I did as you suggested and deleted all references to "quiet splash" in wubi /boot/ grub/menu and it got me a boot in text mode. I've tried to boot 5 times now and the first three stalled (I'll give some details in a moment) the 4th time the boot went on for ages. I let it get to 500+ lines and shut it down , the 5th time similar but I let it get to 700+ and shut it down.

Here's some detail about the first 3 attempts which stalled, just the last few lines:

1)
[50.225491] [<c02f070f>] do_page_fault+0x39f/0x5f0
[50.225658] [<c02f0370>] do_page_fault+0x0/0x5f0
[50.225803] [<c010334b>] work_notifysig+0x13/0x8
[50.225977] =======================

2)
[52.888114] [<c02f0985>] notifier_call_chain+0x25/0x30
[52.888268] [<c0104254>] die+0x114/0x270
[52.888434] [<c02f0661>] do_page_fault+0x2f1/0x5f0
[52.888602] [<c02f0370>] do_page_fault+0x0/0x5f0
[52.888749] [<c02eeb4c>] error_code+0x7c/0x90

3)
[48.988298] [<c02f070f>] do_page_fault+0x39f/0x5f0
[48.988452] [<c0120b40>] default_wake_function+0x0/0x10
[48.998226] [<c02f0370>] do_page_fault+0x0/0x5f0
[48.993373] [<0103346>] work_notifysig+0x13/0x18
[48.993546] =======================
[48.993639] agpgart: AGP aperture is 128M@0xf0000000


So. It feels like we are getting somewhere. I was elated to see it carry on booting on the 4th attempt but it just kept going and the same on the 5th.
Should I have let it keep going?
What do you suggest?
Thanks once again for your help and patience, John Williams

---

### Post by johnwillyums on 2007-05-25
Hi. No change here. I've tried several times and got this endless text boot. Is it trying to boot or just stuck in a loop? Will my cpu blow up? Too many questions. John Williams

---

### Post by johnwillyums on 2007-05-27
Still stuck at a dead end here. Does anyone know whether it would eventually boot? John Williams

---

### Post by ago on 2007-05-27
Try with a live CD that will confirm whether it is a hardware incompatibility or not

---

### Post by johnwillyums on 2007-05-27
I have Ubuntu 7.04 official cd (sent by Canonical) plus I have downloaded the Alternate ISO and burnt it to cd. Which do you recommend I try? Thanks, John Williams

---

### Post by ago on 2007-05-27
The "official" CD (Live CD). Just boot from it and see if it works fine. You can also use that to install if you like and if it works.

---

### Post by johnwillyums on 2007-05-27
Oh well. That did not work either. It tried for a few seconds but quickly stalled. I waited a little while but it is obviously not going any further. Here are the last four lines;                                                                        
[130.993556] [<c0174f8b>] do_system_open+0xcb/0xf0
[130.993702] [<c02f0370>] do_page_fault+0x0/0x5f0
[130.993846] [<c010334b>] work_notifysig+0x13/0x18
[130.993993 ]=======================
 This is most disappointing. Is it the end of the road for me or is there anything I can do to "fix" my hardware?
You may recall I could not install Mandriva from a dvd either. It seems I may never experience Linux.

Thanks for all your help and patience, John Williams

---

### Post by Masonba2000 on 2007-06-05
maybe SGD could help? [http://thejist.info/?p=109](http://thejist.info/?p=109)

---

### Post by ago on 2007-06-05
It's not an issue of bootloader but of hardware compatibility

---

### Post by johnwillyums on 2007-06-09
Yes it seems to be a hardware problem but there is nothing exotic or unusual about my hardware. Is there any way of discovering what the problem is and fixing it or replacing a component or whatever?
Otherwise I'll just have to give up on Linux altogether.
Thanks, John Williams

---

