---
title: "Compaq Armada m700, Pentium III: Issues with installing Lubuntu via BusyBox"
date: 2014-04-11
forum: General Help
---

### Post by charitosha on 2014-04-11
Few days ago i found my first laptop ever - compaq armada m700, and decided to install lubuntu.
the thing is, i tried to do the installation a bit unconventionally, and now i have a problem to solve... #-o
So while in XP(which i want to get rid off) i made a 2nd partition, formated in FAT32, and burnt the iso image overthere(sda2) . I thought that it will start booting from there(which it did) and then through the installation process i'll wipe out xp(can't get to that part yet.)
So the installation stops at the step where it detects and mounts the cd-rom. it gives me an error saying that it couldn't mount the cd-rom because it was empty(duh!).
i tried to do the following: mount -t /dev/sda2 /sr0 and also: mount -t /dev/sda2 /dev/sr0. Both times it couldn't find sr0 in /etc/fstab.
Please tell me this: if it's not possible to mount like this, how can i redirect the installation process into sda2 where the iso lies?
Please bear in mind that i cannot get into xp anymore(as far as i'm concern), so it looks like i have to do it via busybox, which should be possible and would be really cool! :p

_Kind Regards!_

p.s. i looked in this forum before posting, found some infos but nothing particular to my case... i am asking for some guidance

---

### Post by charitosha on 2014-04-13
Ok so i tried to install Lubuntu 12.04
at lubuntu installation screen, the only difference is that i don't have the "Try Lubuntu without installing" option (the root cause of my problem)
Q1: why i don't have the "Try Lubuntu without installing" option?

when in this screen if i press esc i get a pop-up saying :"You are leaving the graphical boot menu and starting the text mode interface"
if ok is pressed the display goes black, the word boot is shown with the cursor next to it i.e. boot: _
i made 2 attemps
boot: /boot/grub 
invalid or corrupt kernel image
boot: /boot/grub/kernel.img
Could not find kernel image: /boot/grub/kernel.img
Q2: why did the above happened?

i believe that the problem arises when while trying to do the installation, i get to the step where it "detecting hardware to find cdrom" and then replies that the cdrom is empty(which it is) and cannot go any further. then i cancel the installation get a window with some options and choose the buil-in shell option. i get the following:
BusyBox v1.18.5 (ubuntu 1:1.18.5-lubuntu4) built-in shell (ash)
~#
Q3: # means that i have su privileges right?

for now i'm just wondering around the files that i see from ls and reading about them from the net.
Q4:how is it possible to make the installation process to look for the kernel image in the sda2 partition?

i am just asking for some pointers and guidance, because i want to make it on my own, i'm believe it's a good way to learn!

---

### Post by mörgæs on 2014-04-13
I would consider an M700 too old to be of any use. How much memory does it have?
If you nevertheless want to experiment I recommend the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") 13.10. Best is to have some unformatted space left on the drive before installing.

---

### Post by ibjsb4 on 2014-04-13
A P3 with a 128M of ram ..

May want to have a look at Puppy.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

The try lubuntu option probably can't run on that.

---

### Post by charitosha on 2014-04-13
actually my RAM is 378.324 MB and cpu 746.306 MHz. i've double checked these values. 
Isn't this ram enough for Lubuntu? And also, i'm _stuck_ in the lubuntu installation as i say in my 1st post, i cannot even access XP let alone try different Linux flavor.
Can somebody, please, answer my 3 questions in my 2nd post?

---

### Post by sudodus on 2014-04-13
I have a few unconventional methods to boot very old computers, but before suggesting which method would suit in your case I have some questions:

- Can you boot from a CD or from USB?

- or must you boot from the internal HDD? In this case, can you take the HDD out of the armada and connect it to another computer?

---

### Post by ibjsb4 on 2014-04-13
Rage Mobility P/M AGP 2x

Looks to be supported

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

---

### Post by sudodus on 2014-04-13
> **charitosha said:**
> Ok so i tried to install Lubuntu 12.04
at lubuntu installation screen, the only difference is that i don't have the "Try Lubuntu without installing" option (the root cause of my problem)
Q1: why i don't have the "Try Lubuntu without installing" option?

What Lubuntu iso file did you download? the desktop iso offers "Try Lubuntu without installing", the alternate iso does not, but it can install in computers with lower RAM and when there are problems with the graphics.

What tool did you use to make a drive bootable? I did not quite understand what you made bootable and how to made it bootable.
> 
when in this screen if i press esc i get a pop-up saying :"You are leaving the graphical boot menu and starting the text mode interface"
if ok is pressed the display goes black, the word boot is shown with the cursor next to it i.e. boot: _
i made 2 attemps
boot: /boot/grub 
invalid or corrupt kernel image
boot: /boot/grub/kernel.img
Could not find kernel image: /boot/grub/kernel.img
Q2: why did the above happened?

I don't understand enough [yet] to answer this question
> 
i believe that the problem arises when while trying to do the installation, i get to the step where it "detecting hardware to find cdrom" and then replies that the cdrom is empty(which it is) and cannot go any further. then i cancel the installation get a window with some options and choose the buil-in shell option. i get the following:
BusyBox v1.18.5 (ubuntu 1:1.18.5-lubuntu4) built-in shell (ash)
~#
Q3: # means that i have su privileges right?

Yes, but busybox is a very limited shell, you can only run a few commands compared to running a full bash shell. I must admit, that I don't know much about what is possible is busybox. I try to avoid getting there ;-)
> 

for now i'm just wondering around the files that i see from ls and reading about them from the net.
Q4:how is it possible to make the installation process to look for the kernel image in the sda2 partition?

I will reply in a general way. If the installation works properly, you can install Lubuntu to any partition, that is big enough. The installer can reformat it if necessary.

You have enough RAM for that, trying to ***install Lubuntu 13.10***. But don't install Lubuntu 12.04, it has no long time support and has passed end of life. (Furthermore, that installer needs more RAM.)


> 
i am just asking for some pointers and guidance, because i want to make it on my own, i'm believe it's a good way to learn!

But as I wrote before, some other installer might be better. And Lubuntu Core might be better than standard Lubuntu. Or even some other distro which is ultra light weight.

---

### Post by charitosha on 2014-04-13
i burnt the iso in the hdd so i could take it out and connect it to my pc (it will take me a bit of time because it has an ide conector).
because i burnt it in the hdd it looks that now i'm stuck with it and have to do it from there...
what can you connect via the Rage Mobility???

---

### Post by sudodus on 2014-04-13
> **charitosha said:**
> i burnt the iso in the hdd so i could take it out and connect it to my pc (it will take me a bit of time because it has an ide conector).
because i burnt it in the hdd it looks that now i'm stuck with it and have to do it from there...

Are there any files, that you need to save before overwriting them?

Is it OK to use the whole drive for Lubuntu (and overwrite whatever is on the HDD?

It is possible to install a Lubuntu system in one computer, and to port it to another computer, and it will run, as long as you use free drivers (opposite to proprietary drivers, typically for graphics and wifi).
> 
what can you connect via the Rage Mobility???
Rage is the graphics chip, and Ibjsb4 told us, that Lubuntu's graphics are likely to work with it.

---

### Post by charitosha on 2014-04-13
i did use the alternate 12.04 iso, too bad for me.
at the begining i wanted to use unetbootin but it didn't allow me to burn the iso in a hdd partition, thus i used lilo.

now my problem is that even if i wanted to use other lubuntu iso, or even a lighter distribution all together,
i don't think it's possible since i burnt the iso in a hdd partition and when i switch the laptop on
it automatically goes to the lubuntu instalation.

i do want to use the whole hdd for linux, this is what i wanted to do in the 1st place, so if it's possible
to install a Lubuntu system in one computer, and to port it to another computer, as sudodus said,
it would be awesome.

---

### Post by sudodus on 2014-04-13
Yes, I have done this many times. The concept on a USB drive with an installed system builds of the concept of a portable system. In the same way, a system on another drive, for example an IDE HDD is also portable between computers, where you can connect IDE drives and even to other computers if you have a 'USB to IDE & SATA adapter'.

So you can install ***Lubuntu 13.10*** into the HDD when connected to another computer, and then re-connect it into your old armada. It is possible to use ***mkusb*** to flash the iso into a USB drive, but you can 'toggle USB-only' with u, which makes IDE and SATA drives available as targets. But you cannot flash back to the live drive (the drive you booted from). See this link about mkusb

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

-o-

If you want a smaller system for example Lubuntu Core, you can start from the ***Ubuntu mini.iso***. But the network will not be portable in that case unless you tweak it. But you can install ***Lubuntu Core Saucy*** from a tarball with the ***One Button Installer***, and that version will be portable. (And you can install and use the One Button Installer itself, the version based on Lubuntu, but then it is bigger again.)

[One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971") 

or you can try to install some very small systems, including ***Lubuntu Core Trusty*** from a compressed image with the experimental ***9w*** installer according to the description in this link (posts #88 and #89 and following)

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

Read about these methods, ask about them and decide which way to go!

---

### Post by charitosha on 2014-04-13
thanks for all the info! really!
just took out the hdd. i'll reply as soon as i'll have some news!

---

### Post by charitosha on 2014-04-14
Ok so i was able to install successfully Lubuntu 13.10 in the hdd. The thing is that i did the installation via my desktop pc. so far so good.
 Then i inserted the hdd back into the laptop. Switched it on.
Booting process started. Got until the Lubuntu loading screen.
Then, suddenly the display goes black. The underscore is shown at the top left corner, going on/off. Nothing is written before the underscore.
For a while the hdd , periodically, makes a sound that it get stuck. Some horizontal white stripes are shown, randomly.
And that's how far it gets....

I was able to run XP on this laptop. Is Lubuntu heavier than xp???
is it more intense on the graphics???
i am really lost right now, and losing hope that i'll be able to run lubuntu in this laptop...
does anyone has any ideas or thoughts that i could look into???

---

### Post by sudodus on 2014-04-14
Try with a boot option. foo=bar is only an example. Try ***nomodeset*** and ***text***. See this link

[URL="http://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter"]http://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter

[/URL]

---

### Post by charitosha on 2014-04-15
I was able to get to the grub menu. Pressed 'e' while Ubuntu was hihglited, not quite sure why it says Ubuntu and not Lubuntu(because it IS lubuntu). got the following:
GNU GRUB version 2.00-19ubuntu2
setparams 'Ubuntu'
recordfail
         load_video
         gfxmode $linux_gfx_mode
         insmod gzio
         insmod part_msdos  
         insmod ext2
         set root='hd2,msdos1'
         if [x$feature_platform_search_hint = xy ]; then
            search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci\2,msdos1 05ebc43b-55ee-42a5-8314-d3accfe7f93a
        else
           search --no-floppy --fs-uuid --set=root 05ebc43b-55ee-42a5-8314-d3accfe7f93a
        fi
        linux /boot/vmlinuz-3.11.0-19-generic root=UUID=05ebc43b-55ee-42a5-8314-d3accfe7f93a ro persistent q\uiet spash $vt_handoff
        initrd /boot/initrd.img-3.11.0.19-generic

isn't possible to add parameters here like nomodeset or acpi_osi=? if so where? under linux /boot??:confused:

i also i booted to recovery mode, and from the menu that appeared i choose "root     drop to root shell promt"thought that via the shell i could modify grub.
as a sudo, i typed gksudo gedit /etc/default/grub. the reply was:
(gksudo:1533): Gtk-WARNING **: cannot open display.

basically i found various threads with usefull infos but not quite sure where to imply them. If possible, don't really want to take out the hdd and reformat it to be able to choose the parameters at the installation. Don't really learn like that...

---

### Post by sudodus on 2014-04-15
> **charitosha said:**
> 
        linux /boot/vmlinuz-3.11.0-19-generic root=UUID=05ebc43b-55ee-42a5-8314-d3accfe7f93a ro persistent quiet spash $vt_handoff
        
Add it among the other boot options at the end of the linux line. You can also remove quiet splash to get more feedback during the boot process.
> 
as a sudo, i typed gksudo gedit /etc/default/grub. the reply was:
(gksudo:1533): Gtk-WARNING **: cannot open display.

basically i found various threads with usefull infos but not quite sure where to imply them. If possible, don't really want to take out the hdd and reformat it to be able to choose the parameters at the installation. Don't really learn like that...

gedit needs graphics to run (and is not part of Lubuntu). Use the text editor ***nano*** in text mode and ***leafpad*** in graphics mode.

You can edit the linux line temporarily if you press **E** at the grub menu, move the cursor and type in **nomodeset** and/or **text**.

Afterwards you boot with the new boot options with the hotkey combo ***ctrl +x***

---

### Post by charitosha on 2014-04-15
i tried individually nomodeset and acpi_osi= and together. also tried acpi_osi=\"Linux\", just in case...
if i put the 'text' parameter then i get to... somekind of terminal in which minimal bash-like editing is supported
also tried vga=791 and vga=773  ,perhaps the graphics were to heavy or something... especially at the vga=773 i 
saw noticeable difference in the Lubuntu logo but nothing changed.
the black screen,with the underscore and the random horizontal lines kelp appearing
 
At the end tried acpi=off. But even this parameter didn't work.  
 
 I boiled down to the fact that i don't know what is causing this problem and thus don't know what parameters 
 to look for.
Any suggestions?

---

### Post by sudodus on 2014-04-15
You installed Lubuntu 13.10 did you? Maybe it is 'too new' and does not support such old hardware. Try something older, (built on an older version of Ubuntu, but still updated with current security updates), LXLE

Or maybe you will have better luck with a really small distro like Puppy, Tiny Core or DSL. See this link for more details [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

Be prepared that it might be very hard (or impossible) to get something working well in the old Armada.

---

### Post by charitosha on 2014-04-15
ok i'll try LXLE and even puppy linux, but just to make a statement i was able to run XP in armada m700. that's why i tried Lubuntu first...

---

### Post by sudodus on 2014-04-15
Yes, but XP was developed more than 10 years ago. Maybe the odds are best with DSL, which is built around a very old kernel, I think 2.4. But the other distros (including LXLE) are much nicer so they are worth trying.

---

### Post by ibjsb4 on 2014-04-15
Even though your video is supported, it may not be well supported by the latest kernel.  Let us know what happens.

---

### Post by charitosha on 2014-04-16
quick question, somebody please answer:
if ii connect my old ide hdd to my desktop pc, and via my desktop pc, install e.g. LXLE in that old hdd.
then after installation, insert that hdd in my compaq laptop.
is it going to work or it will not work out?(for reasons beyond my knowledge)

---

### Post by charitosha on 2014-04-16
Ok so i'm sending this from my compaq armada m700, having LXLE. =d>
worked from the very first attempt!

to sum everything up what i understood from this topic, and corrections are always welcomed!

1) It's not possible to install any OS via BusyBox shell simply because it doesn't have enough commands or it's not built for this purpose...
2)Lubuntu can't run in armada(at least in mine). 
But why is this the case? LXLE worked immediately. i don't get this.

and 3) it's ok to connect an hdd to a desktop pc, and via the desktop pc, install any OS in that hdd.
and then after installation, insert that hdd in a laptop.

Last but not least thanks for the support and guidance!
I wouldn't be able to do on my own!

---

### Post by claracc on 2014-04-16
Congratullations!, you have resurrected your old pentium III.

I only can answer your number 2 question, I am sure you could run lubuntu in this computer but only till 12.04 release wich is out of support now. The question is releases above 12.04 have quit graphic drivers for such an old hardware. I think alternate 12.04 lubuntu iso is possible to install in your case. Also you have to be aware of the PAE question.

I have and old pIII laptop from 2002, 1GHz CPU, 512 Mb RAM and sis 630/730 (maximum 64 MB) graphics card running lubuntu 12.04, impossible to install any more advanced lubuntu release, tried 12.10 and 13.10 and I obtain black screen. Anycase, I can surf web with firefox (I know it is unsecure), of course, it is slow and I have to forgot to play any flash video (also using an outdated adobe flashplayer), but you can do some tweaks using user scripts as viewtube for videos in certain web pages.

 I will try lxle 12.04 release next summer since it seems to fit the specifications of these old dinosaurs.

---

### Post by mörgæs on 2014-04-16
> **claracc said:**
> 
Also you have to be aware of the PAE question.


No, all Pentium 3's support PAE.

---

### Post by sudodus on 2014-04-16
> **charitosha said:**
> Ok so i'm sending this from my compaq armada m700, having LXLE. =d>
worked from the very first attempt!

to sum everything up what i understood from this topic, and corrections are always welcomed!

1) It's not possible to install any OS via BusyBox shell simply because it doesn't have enough commands or it's not built for this purpose...
2)Lubuntu can't run in armada(at least in mine). 
But why is this the case? LXLE worked immediately. i don't get this.

and 3) it's ok to connect an hdd to a desktop pc, and via the desktop pc, install any OS in that hdd.
and then after installation, insert that hdd in a laptop.

Last but not least thanks for the support and guidance!
I wouldn't be able to do on my own!

Congratulations :KS

1) I have not heard of installing via BusyBox.

2) Why? Probably because the drivers for graphics in Lubuntu 13.10 do not work with your hardware. So my reply is the same as that of *claracc*.

3) Ubuntu and Ubuntu based distros are ***portable*** unless you install proprietary drivers. (An exception is a system installed from the mini.iso and Ubuntu server, where the default network is not portable unless you install lubuntu desktop or some equivalent system, which brings network-manager.)

This portability is due to the fact that linux is free (contrary to Windows and MacOS, where licence restrictions and proprietary drivers prevent portability).

---

### Post by claracc on 2014-04-17
> **mörgæs said:**
> No, all Pentium 3's support PAE.
 Ah!, I didn't know.

I said it to be aware of PAE because I tried bodhi linux 32 bit in my old PIII and I had to use the non-PAE iso instead of PAE one, since the PAE one gave me a black screen too. Perhaps the problem was other.

---

