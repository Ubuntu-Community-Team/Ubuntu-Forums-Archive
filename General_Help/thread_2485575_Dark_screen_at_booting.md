---
title: "Dark screen at booting"
date: 2023-04-02
forum: General Help
---

### Post by satimis on 2023-04-02
Hi all,

DELL 32" monitor
Graphic from AMD CPU

Settings
Resolutions: 3840 x 2160
Refresh Rate: 60.00 Hz

In these two days dark screen started at booting with warning (no problem in the past)

Follow warning popup with a dark screen
```

The current time is not supported by display ....

```
(pls refers to screenshot attached)

Wait a while, then the login page started.  Please advise how to fix this problem.  Thanks

Regards

---

### Post by Dennis N on 2023-04-03
Maybe you already did this, but if you google "the current input timing is not supported by the monitor display" you will get some results. One thing to check is if the cables connecting the monitor to the computer haven't become loose.

---

### Post by ActionParsnip on 2023-04-03
Sounds like the boot splash is set to a different refresh than the screen expects. Considering the OS runs OK after that it's not really broken.
You could mess with it using this
[https://ubuntuhandbook.org/index.php/2021/05/screen-resolution-grub-boot-menu-ubuntu/#:~:text=When%20you're%20at%20Grub,to%20get%20back%20boot%20menu](https://ubuntuhandbook.org/index.php/2021/05/screen-resolution-grub-boot-menu-ubuntu/#:~:text=When%20you're%20at%20Grub,to%20get%20back%20boot%20menu).
Personally I'd just leave it.

---

### Post by satimis on 2023-04-03
Hi all,

Thanks for your advice.

I don't know what is the cause.  There are similar cases on Internet.  I just came across it recently on checking the cause of unable booting Ubuntu 22.04, installed on a 1TB pcie SSD.

I have 2 pcie SSDs, one of 2TB capacity and another one of 1TB capacity, both running Ubuntu 22.04.  I just found unable to boot the Ubuntu 22.04 on 1TB pcie SSD.  Booting it, it always boots the 2TB pcie SSD.  It is quite funny to me.

Regards

---

### Post by yancek on 2023-04-04
Are both install of Ubuntu 22.04 on the 1TB and 2TB drives UEFI installs?  Were both drives attached during both installs?  If so, were both drives attached when installing and was the Ubuntu on the 2TB drive installed last?  If that is the case, then the install on the 2TB drive may have overwritten the boot files on the EFI partition on the 1TB drive.  Do you have an EFI partition on both drives?  If you have an EFI partition on both drives, mount it and check the grub.cfg file on it for the UUID then run the blkid command to find which partition it is pointing to.  Is it the partition on the 2TB drive?

---

### Post by satimis on 2023-04-04
> **yancek said:**
> Are both install of Ubuntu 22.04 on the 1TB and 2TB drives UEFI installs?  
Thanks for your advice.

Sorry I couldn't recall. This PC has been running for 4~5 years. Is there any way to check?

1TB drive was installed first.  Later I added 2TB drive to replace it because insufficient space.  Both drives worked without problem.  Most the time I run the 2TB drive and the 1TB drive is standing idle.  Until 2 days before I started the 1TB drive for testing to install my old Epson 3490 Photo scanner and found this problem.

> 
Were both drives attached during both installs? 
No.  Usually I only connect 1 drive for new installation to avoid making mistake to erase the drive accidentally.

> 
Do you have an EFI partition on both drives?  If you have an EFI partition on both drives, mount it and check the grub.cfg file on it for the UUID then run the blkid command to find which partition it is pointing to.  Is it the partition on the 2TB drive?
I couldn't recall exactly.  Usually I use the complete drive without partition.

Attach to this posting is the fdisk.txt running;```

$ sudo fdisk -l > fdisk.txt

```

Thanks

Regards

---

### Post by MAFoElffen on 2023-04-04
Please. Let's not get distracted, and get back on track... onto things that will help with this error, and help this User. 

This error is the display saying it needs to be set into a mode that it supports (natively). This, with other screens is like when it says "Out of Frequency." This is happening in the early stages of the Kernel boot, before the Linux Graphics Layer initializes fully (before the graphics drivers in the Desktop). The way to handle this is to set KMS in the kernel by giving KMS helpers via Kernel boot parameters using Grub command line arguments.

If you ran and submitted the [UbuntuForum's 'system-info' script]("https://github.com/UbuntuForums/system-info"), it would show us all the information we would need to come up with a recommendation... All you would have to do it to post the URL of where the report uploaded to a Pastebin. This is why that report exists. As a tool to help Users asking for help here to get sound recommendations for solutions from members here. (But a tool is only helpful if it is used.)

Alternatively, let's cut to the chase... When you are at the Graphical Login screen (GDM), when you get to the Password panel, select the gear icon in the lower right, and select Xorg... Why Xorg? Because xrandr (an XSession tool) needs to run natively in an X11 session to be able to query the display...

Open a terminal session and post the output of these commands, wrapped within CODE Tags.
```

xrandr -q
grep 'GRUB_CMDLINE_LINUX_DEFAULT' /etc/default/grub
sudo lshw -c display | grep 'product\|vendor'

```
The first command will query the display, and return the resolutions and frequencies that it can do. The second command will return the current Grub2 command line setting. The third command will return the information we will need to know what video hardware you have in your computer.

With that information we can recommend what you need to add to your Grub2 command line to set your video into a mode that your display is happy with (in the Splash and Login screen), until the graphics drivers initialize and take over (in the Desktop).

Sound like a plan?

---

### Post by satimis on 2023-04-04
> **MAFoElffen said:**
> Please. Let's not get distracted, and get back on track... onto things that will help with this error, and help this User. 

This error is the display saying it needs to be set into a mode that it supports (natively). This, with other screens is like when it says "Out of Frequency." This is happening in the early stages of the Kernel boot, before the Linux Graphics Layer initializes fully (before the graphics drivers in the Desktop). The way to handle this is to set KMS in the kernel by giving KMS helpers via Kernel boot parameters using Grub command line arguments.

If you ran and submitted the [UbuntuForum's 'system-info' script]("https://github.com/UbuntuForums/system-info"), it would show us all the information we would need to come up with a recommendation... All you would have to do it to post the URL of where the report uploaded to a Pastebin. This is why that report exists. As a tool to help Users asking for help here to get sound recommendations for solutions from members here. (But a tool is only helpful if it is used.)

Alternatively, let's cut to the chase... When you are at the Graphical Login screen (GDM), when you get to the Password panel, select the gear icon in the lower right, and select Xorg... Why Xorg? Because xrandr (an XSession tool) needs to run natively in an X11 session to be able to query the display...

Open a terminal session and post the output of these commands, wrapped within CODE Tags.
```

xrandr -q
grep 'GRUB_CMDLINE_LINUX_DEFAULT' /etc/default/grub
sudo lshw -c display | grep 'product\|vendor'

```
The first command will query the display, and return the resolutions and frequencies that it can do. The second command will return the current Grub2 command line setting. The third command will return the information we will need to know what video hardware you have in your computer.

With that information we can recommend what you need to add to your Grub2 command line to set your video into a mode that your display is happy with (in the Splash and Login screen), until the graphics drivers initialize and take over (in the Desktop).

Sound like a plan?
Thanks for your advice.

$ xrandr -q > xrandr.txt
xrandr.txt attached

$ grep 'GRUB_CMDLINE_LINUX_DEFAULT' /etc/default/grub```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

$ sudo lshw -c display | grep 'product\|vendor'```

       product: Picasso/Raven 2 [Radeon Vega Series / Radeon Vega Mobile Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]

```

---

### Post by MAFoElffen on 2023-04-04
Open Grub default file with elevated privileges:
```

sudo nano /etc/default/grub

```
Change this line to include the new boot parameter:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

```
Save and exit ( <Cntrl><O>, then <Cntrl><X> )

Update the changes in Grub
```

sudo update-grub
sudo reboot

```

---

### Post by satimis on 2023-04-05
> **MAFoElffen said:**
> Open Grub default file with elevated privileges:
```

sudo nano /etc/default/grub

```
Change this line to include the new boot parameter:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

```
Save and exit ( <Cntrl><O>, then <Cntrl><X> )

Update the changes in Grub
```

sudo update-grub
sudo reboot

```
Performed steps as advised.

$ sudo nano /etc/default/grub
change the line;```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to;
```
GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"
```
save and exit

$ sudo update-grub```

Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-38-generic
Found initrd image: /boot/initrd.img-5.19.0-38-generic
Found linux image: /boot/vmlinuz-5.19.0-35-generic
Found initrd image: /boot/initrd.img-5.19.0-35-generic
Found linux image: /boot/vmlinuz-5.15.0-60-generic
Found initrd image: /boot/initrd.img-5.15.0-60-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
```

$ sudo reboot

Problem still remands.  The warning still popup and I have to wait before popup the login page.

What I recall after the problem occurred is the change of color on some icons on Ubuntu 22.04 desktop after login.

Before problem occurred
(pls refer to screenshot_ubuntu_before_problem.png)
(remark the screenshot captured on an Ubuntu 22.04 VM desktop)

After problem started
(pls refers to screenshot_ubuntu_after_problem60.png)
Some icons changed in color on the desktop.  If I recall correct, it happened after running;
```

sudo apt update ; sudo apt upgrade

```

Regards

---

### Post by MAFoElffen on 2023-04-05
That is strange...

Let's see what it sees from Grub. This might sound a bit tricky.

Get to the Grub2 boot menu. Press <C> to get to Grub commandline. Do this command:
```

videoinfo

```
Take a picture with your smartphone, email it to yourself. Then upload it as an attachment.

For the boot parameter, use one of the resolution shown there, in this format:
```

video=WidthxWidth-color_depth
# For example
video=1920x1080-32

```

---

### Post by satimis on 2023-04-05
> **MAFoElffen said:**
> That is strange...

Let's see what it sees from Grub. This might sound a bit tricky.

Get to the Grub2 boot menu. Press <C> to get to Grub commandline. Do this command:
```

videoinfo

```
Take a picture with your smartphone, email it to yourself. Then upload it as an attachment.

For the boot parameter, use one of the resolution shown there, in this format:
```

video=WidthxWidth-color_depth
# For example
video=1920x1080-32

```
On my MicroSoft keyboard
Press <C> -> no response

I have to start Terminal on its icon on Desktop

$ videoinfo```

videoinfo: command not found

```

$ apt policy videoinfo```

N: Unable to locate package videoinfo

```
It is not on repo

Videoinfo: command not found
[https://itsfoss.community/t/videoinfo-command-not-found/8503](https://itsfoss.community/t/videoinfo-command-not-found/8503)
```
..... videoinfo is a command that can be run in the Grub command console, it’s not available as ‘regular’ software that can be installed from within Linux.

```

Unable to perform your suggested test

$ lspci > lspci.txt
lspci.txt is attached

Regards

---

### Post by ajgreeny on 2023-04-05
You were not asked to open a terminal in which to use the **c** command or the **videoinfo** command either but to hit **c** whilst the grub menu was showing.

That will put you into the grub command line system, not the Ubuntu command line; this is very important and once in that use the videoinfo command.

Please do what is asked of you and if you don't understand ask us or we will continue to go nowhere fast!

---

### Post by satimis on 2023-04-05
> **ajgreeny said:**
> You were not asked to open a terminal in which to use the **c** command or the **videoinfo** command either but to hit **c** whilst the grub menu was showing.

That will put you into the grub command line system, not the Ubuntu command line; this is very important and once in that use the videoinfo command.

Please do what is asked of you and if you don't understand ask us or we will continue to go nowhere fast!

Whether once PC restarts, press Shift plus "C" while loading Ubuntu GRUB, and get GRUB bootloader menu screen (an example) as the screenshot attached.

---

### Post by ajgreeny on 2023-04-05
Yes, when you see that grub menu as shown in your attached image just hit **c**.

It doesn't have to be an upper case c, and you will be taken to a GRUB command line in which you then use the **videoinfo** command..

---

### Post by satimis on 2023-04-05
> **ajgreeny said:**
> Yes, when you see that grub menu as shown in your attached image just hit **c**.

It doesn't have to be an upper case c, and you will be taken to a GRUB command line in which you then use the **videoinfo** command..
Perform following steps;

1.  Reboot PC
2.  Grub command line screen won't start.  It boots straight to Ubuntu 22.04 login page.

I have tried 3 times with the same result.

Regards

[COLOR="#FF0000"]Edit
===[/COLOR]
screenshot - PC BIOS screen
no F8 key on Microsoft keyboard

---

### Post by yancek on 2023-04-05
The image in your last post appears to be the BIOS screen.  Do you have Grub installed to boot your systems?  Do you not see the Grub menu when booting?  That is where you hit the c key then Enter key to run the commands suggested above..

---

### Post by MAFoElffen on 2023-04-05
In Linux, there are several ways to kill a cat... LOL

In the attached pictures, this was what I was explaining. Attachment one is the Grub2 menu, if at that , if you press the <Down-Arrow> once, it will lock the menu from going away. It stops the timers. If you look at the instructions at the bottom it says that if you press the <C> key, it will go into a (Grub) Command Line Mode. If you press the <E> key, it will go into an Edit Mode...

If for some unknown reason, your computer cannot drop into the command line mode from there by pressing the <C> key, then go ahead and press the <E> key to get into Edit Mode... From there, press either <Cntrl><C> or the <F2> key, and it will go into the Command Line mode from the editor.

Attachment 2 is when it initially drops down into the Command Line Mode...

Attachment 3 is typing in "videoinfo" at the Command Line prompt.

Attachment 4 is the output it returns.

---

### Post by satimis on 2023-04-05
> **yancek said:**
> The image in your last post appears to be the BIOS screen.

Yes

> 
Do you have Grub installed to boot your systems?  

$ apt policy grub-emu
```

grub-emu:
  Installed: (none)
  Candidate: 2.06-2ubuntu7.1
  Version table:
     2.06-2ubuntu7.1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
     2.06-2ubuntu7 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
Whether you meant this application?

> 
Do you not see the Grub menu when booting?  That is where you hit the c key then Enter key to run the commands suggested above..
No

Regards

---

### Post by MAFoElffen on 2023-04-05
Then do this to force the Grub2 Menu to show when booting...
```

sudo nano /etc/default/grub

```
When the nano editor starts make these edits...
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
GRUB_RECORDFAIL_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]-- splash video=1920x1080-32@60[/COLOR]"
GRUB_CMDLINE_LINUX=""

GRUB_GFXMODE=[COLOR=#ff0000]1920x1080[/COLOR]  ## <-- Uncomment this line and change to this...

```
Save and exit. Then do
```

sudo update-grub

```

---

### Post by satimis on 2023-04-05
> **MAFoElffen said:**
> Then do this to force the Grub2 Menu to show when booting...
```

sudo nano /etc/default/grub

```
When the nano editor starts make these edits...
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
GRUB_RECORDFAIL_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]-- splash video=1920x1080-32@60[/COLOR]"
GRUB_CMDLINE_LINUX=""

GRUB_GFXMODE=[COLOR=#ff0000]1920x1080[/COLOR]  ## <-- Uncomment this line and change to this...

```
Save and exit. Then do
```

sudo update-grub

```
Edit /etc/default/grub as advised.

$ sudo update-grub```

Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-38-generic
Found initrd image: /boot/initrd.img-5.19.0-38-generic
Found linux image: /boot/vmlinuz-5.19.0-35-generic
Found initrd image: /boot/initrd.img-5.19.0-35-generic
Found linux image: /boot/vmlinuz-5.15.0-60-generic
Found initrd image: /boot/initrd.img-5.15.0-60-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
```

$ reboot

Grub starts -> press "c"

Take photos with smart phone.

Photos are attached here

---

### Post by MAFoElffen on 2023-04-05
Change these two line in /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=[COLOR=#ff0000]3840x2160[/COLOR]-32@60"

GRUB_GFXMODE=[COLOR=#ff0000]3840x2160[/COLOR] 

```
Which, just by coincidence, is the same mode that your Dell display says it is looking for.

Remember to save, & exit the file... Then run 'sudo update-grub' to pick up the changes. (just like the instructions from my last post.)

---

### Post by satimis on 2023-04-05
> **MAFoElffen said:**
> Change these two line in /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=[COLOR=#ff0000]3840x2160[/COLOR]-32@60"

GRUB_GFXMODE=[COLOR=#ff0000]3840x2160[/COLOR] 

```
Which, just by coincidence, is the same mode that your Dell display says it is looking for.

Remember to save, & exit the file... Then run 'sudo update-grub' to pick up the changes. (just like the instructions from my last post.)
Just for your information;
GRUB menu screen is NOT always popup.  

Edit /etc/default/grub as advised.

$ sudo update-grub```

Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-38-generic
Found initrd image: /boot/initrd.img-5.19.0-38-generic
Found linux image: /boot/vmlinuz-5.19.0-35-generic
Found initrd image: /boot/initrd.img-5.19.0-35-generic
Found linux image: /boot/vmlinuz-5.15.0-60-generic
Found initrd image: /boot/initrd.img-5.15.0-60-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
```

Reboot
This time grub menu screen popup after that warning (it is still there)

Reboot the second time.  GRUB menu screen doesn't start.  It boots straight to Ubuntu 22.04 login screen after that warning,

---

### Post by MAFoElffen on 2023-04-06
From one of you other threads... Unistall Grub-Customizer so that the changes can take affect...

---

### Post by satimis on 2023-04-06
> **MAFoElffen said:**
> From one of you other threads... Unistall Grub-Customizer so that the changes can take affect...
I haven't installed Grub-Customizer before, except following your instruction on this thread.  I think it would be better sticking to the problem on this thread first and pending to solve the problem of unable to start 1TB PCIe SSD on another thread until the problem on this thread solved.

I have noticed following problem;
Today when I started the PC the first time, Grub Menu screen started without the warning.  After a while it popup Ubuntu 22.04 login desktop. On rebooting the warning popup but the Grub Menu screen unable to start.  After a while the Ubuntu login screen started.

I have tried rebooting several times but unable to start Grub Menu screen.  The warning popup a while then Ubuntu login desktop started.  I also tried turning off the PC and restarted it.  The aforesaid problem still remains.

Regards

---

### Post by MAFoElffen on 2023-04-06
Please do this
```

grep . /proc/cmdline

```
That will show me what is being passed and the command line Linux was booted with...

---

### Post by satimis on 2023-04-06
> **MAFoElffen said:**
> Please do this
```

grep . /proc/cmdline

```
That will show me what is being passed and the command line Linux was booted with...
$ grep . /proc/cmdline```

BOOT_IMAGE=/boot/vmlinuz-5.19.0-38-generic root=/dev/mapper/vgubuntu-root ro -- splash video=3840x2160-32@60 vt.handoff=7

```

Thanks

---

### Post by MAFoElffen on 2023-04-06
Thank you very much! Congratulations on posting with CODE tags. That is a lot easier and faster to read.

I can see that it is being passed by Grub to the kernel. Now we just have to figure out why it is still getting that error. 

Are the boot messages now look like they are in that resolution as they scroll by? And the Splash Screen? 

That "is" the resolution that the Dell Display says it wants (from the picture of the error in Post #1). That is the mode that 'videoinfo' says that it recognizes as the preferred mode...

---

### Post by MAFoElffen on 2023-04-06
Now change the /etc/default/grub file to this change:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash [COLOR=#ff0000]video=3840x2160-32[/COLOR]"

```
Remember to run 'sudo update-grub' to pick up the change...

---

### Post by satimis on 2023-04-06
> **MAFoElffen said:**
> Thank you very much! Congratulations on posting with CODE tags. That is a lot easier and faster to read.

I can see that it is being passed by Grub to the kernel. Now we just have to figure out why it is still getting that error. 

Are the boot messages now look like they are in that resolution as they scroll by? And the Splash Screen? 

That "is" the resolution that the Dell Display says it wants (from the picture of the error in Post #1). That is the mode that 'videoinfo' says that it recognizes as the preferred mode...
This Ubuntu 22.04 seems unstable.

The warning still starts -> then after a while it popup to Ubuntu login page

If the warning doesn't start -> start BIOS asking whether to press DEL....-> after a while it popup GRUB menu page -> then to Ubuntu login page

It seems out of my control.  I don't know when they'll happen
[B][COLOR="#FF0000"]
Just discovered;[/COLOR][/B]
Gimp installed on Gimp AppImage
and
OpenShot installed on OpenShot AppImage

both unable to start clicking their icons.

I have deleted Gimp AppImage and installed Gimp on repo but still unable to start it clicking its icon.  I have to start GIMP on Terminal running```

$ gimp

```

I have no idea how these problem come.  I don't run GIMP and OpenShot daily. 

Regards

---

### Post by satimis on 2023-04-06
> **MAFoElffen said:**
> Now change the /etc/default/grub file to this change:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash [COLOR=#ff0000]video=3840x2160-32[/COLOR]"

```
Remember to run 'sudo update-grub' to pick up the change...
Change GRUB as advised.

$ sudo update-grub```

Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-38-generic
Found initrd image: /boot/initrd.img-5.19.0-38-generic
Found linux image: /boot/vmlinuz-5.19.0-35-generic
Found initrd image: /boot/initrd.img-5.19.0-35-generic
Found linux image: /boot/vmlinuz-5.15.0-60-generic
Found initrd image: /boot/initrd.img-5.15.0-60-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done

```

Reboot

The warning still starts -> then to Ubuntu login page.

No GRUB menu page starts

---

### Post by MAFoElffen on 2023-04-07
> **satimis said:**
> The warning still starts -> then to Ubuntu login page.

No GRUB menu page starts
Please post the contents of "your" /etc/default/grub file within CODE Tags...

Something is not right, that is is not respecting what is there.

---

### Post by satimis on 2023-04-07
> **MAFoElffen said:**
> Please post the contents of "your" /etc/default/grub file within CODE Tags...

Something is not right, that is is not respecting what is there.
$ cat /etc/default/grub | grep GRUB```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
# GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=3840x2160-32"
GRUB_CMDLINE_LINUX=""
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
#GRUB_TERMINAL=console
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=3840x2160
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
#GRUB_DISABLE_RECOVERY="true"
#GRUB_INIT_TUNE="480 440 1"

```

Thanks

Regards

---

### Post by MAFoElffen on 2023-04-08
I don't see a rhyme or reason why it isn't respecting changes to your KMS settings. It is saying that it booted with that command line parameter. I think we should pause this until your "Won't boot from SSD" thread is resolved, and then continue with this then.

That way we are making changes to one thing at a time, instead of from different angles at the same time.

---

