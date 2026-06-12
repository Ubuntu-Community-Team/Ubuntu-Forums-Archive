---
title: "xServer issues + GRUB Questions"
date: 2007-04-02
forum: General Help
---

### Post by Leumasx on 2007-04-02
Right...

I installed Ubuntu a few weeks ago, and got the xServer - No screens found error. 

Connected to #ubuntu, and somebody in there suggested i change my driver from nv, to something else, which i can't remember at this moment in time. >.<

Anyways... that didn't help, and i still had the No Screens Found error. Someone in #ubuntu told me that my GFX card wasn't supported, but, according to Nvidias supported cards page, it is.

For a while now, i've had to scroll down in GRUB to boot into my only working OS, (Windows) and i don't want to keep doing that. I want a working Ubuntu, and Windows in GRUB, or no GRUB, with Windows automatically loading. :P I can't change my grub order, because Ubuntu won't load.

So, question time:

1 - Is there a solution to my xserver problem?

2 - Can i change my GRUB from within Windows? (Ubuntu is on a seperate partition on my HDD)

3 - If there is no solution, how do i remove GRUB, so it automatically boots into Windows?

Cheers.

If anything isn't clear, just ask and i'll explain it better.

-Sam

---

### Post by chewearn on 2007-04-02
> **Leumasx said:**
> 1 - Is there a solution to my xserver problem?
I can't answer the question whether GFX card is supported or not.  Did you try looking into installing nvidia driver by Envy.
Link to Envy here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Also, I noticed in your profile that your are running ubuntu 5.10?  Any reason for not try ubuntu 6.10 edgy?

> 2 - Can i change my GRUB from within Windows? (Ubuntu is on a seperate partition on my HDD)
Sure, you can boot to the liveCD, then, mount your linux partition.  This will give you access to /boot/grub/menu.lst, which allows you to change the default boot OS.  There are plenty of threads in the forum on doing this; I (or someone else in the forum) can follow-up with the steps, if you have difficulty.

> 3 - If there is no solution, how do i remove GRUB, so it automatically boots into Windows?
Also possible, via Windows installation disc, rescue floppy, etc.  There are also plenty of info around the web to show you how.  If you finally reach the point that you really want to remove ubuntu, then this is the last step to get back to Windows; someone here will be able give you the steps or point you to the instruction to help you out.

---

### Post by Leumasx on 2007-04-02
> **AstalaVista said:**
> 
Also, I noticed in your profile that your are running ubuntu 5.10?  Any reason for not try ubuntu 6.10 edgy?

I have tried downloading the latest Ubuntu, and i can't even get to an install. ;) I get the Xserver error much sooner. :( The Ubuntu 5.10 is from the free CD's i requested a while ago. :P

> **AstalaVista said:**
> 
Sure, you can boot to the liveCD, then, mount your linux partition.  This will give you access to /boot/grub/menu.lst, which allows you to change the default boot OS.  There are plenty of threads in the forum on doing this; I (or someone else in the forum) can follow-up with the steps, if you have difficulty.

Cool, cheers for that. Mind posting a short little tutorial for me? :)

> **AstalaVista said:**
> 
Also possible, via Windows installation disc, rescue floppy, etc.  There are also plenty of info around the web to show you how.  If you finally reach the point that you really want to remove ubuntu, then this is the last step to get back to Windows; someone here will be able give you the steps or point you to the instruction to help you out.

Again, thanks. :D

I'll look into that Envy thing, now. :)

-Sam.

Edit: Reading the Envy program, it seems like i need to be *IN*    Ubuntu. I'm not physically in Ubuntu. After the install, where you have to remove the CD, and reboot, shortly after, it gives me the xServer error, and after that, a command line. :)

---

### Post by chewearn on 2007-04-02
First, bear in mind I have not used 5.10; the commands below should work for 6.06 and 6.10; and probably would for 5.10 as well, but you never know.

> **Leumasx said:**
> I have tried downloading the latest Ubuntu, and i can't even get to an install. ;) I get the Xserver error much sooner. :( The Ubuntu 5.10 is from the free CD's i requested a while ago. :P 

