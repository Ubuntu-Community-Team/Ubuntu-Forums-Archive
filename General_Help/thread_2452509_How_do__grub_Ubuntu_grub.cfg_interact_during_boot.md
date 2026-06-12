---
title: "How do  grub/ Ubuntu/ grub.cfg interact during boot ?"
date: 2020-10-23
forum: General Help
---

### Post by helen314 on 2020-10-23
Please help me understand the relationship of files run during boot process. 
I do have SOME notion how each INDIVIDUAL file is configured and how it works.
I do not need references to manuals. 

One of the "issues" is -  how do you configure "grub2"  - most tutorials are for plain "grub".



I am trying to implement a simple change in "grub". 


```

# GRUB_DEFAULT=3
# use last menu selection
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
 
 
 

```

That did not work, so I did change the "timeout"  to verify my method.


```

GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5[/SIZE]
 


```


No go, the timeout actually changed to what appears some kind of default - 30 seconds.
[COLOR=#ff0000]**I must be changing wrong  /etc/default/grub - how do I verify  this? **[/COLOR]


[FONT=arial]PS 
I do run  
[/FONT]
[FONT=arial]update-grub after I make changes in /etc/default/grub  [/FONT]
[FONT=arial]and I see the changes 
 [/FONT]

 
 
 
 Ubuntu 16.04.7

---

### Post by oldfred on 2020-10-23
There is the manual and online resources.
[https://www.gnu.org/software/grub/index.html](https://www.gnu.org/software/grub/index.html)
When I click on this in my new Firefox, it does not open, but just downloads it.
Manual 2.04
[https://www.gnu.org/software/grub/manual/grub/grub.pdf](https://www.gnu.org/software/grub/manual/grub/grub.pdf)

What are you trying to do.
In one case  you are changing default boot order.
And in other changing timeout.

I tend to turn off a lot of grub and use 40_custom for my boot entries.

Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)
Stop 30_custom from resetting timeout & style
[https://gist.github.com/LeahCim/9332432](https://gist.github.com/LeahCim/9332432)
Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by grahammechanical on 2020-10-23
As far as Ubuntu is concerned there is little difference between Grub and Grub2. Ubuntu used to use Grub 1.99 and then slowly switched over to Grub2 which was labelled as beta code for several releases. You will find duplicate files in Grub and Grub2 folders.

update-grub is a Ubuntu shell script that runs grub-mkconfig. We find it at /usr/sbin/update-grub

This is what the script reads on my machine

> #!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

It is exactly the same as the update-grub2 script. There is even a script called upgrade-from-grub-legacy. We find grub-mkconfig at /usr/sbin/grub-mkconfig. In the same folder there is grub-install which is a program not a script. In my notes from past attempts at getting a Ubuntu education I have written this: "grub-install copies Grub images into /boot/grub, and uses grub-setup to install Grub into the boot sector."

I have a BIOS motherboard so I do not know of the changes (if any) made to install Grub on a UEFI motherboard. I know about boot partition and efi partition. The ability to install Grub code/images into either a boot partition (MBR) or an efi boot partition must come from how  grub-install is programed

Regards

---

### Post by helen314 on 2020-10-23
> **grahammechanical said:**
> As far as Ubuntu is concerned** there is little difference between Grub and Grub2**. Ubuntu used to use Grub 1.99 and then slowly switched over to Grub2 which was labelled as beta code for several releases. You will find duplicate files in Grub and Grub2 folders.

If you do not mind ,  let' settle this first. 

[B] there is little difference between Grub and Grub2

1. there is - [/B]/etc/default/grub exists  but  there is NO /etc/default/grub2
 
a@a-desktop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
#  temorary from default = 0 

GRUB_DEFAULT=3  

#GRUB_DEFAULT=saved         # use last menu 
#GRUB_SAVEDEFAULT=true      # save as default 
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#####GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=text   ###  640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


a@a-desktop:~$ cat /etc/default/grub2
cat: /etc/default/grub2: No such file or directory
a@a-desktop:~$ 

2. /etc/default/grub entries are used by   /boot/grub/grub.cfg





update-grub is a Ubuntu shell script that runs grub-mkconfig. We find it at /usr/sbin/update-grub

This is what the script reads on my machine



It is exactly the same as the update-grub2 script. There is even a script called upgrade-from-grub-legacy. We find grub-mkconfig at /usr/sbin/grub-mkconfig. In the same folder there is grub-install which is a program not a script. In my notes from past attempts at getting a Ubuntu education I have written this: "grub-install copies Grub images into /boot/grub, and uses grub-setup to install Grub into the boot sector."

I have a BIOS motherboard so I do not know of the changes (if any) made to install Grub on a UEFI motherboard. I know about boot partition and efi partition. The ability to install Grub code/images into either a boot partition (MBR) or an efi boot partition must come from how  grub-install is programed

Regards

To follow-up  on original post 

The objective is to VERIFY that changing /etc/default/grub  indeed changes "Ubuntu"  file during boot. . 
I picked TWO options and neither one resulted in expected changes in boot process. 

The "question" is not WHAT options I used and why , but WHY it did not work. 
Simply repeated - I set the timeout to 5 seconds and my boot file runs "timeout of 30  seconds" 

Therefore the question is - WHERE is timeout of 30 second set - it is NOT in  /etc/default/grub.

In order to make an intelligent  guess, I should know THE SEQUENCE of boot process files execution. 

Unfortunately I have not discover HOW  grub, grub.cfg, UEFI etc interact - HENCE I ASKED. 
From past - this reply is pretty much in line with others - "I have no UEFI, so I dont not know..." is pretty much norm here.

Hopefully my expectations from this forum are not to high,

however, is it too much to ask to read the original post before answering  / posting replies?
If so - I have no choise but to repeat - **please no more references to manuals**.

---

### Post by jeremy31 on 2020-10-23
It must be set in one of the scripts in /etc/grub.d/ as there are some conditions that will cause a 30 second wait

---

### Post by grahammechanical on 2020-10-23
> Hopefully my expectations from this forum are not to high,

If I tell you the answer your expectation might increase. That would lead to further disappointment. The answer is on page 18 of the Grub 2 manual under GRUB_TIMEOUT.

> &#8216;GRUB_TIMEOUT&#8217;
Boot the default entry this many seconds after the menu is displayed, unless a key is pressed. The default is &#8216;5&#8217;. Set to &#8216;0&#8217; to boot immediately without displaying the menu, or to &#8216;-1&#8217; to wait indefinitely.

I will not be replying to any further posts from you.

---

### Post by helen314 on 2020-10-23
> **jeremy31 said:**
> It must be set in one of the scripts in /etc/grub.d/ as there are some conditions that will cause a 30 second wait

Yes, it "could" be in one of those scripts, BUT -  since everybody likes manuals here  - it is an option mentioned  in "grub"  manual. 
Unless these "helper scripts" are overriding the grub  setting.
Looks as  there are about  half a dozen of them. I'll check them. 

I am currently trying to answer myself  - how does UEFI  and grub relate.

---

### Post by oldfred on 2020-10-23
If you do not want to read the manual, you can read the output of the sudo update-grub or your grub.cfg.
it is built from all the scripts which you do not normally edit and the settings that you normally can change in /etc/default/grub configuration file. 

On mine it is line 106, may vary based on version or settings:

```
if [ "${recordfail}" = 1 ] ; then
  set timeout=30

```
That says if grub has any issues recordfail then it defaults to 30 seconds.

And if you really want to understand grub, this now very long thread deals with many issues and how grub works.
Posted above, but obviously not reviewed.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)

[https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)
[https://superuser.com/questions/496026/what-is-the-difference-in-boot-with-bios-and-boot-with-uefi](https://superuser.com/questions/496026/what-is-the-difference-in-boot-with-bios-and-boot-with-uefi)
[URL="https://www.zdnet.com/article/linux-on-your-laptop-heres-what-you-need-to-know-about-uefi-firmware/"]https://www.zdnet.com/article/linux-on-your-laptop-heres-what-you-need-to-know-about-uefi-firmware/
[/URL]
>  GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

1. /etc/default/grub - the file containing GRUB 2 menu settings.
2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.



Original grub or now grub legacy used menu.lst for all of above in major sections. And you directly edited it, often leading to errors in booting.

---

### Post by helen314 on 2020-10-24
> **oldfred said:**
> If you do not want to read the manual, you can read the output of the sudo update-grub or your grub.cfg.
it is built from all the scripts which you do not normally edit and the settings that you normally can change in /etc/default/grub configuration file. 

On mine it is line 106, may vary based on version or settings:

```
if [ "${recordfail}" = 1 ] ; then
  set timeout=30

```




That says if grub has any issues recordfail then it defaults to 30 seconds.

And if you really want to understand grub, this now very long thread deals with many issues and how grub works.
Posted above, but obviously not reviewed.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)

[https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)
[https://superuser.com/questions/496026/what-is-the-difference-in-boot-with-bios-and-boot-with-uefi](https://superuser.com/questions/496026/what-is-the-difference-in-boot-with-bios-and-boot-with-uefi)
[URL="https://www.zdnet.com/article/linux-on-your-laptop-heres-what-you-need-to-know-about-uefi-firmware/"]https://www.zdnet.com/article/linux-on-your-laptop-heres-what-you-need-to-know-about-uefi-firmware/
[/URL]


Original grub or now grub legacy used menu.lst for all of above in major sections. And you directly edited it, often leading to errors in booting.

I guess you and I have "failure to communicate " .  You keep making refernces AFTER I asked not to.
I am not sure why you cannot follow such simple request.


**Let me ask AGAIN and hopefully YOU will finally answer such simple question.**

Per your favorite , GNU grub manual, the timeout is  set in "grub" .

[B]Please - just say YES or NO. 


If you manage that, MAYBE  you and I can finally find out WHY my timeout is 30 seconds by analyzing OTHER files.
[/B]
AND in the process answering  my original post too.** Re: How do  grub/ Ubuntu/ grub.cfg interact during boot ?-**
That would be very nice and productive since I have not  found a "manual"  on that - hence I posted my question here.

Here is what I know so far 

1. During Ubuntu ISO install use GPT partition 
2. Install will create EFI boot partition etc.
3. UEFI firmware reads  such EFI partition 

??????????????????


```


a@a-desktop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
#  temporary from default = 0 

GRUB_DEFAULT=3  

#GRUB_DEFAULT=saved         # use last menu 
#GRUB_SAVEDEFAULT=true      # save as default 
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=5**
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#####GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=text   ###  640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
a@a-desktop:~$ 


```

---

### Post by oldfred on 2020-10-24
I have this in my old notes:
Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 
And one user a long time ago posted this:
Solved by editing the grub file. GRUB_HIDDEN_TIMEOUT_QUIET was =true. Setting it to =false gave me the boot options at startup and can now freely boot into windows or ubuntu. 

My grub.cfg, I typically run a small script to edit it with a new install to my preferred settings.
And timeout is 3 seconds, I have to be quick if I want to change to a different grub entry.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/default/grub [/COLOR]
# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. 
# For full documentation of the options in this file, see: 
#   info -f grub -n 'Simple configuration' 

GRUB_DEFAULT=0 
GRUB_TIMEOUT_STYLE=menu 
GRUB_TIMEOUT=3 
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth" 
GRUB_CMDLINE_LINUX="" 

# Uncomment to enable BadRAM filtering, modify to suit your needs 
# This works with Linux (no patch required) and with any kernel that obtains 
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) 
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef" 

# Uncomment to disable graphical terminal (grub-pc only) 
#GRUB_TERMINAL=console 

# The resolution used on graphical terminal 
# note that you can use only modes which your graphic card supports via VBE 
# you can see them in real GRUB with the command `vbeinfo' 
#GRUB_GFXMODE=640x480 

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
#GRUB_DISABLE_LINUX_UUID=true 

# Uncomment to disable generation of recovery mode menu entries 
#GRUB_DISABLE_RECOVERY="true" 

# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1" 
GRUB_DISABLE_OS_PROBER=true 
GRUB_DISTRIBUTOR=kubuntu

[/FONT]
```

With old BIOS, system powered on and read the code on the chip. Your basic choices were to choose a hard drive (if newer BIOS and drives with cable select) or jumper pins to choose which drive.
With UEFI, you have both old BIOS as CSM and newer UEFI. It has more graphics and choices, but still loads from EEROM and using choices you have selected loads boot files from the ESP. You can have on each drive an ESP, so it uses the GUID of the partition to know which ESP to use. And then find file to load. That is end of UEFI and start of grub2 or any other boot loader you may use.

I have set in UEFI to boot entry 0002 as default. Using the GUID/partUUID to find shimx64.efi
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for fred:  
BootCurrent: 0002 
Timeout: 1 seconds 
BootOrder: 0002,0000,0012,0013,0014,0005,0010,0001 
Boot0000* ubuntu        HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0xff1b9)/File(\EFI\UBUNTU\SHIMX64.EFI) 
Boot0001* bionic_18_04  VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb) 
Boot0002* focal HD(1,GPT,[COLOR=#ff0000]c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1[/COLOR],0x800,0x100000)/File(\EFI\FOCAL\SHIMX64.EFI) 
B
[/FONT]
```

```
[FONT=monospace][COLOR=#000000]nvme0n1                          465.8G                                              [/COLOR]
&#9500;&#9472;nvme0n1p1 /boot/efi  ESP_NVME    512M vfat   4954-C122                            [COLOR=#ff0000]c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1[/COLOR] 
&#9500;&#9472;nvme0n1p2            focal_0    29.3G ext4   b913e1bc-6f08-4984-b653-9a604d95470a 043d0f2a-48f1-4bcd-8d8b-df02a242436c 
&#9500;&#9472;nvme0n1p3 /          focal_k    29.3G ext4   [COLOR=#00ff00]54029c4f-0cbe-413e-80ce-78a4995b0551[/COLOR] c4d96c9e-eebb-43e6-b1b0-7ece2306cfee 
&#9500;&#9472;nvme0n1p4                       29.3G ext4   dd5925b4-0250-4f6d-b59e-165f85365721 a4d9289a-6beb-4e64-b11e-65aba5ddb884 
&#9492;&#9472;nvme0n1p5 /mnt/data  nvme_data 195.3G ext4   1a44f4af-6780-4bbd-ad0b-6385ed30830b dfd49ef3-46a6-4cad-8f64-7b1696fba6fb

[/FONT][FONT=monospace]
[/FONT]
```

Shimx64.efi requires /EFI/ubuntu/grub.cfg which is a configfile into the full grub.cfg in your install.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo cat /boot/efi/EFI/ubuntu/grub.cfg [/COLOR]
search.fs_uuid [COLOR=#00ff00]54029c4f-0cbe-413e-80ce-78a4995b0551[/COLOR] root  
set prefix=($root)'/boot/grub' 
configfile $prefix/grub.cfg[/FONT]
```

And that finds my full grub.cfg in my Ubuntu install.

---

### Post by helen314 on 2020-10-24
[CODE]
if [ "${recordfail}" = 1 ] ; then
  set timeout=5                           ** generated AFTER** **changes in grub implemented** 
{/CODE]

recordfail is ALWAYS set to 1  by a function in one of the "helper scripts".
From other discussions the purpose of "recordfail" is unclear , but not important to this discussion. 

Even when bypassed by setting GRUB_RECORDFAIL_TIMEOUT=5 in " default /grub" the grub boot menu STILL times out in 30 seconds.

 
The simple conclusion - it has to be modified somewhere else. Still looking for the source. 

BTW - the GRUB_DEFAULT=3   shows up in grub.cfg , however item  #3 is NOT selected in grub menu - issue #2

---

### Post by oldfred on 2020-10-24
Start with default grub config file and change only one line at a time.
Some defaults are set in the scripts in /etc/grub.d, normally not edited.

Remove entries that are not standard in new default like.
Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.

How are you counting? Grub starts at 0, so first entry is 0 not 1. Not Like floors in Europe.

---

### Post by dragonfly41 on 2020-10-24
When I investigate such issues I often turn to ripgrep to explore various directories for file content
First install ripgrep if not already installed

sudo apt install rg

Let us look for the pattern TIMEOUT=

[https://blog.burntsushi.net/ripgrep/](https://blog.burntsushi.net/ripgrep/)

TIMEOUT=

rg -i TIMEOUT=  /etc/default  | grep grub

rg -i TIMEOUT=  /boot | grep grub

I see returns such as ..

[FONT=monospace][COLOR=#000000]/boot/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000].cfg:  set timeout=30[/COLOR]
/boot/[COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000].cfg:    set timeout=10[/COLOR]
/boot/[COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000].cfg:    set timeout=0[/COLOR]
/boot/[COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000].cfg:  set timeout=10

[/COLOR]In fact I use rEFInd ..



[/FONT]

---

### Post by Impavidus on 2020-10-24
The error that causes grub to switch to a 30 second default instead of the normal 5 second (or whatever you set it to be in /etc/grub/default – yes, that's the right place to set it), is an error occuring during boot, not when updating grub. Sometimes, without updating grub, I see it fall back to a 30 second timeout and the next time, still without updating grub, it's back to 3 seconds. It has become more common as my computer gets older, but otherwise it's still fine, so I keep using it. At the same time, grub doesn't set the high display resolution. I guess that on your system grub has some difficulty finding the things it needs at boot time. For possible causes I would have to read the manual and quote the relevant passages for your, but I won't do that.

---

### Post by helen314 on 2020-10-24
So back to my original post. 

I have learned that  UEFI boot process involves 
[FONT=monospace][COLOR=#000000] efibootmgr


I am still  looking for connection between grub / grub.cfg and efibootmgr .

This is how mine [/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000] efibootmgr [/COLOR][/FONT]looks currently 



```


BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0007,0011,0006,0004,0008,0009,000A,000B,000C,000D,000E,000F,0010
Boot0000* ubuntu    HD(2,GPT,44c98307-eb14-4cd8-ab7e-3138193729a1,0x100800,0x100800)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* USB     BBS(USB,,0x0)..GO..NO........].e.M. .B.a.y. .R.e.a.d.e.r. .1...0.0....................A...................................$..Gd-.;.A..MQ..L.9.2.0.3.1.1.1........BO..NO........e.e.M. .B.a.y. .R.e.a.d.e.r. .1...0.1....................A...........................................$..Gd-.;.A..MQ..L.9.2.0.3.1.1.1........BO..NO........e.e.M. .B.a.y. .R.e.a.d.e.r. .1...0.2....................A...........................................$..Gd-.;.A..MQ..L.9.2.0.3.1.1.1........BO..NO........i.S.e.a.g.a.t.e. .B.U.P. .U.l.t.r.a. .T.o.u.c.h. .0.0.0.4....................A.............................6..Gd-.;.A..MQ..L.0.0.0.0.0.0.0.0.N.A.B.1.3.3.H.H........BO..NO{.......Y.S.e.a.g.a.t.e....................A.............................&..Gd-.;.A..MQ..L.N.A.8.3.3.B.D.C........BO..NO........e.e.M. .B.a.y. .R.e.a.d.e.r. .1...0.3....................A...........................................$..Gd-.;.A..MQ..L.9.2.0.3.1.1.1........BO
Boot0006* Hard Drive     BBS(HD,,0x0)..GO..NO........u.W.D.C. .W.D.5.0.0.0.A.A.K.X.-.0.0.E.R.M.A.0....................A.................................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.2.C.W.E.4.9.5.7.9.3........BO..NO........o.W.D.C. .W.D.5.0.0.0.B.E.V.T.-.6.0.Z.A.T.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.X.W.Y.N.8.0.C.K.5.M.9.1........BO..NO........o.W.D.C. .W.D.5.0.0.0.A.A.K.S.-.7.5.V.0.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.W.A.8.F.5.3.6.8.8.8........BO..NO........u.S.T.3.3.2.0.4.1.8.A.S....................A.................................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .V.6.P.M.D.L.P.Z........BO
Boot0007* ubuntu    HD(1,GPT,db6b86b5-a4cc-4395-a80a-f2a4e652586a,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)..BO
Boot0008* UEFI: Seagate BUP Ultra Touch 0004    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(3,0)/HD(1,GPT,7149cebc-a872-4fa7-bf45-e75ea1672895,0xffff,0xefff1)..BO
Boot0009* UEFI: Seagate BUP Ultra Touch 0004    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(3,0)/HD(10,GPT,66537b42-4255-4eef-886f-7f0d54024f1f,0x803c8000,0x39fbc000)..BO
Boot000A* UEFI: Seagate BUP Ultra Touch 0004    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(3,0)/HD(12,GPT,eaa6938b-2fda-41b8-a307-6eaa95e594e4,0xba384000,0x3a98000)..BO
Boot000B* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(1,MBR,0x4294967229,0x3f,0x33dccfc1)..BO
Boot000C* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(2,MBR,0x4294967229,0x3605f800,0xf5aec000)/HD(1,MBR,0x0,0x36060000,0x4e2f800)..BO
Boot000D* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(2,MBR,0x4294967229,0x3605f800,0xf5aec000)/HD(2,MBR,0x0,0x3ae90000,0x7b64000)..BO
Boot000E* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(2,MBR,0x4294967229,0x3605f800,0xf5aec000)/HD(3,MBR,0x0,0x429f4800,0xc350000)..BO
Boot000F* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(2,MBR,0x4294967229,0x3605f800,0xf5aec000)/HD(4,MBR,0x0,0x673e6800,0xd206800)..BO
Boot0010* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(2,MBR,0x4294967229,0x3605f800,0xf5aec000)/HD(13,MBR,0x0,0xbe1a0800,0x100000)..BO
Boot0011* ubuntu    HD(1,GPT,4f929080-5b02-4d52-a717-efffff17ed13,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)..BO



```


I do not see any "30" (seconds ) time. Actually 
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]Timeout: 1 seconds 
does not make much sense - if it is indeed timer to execute 
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]/File(\EFI\ubuntu\shimx64.efi 
The grub menu of 30 seconds timeout overrides this mystery timeout. 

[/COLOR][/FONT]
[FONT=monospace][COLOR=#000000]shimx64.efi being yet another mystery file used during Linux UEFI boot. 
And which appears to be machine generated (binary?) file ( by [/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]temporary [/COLOR][/FONT]yet unknown process) and not adding much to the [B]

resolution of the grub menu timeout of 30 seconds[/B]. 

This file seems to follow "grub"  menu items, in relative "inhumanly  readable " format. That is about all it tells. 
But it show older OS with BIOS boot options. They will go away AFTER I resolve this "30 seconds" issue. 
Not to bother to analyze.

**CORRECTION **
[/COLOR][/FONT]
[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]efibootmgr seems to be a copy of UEFI firmware "boot sequence " setup.

That is where "ubuntu"  DEVICE (?) ( not hardware - such as USB ) is identified and there are currently THREE of them , but the sequence is wrong !

At present I do not want to monkey with UEFI firmware , mainly because it "automatically" tries different "device" 
when it fails 3 times ( per RTFM) . 

[/COLOR][/FONT]

( Yes, there got to be a pony there somewhere under all this ....) 




[/COLOR][/FONT]

---

### Post by oldfred on 2020-10-24
You seem to have three different UEFI boot entries for ubuntu using different GUIDs.
Do you have three different installs with three different ESP - efi system partitions?
Or did you install & reformat ESP, so it got new UUID & GUID making new entry in UEFI and obsoleting old entry. You have to manually houseclean if obsolete entry.
You can use efibootmgr to remove old or duplicate boot entries.
See where XXXX is the number of the entry:
man efibootmgr
sudo efibootmgr -b XXXX -B 

UEFI has its own timeout. Not all UEFI have same settings. Some just have fast boot or no time. One of my systems has a fast boot off, but I can set a time delay.
That is not related to grub at all.

The install of Ubuntu to your system creates the /EFI/ubuntu folder & all the files inside it. A major update or reinstall of grub will recreate it.
Shimx64.efi is used for UEFI Secure Boot, but works if Secure boot is off. Grubx64.efi only works if Secure boot is off. 

You are booting entry 0000, is that your correct Ubuntu?

If grub is still using 30 sec it, in effect is saying something is wrong in your grub. Again go back to the default and only make one change at a time.

---

### Post by helen314 on 2020-10-24
> **oldfred said:**
> You seem to have three different UEFI boot entries for ubuntu using different GUIDs.
Do you have three different installs with three different ESP - efi system partitions?
Or did you install & reformat ESP, so it got new UUID & GUID making new entry in UEFI and obsoleting old entry. You have to manually houseclean if obsolete entry.
You can use efibootmgr to remove old or duplicate boot entries.
See where XXXX is the number of the entry:
man efibootmgr
sudo efibootmgr -b XXXX -B 

UEFI has its own timeout. Not all UEFI have same settings. Some just have fast boot or no time. One of my systems has a fast boot off, but I can set a time delay.
That is not related to grub at all.

The install of Ubuntu to your system creates the /EFI/ubuntu folder & all the files inside it. A major update or reinstall of grub will recreate it.
Shimx64.efi is used for UEFI Secure Boot, but works if Secure boot is off. Grubx64.efi only works if Secure boot is off. 

You are booting entry 0000, is that your correct Ubuntu?

If grun effect is saying something is wrong in your grubb is still using 30 sec it, i. Again go back to the default and only make one change at a time.

If grun effect is** saying something is wrong **in your grubb is still using 30 sec. 

Timely reminder WHAT is the issue. Much appreciated. 


My grub configuration is a result of several years of adding hardware and only SOME of the entries are actually working OS. 
[B]
That is NOT the issue - the grub timeout is.[/B]

---

### Post by helen314 on 2020-10-24
> **Impavidus said:**
> The error that causes grub to switch to a 30 second default instead of the normal 5 second (or whatever you set it to be in /etc/grub/default – yes, that's the right place to set it), is an error occuring during boot, not when updating grub. Sometimes, without updating grub, I see it fall back to a 30 second timeout and the next time, still without updating grub, it's back to 3 seconds. It has become more common as my computer gets older, but otherwise it's still fine, so I keep using it. At the same time, grub doesn't set the high display resolution. I guess that on your system grub has some difficulty finding the things it needs at boot time. For possible causes I would have to read the manual and quote the relevant passages for your, but I won't do that.

 For possible causes I would have to read the manual and quote the relevant passages for your, but I won't do that. 

So basically you confirmed same issue without offering an iota of solutions .
Much appreciated.
I will not suggest next time do not waste your time posting, it would be rude.

---

### Post by helen314 on 2020-10-24
> **dragonfly41 said:**
> When I investigate such issues I often turn to ripgrep to explore various directories for file content
First install ripgrep if not already installed

sudo apt install rg

Let us look for the pattern TIMEOUT=

[https://blog.burntsushi.net/ripgrep/](https://blog.burntsushi.net/ripgrep/)

TIMEOUT=

rg -i TIMEOUT=  /etc/default  | grep grub

rg -i TIMEOUT=  /boot | grep grub

I see returns such as ..

[FONT=monospace][COLOR=#000000]/boot/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000].cfg:  set timeout=30[/COLOR]
/boot/[COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000].cfg:    set timeout=10[/COLOR]
/boot/[COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000].cfg:    set timeout=0[/COLOR]
/boot/[COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#FF5454]**grub**[/COLOR][COLOR=#000000].cfg:  set timeout=10

[/COLOR]In fact I use rEFInd ..



[/FONT]
Thanks for real debugging approach to the issue. 
Appreciate your post , very much.

Here is my search 
```

a@a-desktop:~$ grep "TIMEOUT" /etc/default/grub
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
# recordfail = 1 is causing GRUB_RECORDFAIL_TIMEOUT=30 
GRUB_RECORDFAIL_TIMEOUT=5
a@a-desktop:~$ 



```

```

a@a-desktop:~$ grep "set timeout=" /boot/grub/grub.cfg
  set timeout=5
    set timeout=0
    set timeout=0
  set timeout=10
a@a-desktop:~$ 


```

Both confirm what I already know - nether one of these sets the grub menu timeout to 30 seconds

---

### Post by oldfred on 2020-10-24
/etc/default/grub is the small settings file. You have posted it before.
Did you try changing everything to defaults and then test?

You full grub.cfg with all the settings is in your /boot folder.
Again the scripts build your full grub.cfg using settings from grub.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ grep "time" /boot/grub/grub.cfg        [/COLOR]
  set [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out=30 [/COLOR]
  if [ x$feature_[COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out_style = xy ] ; then [/COLOR]
    set [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out_style=menu [/COLOR]
    set [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out=3 [/COLOR]
  # Fallback normal [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out code in case the [/COLOR][COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out_style feature is [/COLOR]
    set [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out=3[/COLOR]

[/FONT]
```

So if your settings in /etc/default/grub are not correct it defaults to 30.

---

### Post by helen314 on 2020-10-25
I have changed / added 

# test GRUB_TIMEOUT 
GRUB_TIMEOUT_STYLE=menu 

to default/grub 

The  ,manual( !)  states 



```

‘GRUB_TIMEOUT_STYLE’If this option is unset or set to ‘menu’, then GRUB will display the menu and then wait for the timeout set by ‘GRUB_TIMEOUT’ to expire before booting the default entry.  Pressing a key interrupts the timeout. 
 If this option is set to ‘countdown’ or ‘hidden’, then, before displaying the menu, GRUB will wait for the timeout set by ‘GRUB_TIMEOUT’ to expire.  If ESC is pressed during that time, it will display the menu and wait for input.  If a hotkey associated with a menu entry is pressed, it will boot the associated menu entry immediately. If the timeout expires before either of these happens, it will boot the default entry.  In the ‘countdown’ case, it will show a one-line indication of the remaining time. 
 



```

I am not sure what "they" mean " by " unset ", so I tried both 
GRUB_TIMEOUT_STYLE= 
and
GRUB_TIMEOUT_STYLE=menu 

Same results , timeout is still 30 seconds .



Here is the output of update-grub 

```

a@a-desktop:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-122-generic
Found initrd image: /boot/initrd.img-4.15.0-122-generic
Found linux image: /boot/vmlinuz-4.15.0-120-generic
Found initrd image: /boot/initrd.img-4.15.0-120-generic
Found Ubuntu 16.04.6 LTS (16.04) on /dev/sda2
Found Ubuntu 16.04.2 LTS (16.04) on /dev/sda5
Found Ubuntu 16.04.6 LTS (16.04) on /dev/sdc6
Found Ubuntu 16.04.7 LTS (16.04) on /dev/sdd6
Found Ubuntu 16.04.7 LTS (16.04) on /dev/sde2
Found Ubuntu 16.04.7 LTS (16.04) on /dev/sdf18
**Adding boot menu entry for EFI firmware configuration**
done
a@a-desktop:~$ 


```

I could use some assistance answering these questions:  

1. I realize my system is a mess, however why do I see ONLY two images. 
   I am using "only /dev/sdd6"  and do no know if it has a valid "image" 
   **What is the difference between "image" and "dev/.." entries in update-grub ?**

2. What is this line telling me ?
[B]Adding boot menu entry for EFI firmware configuration
[/B]  How can i verify such addition ? 
  Pehaps using efibootmgr ?

---

### Post by helen314 on 2020-10-25
> **oldfred said:**
> /etc/default/grub is the small settings file. You have posted it before.
Did you try changing everything to defaults and then test?

You full grub.cfg with all the settings is in your /boot folder.
Again the scripts build your full grub.cfg using settings from grub.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ grep "time" /boot/grub/grub.cfg        [/COLOR]
  set [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out=30 [/COLOR]
  if [ x$feature_[COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out_style = xy ] ; then [/COLOR]
    set [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out_style=menu [/COLOR]
    set [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out=3 [/COLOR]
  # Fallback normal [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out code in case the [/COLOR][COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out_style feature is [/COLOR]
    set [COLOR=#ff5454]**time**[/COLOR][COLOR=#000000]out=3[/COLOR]

[/FONT]
```

So if your settings in /etc/default/grub are not correct it defaults to 30.



Here is my result. 
Not sure what it is telling me.
Besides, why am I modifying machine generated file - it will change during reboot anyway. 







```

a@a-desktop:~$ grep "time" /boot/grub/grub.cfg        
  set timeout=5
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=5
  # Fallback normal timeout code in case the timeout_style feature is
    set timeout=5
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
a@a-desktop:~$   set timeout=30 
a@a-desktop:~$   if [ x$feature_timeout_style = xy ] ; then 
>     set timeout_style=menu 
>     set timeout=3 
>   # Fallback normal timeout code in case the timeout_style feature is 
>     set timeout=3
> 


```

---

### Post by oldfred on 2020-10-25
Windows can update UEFI.
Now Ubuntu can update some UEFI if vendor uses fwupd.
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

My system is older and will never be on list, so I uninstall fwupd to speed boot slightly.

First entry in grub is the install you are booting. It will be default in grub menu and should be the main working install you are using.
If using sdd6, you need to reinstall grub in that install to make it first in menu and be  the "image" that is first menu item.

Do you really need all those other installs?
I have many different installs and some obsolete. 
So I turn off os-prober and only put the other installs that are current & that I want to boot into 40_custom. 
I am sure I have posted this before.
[http://askubuntu.com/questions/848119/how-to-update-grub-on-a-dual-boot-machine/848614#848614](http://askubuntu.com/questions/848119/how-to-update-grub-on-a-dual-boot-machine/848614#848614)
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
My entries in 40_custom to boot another install. I use labels now, but have to be careful to have unique labels. Labels are more understandable than UUIDs.
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by helen314 on 2020-10-25
First entry in grub is the install you are booting. It will be default  in grub menu and should be the main working install you are using.
If using sdd6, you need to reinstall grub in that install to make it first in menu and be  the "image" that is first menu item.

Please explain  THE above. 


As far as I know there should be only ONE grub.
grub "generates" a menu for multi boot system, including "advanced (recovery) options" .

To certain degree my "grub" functions as expected, including access to OS which are no longer useful ( to me ). 

I have given up on this discussion to ever answer my "how it all interacts " question. 

Since honest opinions are considered inappropriate and rude , I shall just state:
**I am slowly realizing that the "menu timeout of 30 seconds"  will not be resolved also.**


HOWEVER - I REMAIN CONFIDENT THAT SOMEBODY WILL HELP ME TO FIND THE [COLOR=#ff0000]REAL SOURCE [/COLOR]OF THE PROBLEM.

---

### Post by dragonfly41 on 2020-10-25
Possibly .. you might get some insights by installing and launching [grub customizer.]("https://launchpad.net/grub-customizer")

I also find the [writings of Rod Smith]("https://www.rodsbooks.com/") to be helpful.  It was there that I found rEFInd as an alternative to the usual loaders.

---

### Post by helen314 on 2020-10-25
> **dragonfly41 said:**
> Possibly .. you might get some insights by installing and launching [grub customizer.]("https://launchpad.net/grub-customizer")

I also find the [writings of Rod Smith]("https://www.rodsbooks.com/") to be helpful.  It was there that I found rEFInd as an alternative to the usual loaders.

I'll give a go, BUT - menu timeout is hardy "customizing" anything. 
(Just my opinion )

---

### Post by oldfred on 2020-10-25
You have 7 grub2s.
Each install has its own grub, but only one is the default boot at any one time.
But if you boot into another install & it updates grub, then it will become the default boot.

With multiple installs you have to do a lot to manage which system is default boot.

Many have posted confusion where they are booting into a second install, but actual boot is first install.
They constantly update grub in second install, but first install is still in control and has settings that matter.
First menu item in grub that appears will be the default install.

---

### Post by Dennis N on 2020-10-25
If you have older grub as in 16.04, there was a time grub was rigged to always display the grub menu with 30 sec timeout for UEFI systems. There was a workaround, but I don't recall the details.

Of course, you don't have to patiently wait 30 sec. for it to boot - just select the entry (it preselects the default) and press enter and the boot goes on.

---

### Post by oldfred on 2020-10-25
Have you been updating grub settings in sdd6 but grub is default booting another install?
If default is not 0 and you are selecting 3 or some other entry then any editing of grub will not be the grub that boots and provides menu.

If in sdd6, update grub only updates menu.
Recreate /boot/efi/EFI/ubuntu/grub.cfg or reinstall grub2 UEFI boot
sudo dpkg-reconfigure grub-efi-amd64
sudo grub-install --efi-directory=/boot/efi

---

### Post by dragonfly41 on 2020-10-25
I just point out that if you install rEFInd (see Rod Smith books) into one of your ESP partitions then it scans through *all *the available loaders and presents these in a GUI. Moreover in refind.conf the timeout can be set.

---

### Post by helen314 on 2020-10-26
> **oldfred said:**
> Have you been updating grub settings in sdd6 but grub is default booting another install?
If default is not 0 and you are selecting 3 or some other entry then any editing of grub will not be the grub that boots and provides menu.

If in sdd6, update grub only updates menu.
Recreate /boot/efi/EFI/ubuntu/grub.cfg or reinstall grub2 UEFI boot
sudo dpkg-reconfigure grub-efi-amd64
sudo grub-install --efi-directory=/boot/efi



This last entry just ignored the original post and it is getting tiresome to keep repeating what was already discussed. 

So to be fair - for last time 
I can set the value of "default" and verify  it, I AM SETTING THE CORRECT grub. 
Same time. 
I can set the timeout to anything but 30 seconds and the  grub menu timeout will be 30 seconds.

How does that NOT prove I am setting the correct grub?



**Let us agree that we as a group cannot find the source of the problem**

[COLOR=#ff0000]**[FONT=book antiqua]Please consider this thread closed .[/FONT]**[/COLOR]

---

### Post by wildmanne39 on 2020-10-26
At OP's request thread closed!

---

