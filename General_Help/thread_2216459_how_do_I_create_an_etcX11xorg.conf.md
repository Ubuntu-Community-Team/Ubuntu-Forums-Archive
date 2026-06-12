---
title: "how do I create an /etc/X11/xorg.conf"
date: 2014-04-12
forum: General Help
---

### Post by michel-defever on 2014-04-12
I find a solution for my purple/green screen and distorted video/flash 
but as an absolute beginner tell me how to execute following solution:
I'm able to open a terminal window.

you need to create an /etc/X11/xorg.conf file with the following contents:

 	Code:
 	Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

Thanks in advance
[email]michel.defever@telenet.be[/email]

---

### Post by 23dornot23d on 2014-04-12
Can you run these commands in a terminal - so we can get some in formation about your setup.

 			[INDENT] 				**lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'**[B]

lsb_release -a[/B] 				 			

These commands will then give information back - like this as an example 

( just cut and paste what you get back from yours - using those commands. )

> 
K53SV:~$     lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Kernel driver in use: i915
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev ff) (prog-if ff)

K53SV:~$     lsb_release -a 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty


[/INDENT]

---

### Post by SeijiSensei on 2014-04-12
Open a terminal and enter the command "sudo nano /etc/X11/xorg.conf".  You'll be in an editor.  Paste the lines in your post into that file, then hold down Ctrl and type "X". You'll be prompted to save the file; say yes. Then reboot. 

(Nano has a convenient menu of commands at the bottom of the screen.  The carat "^" represents the Ctrl key.)

---