Not sure if you have tried this at the command line, after Xserver fails:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```or:
```
sudo dpkg-reconfigure xserver-xorg
```You can also try the alternate CD installation, if you have not done so.

> Cool, cheers for that. Mind posting a short little tutorial for me? :)Boot into live cd, open a terminal.
Create a mount location:
```
sudo mkdir /media/ubuntuhd
```Then, locate your ubuntu partition:
```
sudo fdisk -l
```It should be a line with ext3 and linux (post the output if you are unsure).

Then, mount the partition; here I give the example of /dev/hda1.  You should use the one for your ubuntu partition from the fdisk command above.
```
sudo mount -t ext3 /dev/hda1 /media/ubuntuhd
```Then, you can open up the menu.lst:
```
sudo gedit /media/ubuntuhd/boot/grub/menu.lst
```Find the line near the top of the file starting with "default".  There should be a number after that.  This number counting from 0, indicate which OS/kernel to load by default.  Go down to near the bottom of the file, count the number of boot entries until you get the one for Windows; and replace the number next to "default" by your count.
Again, if you are unsure, post your menu.lst


> Edit: Reading the Envy program, it seems like i need to be *IN*    Ubuntu. I'm not physically in Ubuntu. After the install, where you have to remove the CD, and reboot, shortly after, it gives me the xServer error, and after that, a command line. :)Unfortunately,  envy does not supports ubuntu 5.10.  It is still possible, via a roundabout way to install envy without access to the gnome desktop, but only if you can get 6.06 or 6.10 installed.

---

### Post by Leumasx on 2007-04-02
Hmm. with 6.10, after the Ubuntu menu comes up, and i select install, i get the xServer error, and NO command line.

Does this mean that it's going to be near-impossible for me to get Ubuntu working?

-Sam

EDIT : Just tried booting into the Live CD, and was surprised to see the xServer error while it was loading everything up...

I'm sure that's not right. :P Maybe there's other factors messing with my Ubuntu? :s

---

### Post by chewearn on 2007-04-04
Two things you could do:
1. Post your hardware specs, maybe someone in this forum can give a suggestion on your particular hardware.

2. Try the alternate disc; this installation is text based; I personally have not used this method though.
[http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)

---

### Post by Leumasx on 2007-04-04
Hardware spec:
(Built it myself)

CPU : AMD 64 bit Athlon 3500+
RAM : Kingston DDR 3200 (1Gb)
GFX Card : Nvidia 6600 (**NOT** GT)
Motherboard : Winfast 6100K8 (Not a very well known brand, I don't think. Motherboard monitor doesn't have this brand. :P This was bought because the first Mobo had a fault)
HDD : Maxtor 250Gb (50Gb partitioned for Ubuntu)

That's all you need to know, i think. :P

I won't bother with an alternative disk yet, hopefully someone can tell me why i'm getting an Xserver error all the time. :(

Cheers,

-Sam

---

### Post by Leumasx on 2007-04-08
Anyone got any suggestions?

-Sam

EDIT : Over 100 views, and only one person has been able to give any input? :(

---

### Post by Leumasx on 2007-04-08
> **Leumasx said:**
> 
EDIT : Over 100 views, and only one person has been able to give any input? :(

*Sorry for all the posts, but i'm eager to solve my problem...*

---

### Post by bulldog on 2007-04-08
Just download the alternate 6.10 release and install it text based.
After the install it's possible your xserver will crash again.
If so,boot into recovery mode [command line] and install the following.

Find which kernel you have installed with```
uname -a
``` this will return something like"Linux AMD64 2.6.20-14-generic #2 SMP Mon Apr 2 20:37:49 UTC 2007 i686 GNU/Linux" [I use Feisty]
Install the restricted modules for your kernel```
sudo aptitude install linux-restricted-modules-2.6.20-14-generic
``` you have to use the kernel which you find with the previous command of course.

Install the graphics driver.
```
sudo aptitude install nvidia-glx
```

Open the xorg.conf ```
sudo nano /etc/X11/xorg.conf
``` and find the 'driver' section.
Change the driver from 'nv' to nvidia,safe the file with Ctrl-x and enter and  reboot.

It should be working now.

---

### Post by Leumasx on 2007-04-10
Cheers for that. Got a direct link to the download?

-Sam

---

### Post by chewearn on 2007-04-10
[http://releases.ubuntu.com/6.10/ubuntu-6.10-alternate-i386.iso](http://releases.ubuntu.com/6.10/ubuntu-6.10-alternate-i386.iso)

---

### Post by Leumasx on 2007-04-10
Cheers, guys. :)

I'll do that sometime tonight.

-Sam

---

### Post by Leumasx on 2007-04-10
OK... I downloaded it, and burned it to disk, no problems.

Installed it, no problems.

Restarted, and the Ubuntu logo appeared, with a loading bar... After that get's all the way to the end, the screen goes black, and nothing happens.

So, I thought it might be my xServer... Booted into recovery mode, installed the nvidia driver, and then proceeded to edt my xorg.conf... Except, there wasn't anything there.. 

Now, i'm at a loss... It's gone from xServer... To an unknown issue. 

Really thought I had Ubuntu working for a moment, too. :(

Any ideas, please?

-Sam

---

### Post by Leumasx on 2007-04-11
Anyone?

-Sam

---

### Post by chewearn on 2007-04-12
Did you install nvidia driver using the Envy script?  Unfortunately, you situation is quite unusual, and I am out of my depth.  Only thing I could think of is wait for Feisty release, which supposed to be out sometime next week.

---

### Post by Leumasx on 2007-04-12
> **AstalaVista said:**
> Did you install nvidia driver using the Envy script?  Unfortunately, you situation is quite unusual, and I am out of my depth.  Only thing I could think of is wait for Feisty release, which supposed to be out sometime next week.

Alright, i suppose that's the only thing i can do. :P

Would like to get Ubuntu working, but heck, doesn't look like i can. :(

C'mon Fiesty! Please work. :P

Cheers for all your help though. Greatly appritiated. :)

-Sam

---

