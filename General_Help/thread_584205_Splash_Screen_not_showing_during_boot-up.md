---
title: "Splash Screen not showing during boot-up"
date: 2007-10-20
forum: General Help
---

### Post by Goombie on 2007-10-20
Whenever I start up my computer, it boots up into the Gutsy login prompt, but, while it is booting, nothing shows on the screen. In Feisty, there was always the ubuntu logo with the orange progress bar, but now I don't see anything. Anyone know what the problem could be/a solution?

Thanks! :)

---

### Post by fjgaude on 2007-10-20
I do believe this is the way the designers wished it to be -- clean and simple.

---

### Post by Goombie on 2007-10-20
Possibly, but it's too simple for me. I'm used to seeing status messages, etc when the computer boots up.

---

### Post by KevinCLovesU on 2007-10-20
Yeah, I'm not really happy with the disabling of the splash. The argument is that it slowed down people's machines, but I personally am not finding any difference.

If you upgraded (not a clean install from CD) you can re-enable it. I'm not sure if clean installs still have the splash.

To enable it:

[LIST]
[*]Alt+F2 ("Run Application")
[*]Type gconf-editor (then hit enter)
[*]select Apps>gnome-session>options
[*]check show_splash_screen
[/LIST]

Then it should be present when you log in.

---

### Post by bonzini on 2007-10-20
Wow, now that there's a nice looking splash screen someone decided to take it away?  So that we look at ... nothing, for a minute or so, wondering what's going on?

Hmm, seems like a bit of a strange decision to me!

---

### Post by Goombie on 2007-10-21
Yes, it is an odd decision.

> **KevinCLovesU said:**
> Yeah, I'm not really happy with the disabling of the splash. The argument is that it slowed down people's machines, but I personally am not finding any difference.

If you upgraded (not a clean install from CD) you can re-enable it. I'm not sure if clean installs still have the splash.

To enable it:[LIST]
[*]Alt+F2 ("Run Application")
[*]Type gconf-editor (then hit enter)
[*]select Apps>gnome-session>options
[*]check show_splash_screen[/LIST]Then it should be present when you log in.

I did a clean install, and I found that option in gconf. Although, I just rebooted, and I still don't see the splash screen. Also, I'm not talking about the splash screen that appears after you login, I'm talking about the one that should show while Ubuntu is loading, before the login prompt. THAT is the one I don't see; instead, it's just a blank screen for my computer. :(

---

### Post by Goombie on 2007-10-23
Well, I think I've figured out the problem. Apparently, my boot screen image is missing! Is there anywhere I can download a fresh copy of it?

---

### Post by arthur5005 on 2007-10-24
Well I just installed Gutsy on one my computers and I'm having the exact same issue. Gutsy starts up fine, but even before the GDM, I don't see the ubuntu loading splashscreen. Just darkness, then the login screen.. which I suppose is fine, but I am used to that little orange bar going back and forth. :)

Anyone know what the cause of that issue might be?

---

### Post by Goombie on 2007-10-25
Woohoo, I'm not the only person with this problem!
arthur5005, would you mind posting your computer specs? That way we can see if there might be something in common with our machines that causes this.

Mine:
Dell Inspiron 9100 Laptop
3.2Ghz Pentium IV CPU
1 GB Kingston RAM, 80GB Fujitsu HDD
Graphics: 128 MB ATI Mobility Radeon 9700
Dell Truemobile 1350(I think) wireless with Broadcom 4306 chipset

All I can think of for now, now shamlessly bumping this topic. :)

---

### Post by dashnak on 2007-10-25
This happens to me as well, I only see the splash when I'm turning my laptop off, not when turning it on.... It's kind of annoying....
I see many people in this thread confused what you are talking about with the after-gdm-before-desktop-is-fully-loaded splashscreen....

---

### Post by Caffeine_Junky on 2007-10-25
This is strange that all these people are missing there Ubuntu Loading screen (Ubuntu with orange progress bar)  because I downloaded a fresh copy of Gutsy and I have one!

In fact, I have noticed that the "orange bar" fully completes before moving on now where in Feisty and pre-release Gutsy the screen would change when the bar was only 80 to 90% full.

---

### Post by por100pre1 on 2007-10-25
It should be a resolution issue:

Try this:

```
sudo cp /etc/usplash.conf /etc/usplash.conf_backup
```

```
gksudo gedit /etc/usplash.conf
```

Something like this should appear:

> # Usplash configuration file
xres=1024
yres=768

Change the resolution and save.

---

### Post by Sain on 2007-10-26
This didn't worked for me... It seems that a lot of people are having this issue, but there is no universal solution... Apparently graphics configuration for splash screen is not set up correctly. 
To me it happens even with LiveCD.

Damnit! Couldn't they just leave it the way it was in Fiesty?

EDIT:
Oh by the way, Gutsy Tribe releases didn't have this issue.. :-/

---

### Post by kakao on 2007-10-26
I'll queue myself up here as my laptop suffers from the same issue. But first to clarify (for those who wonder) here is a link to the splash screen that I'm talking about (and I understand everyone else): [http://ubuntuforums.org/attachment.php?attachmentid=3197&d=1130424660](http://ubuntuforums.org/attachment.php?attachmentid=3197&d=1130424660)

The funny bit is I see the splash when I
[LIST=1]
[*]in BIOS enable automatic display selection
[*]plug in an external monitor/TFT
[/LIST]
on the external monitor. More over the monitor seams to be taken as the "main" display. I have more issues under gnome/gdm. But that's not what I'm talking about, here.

I'll try to edit usplash.conf and see how it goes...

By the way:
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

---

### Post by kakao on 2007-10-26
Unfortunatelly nothing changed. I also tried LiveCD boot and the spalsh showed up as it should. A couple of boots back it was really annoying as I didn't see a forced fsck was running and, mr. impatient I am, I rebooted. I found myself in recovery mode after that...

Another thing I noticed is when going to for reboot the splash does show up even with only one (the laptop's) display (no monitor attached). The laptop is a Amilo M model (fujitsu-siemens) with Intel Graphics (82852/82855 GM/GME).

Edit: After I now booted with monitor attached I noticed the splash is gone while going down for reboot after I edited usplash.conf back to default:
```

# Usplash configuration file
xres=1280
yres=1024

```

Usplash only shows while shutting down with the following usplash.conf:
```

# Usplash configuration file
xres=1024
yres=768

```

As I said earlier, on external monitor the splash shows anytime it's supposed to show up (boot as soon as "font changes" and shut down up to power off or reboot).

I noticed one more thing: While on laptop display only going into console (CTRL+ALT+F1) it shows in rather ugly large font, lines shifted strangly and display only in the central 800x600 radius even though the "virtual output " (not shown but calculated) goes further down (varified with CTRL+L). This whole thing is not influenced by grub time vga modes (passing vga=ask). Mode does change until this "font change" during boot, right before the splash should show (excuse me not knowing the right terminology) and than everything is the same as described above.

Cheers folks.

---

### Post by Excalibre on 2007-10-27
Yeah, I'm not seeing the splash screen either, and I checked, and usplash already had the right resolution. I didn't see it on the install CD either. I'm using an nVidia video card with the restricted drivers and everything else video-related seems to be doing great. Just not this.

---

### Post by janko on 2007-10-27
On the live CD the splash appeared, but after the installation is gone. I've modified the resolution in usplash but now it shows only when shuts down. I've even tried to mess with grub options but nothing... I hope someone would find a solution

By the way... I need to see what happens during start-up cause after a fresh install it takes forever compared with feisty.

Janko

---

### Post by muadnu on 2007-10-27
The same happens to me, I'm on a Dell Vostro 1400, with Nvidia. Changing the resolution on usplash.conf didn't make a difference.

> **janko said:**
> 
By the way... I need to see what happens during start-up cause after a fresh install it takes forever compared with feisty.


You can see what happens on startup anyway. Edit the file /boot/grub/menu.lst and look for the line that looks like

```
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6b0fc929-0be2-410e-a1b3-f6c9a0e2909b ro quiet splash
```

(or the one corresponding to the kernel you are using) and erase the words quiet and splash.

---

### Post by kakao on 2007-10-27
Since there are a few by now reporting similar issues I filed a [bug at launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/157620"). I guess it would be helpfull and speed up solutions if you take a couple of minutes to report the following in short:

[LIST=1]
[*]no usplash at boot | shutdown (booted from harddrive)
[*]no usplash at boot | shutdown (booted from LiveCD)
[*]hardware: possibly laptop model, graphic chips, (...?)
[*]attache /etc/usplash.conf and /var/log/dmesg after you booted with missing usplash
[*]anything else you consider relevant
[/LIST]

---

### Post by kongsian on 2007-11-01
Hi.  Here is how to obtain your bootup splash again on Gutsy.  Works for me.

[http://embiggened.wordpress.com/](http://embiggened.wordpress.com/)

Reproduced here in case the previous blog disappears

1) Call up the Terminal (Accesories>Terminal). Type in sudo gedit /boot/grub/menu.lst. This should open the GRUB config file, from there, what you will want to edit is usually near the end. You&#8217;ll have a bunch of entries with &#8220;Title Ubuntu, kernel&#8221; and kernel numbers, you need to find the one you&#8217;re booting from, then under it in the &#8220;kernel&#8221; part of the entry, you&#8217;ll find the &#8220;splash&#8221; option.

2) At the very end of the kernel line after &#8220;splash&#8221; , add &#8220;vga=791&#8243; This is the weird part for me, because I&#8217;m not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf (by typing sudo gedit /etc/usplash.conf in the Terminal)

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won&#8217;t know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k <insert results from uname -r here>

This rebuilds the image that Grub uses to start the system.

Cheers.
Kong Sian

---

### Post by Goombie on 2007-11-02
Someone beat you to it, Kongsian. Here's link to the page on the UbuntuGuide Wiki:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

It'll explain why that VGA number was 791 (or whatever), plus it gives good instructions how to solve the problem.
Here's the copied text:

if your system is booting slowly or your ubuntu splash screen is not being displayed it could be that Usplash has created the s[plash screen incorrectly 
1) edit /boot/grub/menu.lst 
  sudo gedit /boot/grub/menu.lst
At the very end of the kernel line after "splash" , add  
  "vga=***" 
replace *** with the code from the table below that corresponds with the resolution  and colour setting you are using 
(Note: this table didn't post very well; I'd suggest visiting the link).
Screen      640x480  800x600  1024x768  1280x1024  1600x1200    
Colors    256  769           771  773  775  796    32,768  784  787  790  793  797    65,536  785  788  791  794  798    16.8M  786  789  792  795  799  


the line should look something like this:
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=20fd9912-6383-4860-9cd8-88a11909d715 ro quiet splash vga=791
Save that file, close it,  
2) edit /etc/usplash.conf 
     sudo gedit /etc/usplash.conf
change the resolution to the one you set in the previous step save and close 
3) rebuild the bootsplash screen 
  get your kernel version
   uname -r
     This lists your current kernel version.
   sudo update-initramfs -u -k <insert results from uname -r here>
 This rebuilds the image that Grub uses to start the system.
4) reboot 

Ta~da!

---

### Post by gdp77 on 2007-11-03
**1) First u need to edit the usplash.conf to setup the correct resolution of your screen**

```
sudo gedit /etc/usplash.conf
```


This is my usplash.conft (15" wide laptop)  :

```
# Usplash configuration file
xres=1280
yres=800
``` 

**2) now, type the correct resolution for your monitor and save.**

**3) then in a terminal type :**

```
sudo update-usplash-theme usplash-theme-ubuntu
```

Now u will have both the splash screen at boot and it will be MUCH faster :)

Have fun

---

### Post by kakao on 2007-11-03
> **gdp77 said:**
> **1) First u need to edit the usplash.conf to setup the correct resolution of your screen**

**2) now, type the correct resolution for your monitor and save.**

**3) then in a terminal type :**


Thanks, that finally made my notebook boot like a charm! The only difference is I put grub's resolution in /etc/usplash.conf:
```
# Usplash configuration file
xres=1024
yres=768
```
(Update: wrong solution, changed now.)

plus I also did the "grub thing" Goombie pointed out.

For debugging I shall add I first did what you suggested, gdp77: Adjust resolution of /etc/usplash.conf *and* after that did update-usplash-theme. I've changed usplash.conf before but never updated initramfs. Eventhough that made usplash show up at boot it only shows after a couple of seconds of "scrolling text". But adding vga=971 to grub's menu.lst (I changed the line
```
# defoptions=splash quiet
```
which is Ubuntu's default, to
```
# defoptions=splash vga=791
```
Now I called 
```

sudo update-grub

```
for the changes to take effect. Not only do I get the usplash screen from right after leaving grub's menu at boot time. Under Ubuntu's usplash I get information on what is going on at boot time in the background - in nice colours that is :)

Cheers!

---

### Post by kakao on 2007-11-03
Hi Kong Sian.

And thanks for your guide. As I just posted that's the information I needed to fix my setup. Let me add a couple of knick-knacks:

> **kongsian said:**
> 

[http://embiggened.wordpress.com/](http://embiggened.wordpress.com/)


Here's the [permanent link]("http://embiggened.wordpress.com/2007/10/25/tips-for-ubuntu-newbs-like-me/") for those who read this thread some time in future.

> **kongsian said:**
> 
sudo update-initramfs -u -k <insert results from uname -r here>


You can shorten this by only doing 
```

sudo update-initramfs -u -k `uname -r`

```

Update: But as far as I understand it this is all been taken care of if you do instead:
```

sudo update-usplash-theme usplash-theme-ubuntu

```

Cheers!

---

### Post by kakao on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/157620](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/157620) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				since I couldn't find an edit option to add launchpad bug links to a post I'll just post a new one here...

---

### Post by muadnu on 2007-11-03
When I run update-grub I get

```
Searching for splash image ... none found, skipping ...
```

I guess somehow the splash image is missing from my installation, and thus it's not shown. Any idea where I can get it?

---

### Post by pacsum on 2007-11-03
It is a bug, it's not that the developers wanted it in that way. It is very simple just do this:

1) Open Terminal
2) Type:   sudo gedit /etc/usplash.conf and change the resolution to 1024x768
3) sudo update-initramfs -u -k `uname -r` 

That's it.

---

### Post by motang on 2007-11-03
> **KevinCLovesU said:**
> Yeah, I'm not really happy with the disabling of the splash. The argument is that it slowed down people's machines, but I personally am not finding any difference.

If you upgraded (not a clean install from CD) you can re-enable it. I'm not sure if clean installs still have the splash.

To enable it:

[LIST]
[*]Alt+F2 ("Run Application")
[*]Type gconf-editor (then hit enter)
[*]select Apps>gnome-session>options
[*]check show_splash_screen
[/LIST]

Then it should be present when you log in.
Wow cool thanks that fixed the exact problem I was having. :-D

---

### Post by kakao on 2007-11-03
> **muadnu said:**
> When I run update-grub I get
```
Searching for splash image ... none found, skipping ...
```


Let me get something straight here. There are a couple of splash screens involved on the way from power on to your desktop after login. Usplash is one of them that is discussed in this thread. In contrast the error grub gives you likely is because you might not have any grub splash images (that's the splash grub showes at boot *prompt* -- where you select which operating system to start up. So it's really more like a background image to the boot chooser). 

**Bootsplash:**
Does the following command give any answer?
```

find /boot/grub/ -iname '*xpm.gz*' -type f -print

```
(search for image files necessary for bootsplash functionality). And what does this give you?
```

sudo egrep -i '^[^#]?splashimage.*$' /boot/grub/menu.lst

```
(look for grub splashimage option). If this doesn't show anything I'm mistaken and you don't have a grub splash issue. If you like the idea of a rather colourfull greeting from your PC see here for [howto setup grub splash images]("http://ubuntuforums.org/showthread.php?t=30341&highlight=grub+splashimage") or a [quick guide]("http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image/"). If you don't want them edit menu.lst
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup && gedit /boot/grub/menu.lst

```
search for 'splashimage' and add a '#' at the beginning of that line.

**Usplash:**
It's also called [bootsplash]("http://www.bootsplash.org/") sometimes. That's what Ubuntu has enabled by default giving you Ubuntu's circle with an orange progress bar beneath. If you think the usplash itself is missing on your system do
```

ls -la /usr/lib/usplash/

```
There should at least be a file called usplash-theme-ubuntu.so. If not do
```

sudo aptitude update && sudo aptitude install usplash-theme-ubuntu

```
Otherwise you should do
```

sudo aptitude update && sudo aptitude reinstall usplash-theme-ubuntu

```
(notice the install/reinstall difference). To ensure the socalled initramfs is up-to-date proceed with (which should be done by the reinstalling usplash-theme-ubuntu but just to double check)
```

sudo update-usplash-theme usplash-theme-ubuntu

```
This will take a couple of seconds. Now, when restarting, you should see (hopefully) the orange progress bar (usplash) while booting until the xserver (gdm) is up and asks you for your username and password. After you delivered that we see...

**Gnome/KDE splash:**

That's the third of the most famouse splashes we have in Linux and the one [KevinCLovesU]("http://ubuntuforums.org/showthread.php?p=3586195#post3586195") and motang are refering to.

I hope this post actually helped and did rather not confuse.

Good luck and post your results if you like.
Cheers.

---

### Post by semperfiguy on 2007-11-03
I am also having this problem I have tried different vga modes (773 791) and changing around the usplash but all i get is a black screen.  I noticed that it is putting quiet underneath each kernel for grub/menu.lst.  even though it is already in the kernel= line.

I would settle for just having the text scrolling, just anything but a black screen.

Here is my /boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=df783529-6c0c-4757-90bc-dec87e0227f5 ro

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
# defoptions=quiet splash vga=773

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=df783529-6c0c-4757-90bc-dec87e0227f5 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=df783529-6c0c-4757-90bc-dec87e0227f5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by kakao on 2007-11-04
> **semperfiguy said:**
> I am also having this problem I have tried different vga modes (773 791) and changing around the usplash but all i get is a black screen.


Can you please post the output from
```

sudo aptitude update && sudo aptitude reinstall usplash-theme-ubuntu

```
and from 
```

ls -la /usr/lib/usplash/

```
and also from
```

uname -a && lsmod | grep 'fbcon'

```

You will have done
```

sudo update-grub

```
after you edited menu.lst each time before booting? Otherwise your vga=773 wouldn't be there (see below).

What kind of screen/monitor/display do you have, semperfiguy? 15" notebook or whatever size seperate monitor?

> **semperfiguy said:**
> 
I would settle for just having the text scrolling, just anything but a black screen.

You should always be able to see a screen with plain text lines listing what's going on if you press Alt+F1 while your PC is booting (or at a later stage Ctrl+Alt+F1 or at some setups Alt+Ctrl+F6 or +F8 ). Do you see anything at all if you do that? If not try vga=ask (see below) or see if [this bug known for Gutsy's kernel]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135613") has anything to do with it.

> **semperfiguy said:**
> 
I noticed that it is putting quiet underneath each kernel for grub/menu.lst.  even though it is already in the kernel= line.

That's because you (correctly, see below) changed the vga option in defoptions line. update-grub will adapt your settings to become kernel parameters, i.e. make lines like "kernel ... vga=773" at the bottom of menu.lst.

```

...
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

...

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=773

```

Another posibility to have vga settings right at early boot time (for grub) is to use vga=ask instead of declaring explicit numbers. After next boot you will be asked to try vga settings. You cannot break anything because you could always skip that and boot normally and then change back vga settings in menu.lst. [More on grub vga options]("http://ubuntuforums.org/showthread.php?t=454392").

Cheers.

---

### Post by semperfiguy on 2007-11-04
Ok Here is the commands you asked me to put in:

1. sudo aptitude reinstall usplash-theme-ubuntu
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  usplash-theme-ubuntu 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/80.4kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 97060 files and directories currently installed.)
Preparing to replace usplash-theme-ubuntu 0.17 (using .../usplash-theme-ubuntu_0.17_i386.deb) ...
Unpacking replacement usplash-theme-ubuntu ...
Setting up usplash-theme-ubuntu (0.17) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done  
```

2. ls -la /usr/lib/usplash
```
total 2632
drwxr-xr-x   2 root root    4096 2007-11-04 13:35 .
drwxr-xr-x 151 root root   40960 2007-11-03 16:35 ..
lrwxrwxrwx   1 root root      36 2007-11-02 21:25 usplash-artwork.so -> /etc/alternatives/usplash-artwork.so
-rw-r--r--   1 root root 2643784 2007-09-28 07:32 usplash-theme-ubuntu.so

```

3. uname -a && lsmod | grep 'fbcon'
```
Linux ubuntuportable 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

```

And yes I was running sudo update-grub after I edited the menu.lst file.  Right now I have it set on nosplash so I just get the scrolling text, but I would like to have the splash screen.

It is a 15" Dell inspiron 1100 laptop.  I did have the splash screen before with the vga set at 773 when I was running fiesty.

The "quiet" option I was talking about is this one:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=df783529-6c0c-4757-90bc-dec87e0227f5 ro nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
**quiet**

```

---

### Post by kakao on 2007-11-04
> **semperfiguy said:**
> 
1. sudo aptitude reinstall usplash-theme-ubuntu
2. ls -la /usr/lib/usplash

Ok, usplash itself should be setup right and initram knows about it. Have you booted using
```

# defoptions=quiet splash vga=773

```
If that doesn't show usplash I cannot think of anything else to look for, sorry. Oh, wait, one more thing, try
```

# defoptions=quiet splash

```
first. There are some [known issues since the latest kernel]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910") (that you use also) if one uses vga=... option with grub. If've got blank consoles (ttys, that's what's normally coming up when you press Ctrl+Alt+F1) if I use vga=... But I at least still see usplash at boot time.

> **semperfiguy said:**
> 
And yes I was running sudo update-grub after I edited the menu.lst file.  Right now I have it set on nosplash so I just get the scrolling text, but I would like to have the splash screen.

It is a 15" Dell inspiron 1100 laptop.  I did have the splash screen before with the vga set at 773 when I was running fiesty.


If you have the chance of an external monitor sitting around somewhere that might give some hints since before I had mine fixed I could smoothly see usplash on an external monitor but just not on the laptop LCD itself. I played around with BIOS options for CTR and LCD. But that shouldn't be nessesary. If you feel comfortable with it though it might give you more information.

> **semperfiguy said:**
> 
The "quiet" option I was talking about is this one:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=df783529-6c0c-4757-90bc-dec87e0227f5 ro nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
**quiet**

```

Ah, I see. Strange! You don't happen to call update-grub with any options or anything that could put it there? Those lines are entirely generated automatically by update-grub. What puzzles me most is I cannot find any such option in the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html") so this doesn't make any sense to me. Nevertheless you could try and delete that "quiet" lines and see if they are there again after you run update-grub.

Anyway it seams to me since around Gutsy release boot graphics are at sixes and sevens which is not nice at all.

Hope this was helpfull nevertheless.
Cheers and good luck.

---

### Post by semperfiguy on 2007-11-04
Well thanks for your help, I will play around with those options even though I've tried them before with no luck.  It seems like I will just have to stick with the bland scrolling text for now at least until the kernel is updated.

---

### Post by muadnu on 2007-11-05
> **kakao said:**
> Let me get something straight here. There are a couple of splash screens involved on the way from power on to your desktop after login. Usplash is one of them that is discussed in this thread. In contrast the error grub gives you likely is because you might not have any grub splash images (that's the splash grub showes at boot *prompt* -- where you select which operating system to start up. So it's really more like a background image to the boot chooser). 


Thanks for the help. The problem actually is with what you call usplash. I don't have a grub splash image, and that's why I got that message when running update-grub, so thanks for the explanation.

Running
```
find /boot/grub/ -iname '*xpm.gz*' -type f -print
```
gives me a list with splashimages, but
```
sudo egrep -i '^[^#]?splashimage.*$' /boot/grub/menu.lst
```
gives nothing.

```
ls -la /usr/lib/usplash/
```
does show usplash-theme-ubuntu.so, so that's not the problem.

I have actually tried all you said, and I have changed the configuration at usplash.conf and the vga modes on /boot/grub/menu.lst, but still nothing, no matter what combination I use. My laptop has a 1440x900 resolution, by the way...

It's not a pretty bad problem anyway, the boot-up is not especially slow, but it's still anoying...

---

### Post by namanbagga on 2007-11-06
Try this[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html")

---

### Post by kakao on 2007-11-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **namanbagga said:**
> Try this[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html")

Thanks for your link, namanbagga, but I don't see anything over there that hasn't been suggested in this thread (even though it's quiet neat).

The problem seams to lie somewhere related to kernel modules. There have been massive changes along with the latest update of the kernel. At launchpad.net they have a very [long thread on a bug on framebuffer]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910") (used for displaying higher resolution at boot time before X is up) that might be related. There are suggestions as to how it might be worked around for some hardware. But its fairly technical so I wouldn't advice anyone that doesn't rely on it to play around with it. I certainly wouldn't know how to fix anything beeing broken duiring such operations.

Cheers.

Hoping this thing is solved soon as it seams to effect many Ubuntu Gutsy users on diverse hardware!

---

### Post by Goombie on 2007-11-06
I second that one, chocolate - er, kakao. :)

Just to repeat myself, here's a link to a solution that worked for me, and might work for you:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

Of course, the idea is to prevent this from happening in future Ubuntu versions, as well. I'll leave this thread marked unsolved for now, to see if we can nail down a cause for this.

---

### Post by kakao on 2007-11-07
> **Goombie said:**
> I second that one, chocolate - er, kakao. :)

Just to repeat myself, here's a link to a solution that worked for me, and might work for you:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)


Thanks for your thoughts, Goombie. In fact, the steps you pointed out where the ones that brought back usplash for me (as said before). But the bug stated affects my notebook nevertheless. If I omit grubs vga option I get to see ttys (that in fact are there and functioning all the time, but no output is shown with vga= in use). I'm a bit in a delema here, since if I use vga= I get to see usplash but no ttys. If I remove vga= I have ttys but no usplash. As my X is not working with external Monitors as disired I'll have to work on that. But if no working ttys are present I only will be able to fix broken xorg.conf settings in single user mode, rebooting each time. But since right now I don't have the time to play around I might as well just wait :)

Cheers.

---

### Post by muadnu on 2007-11-08
> **namanbagga said:**
> Try this[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html")

Same here, I have tried this with many alternative configurations, but nothing. Thanks for the link, though.

In any case, Gutsy works quite good for me (I just have some other small issues with the video), and this usplash problem is not really that annoying, so I guess I'll simply remove the quiet option on grub and wait till some update (or maybe Hardy) fixes this...

---

### Post by Jubalgunn on 2008-01-11
Thanks kongsian !!
The solution you have posted works a treat on my Fujsitsu P series lifebook witha resolution 1280 x 768:)

---

### Post by jazz452 on 2008-05-17
Worked for me with hardy 64 bit.But remember to "sudo update-initramfs -u" afterwards or it wont work

---

### Post by rybaxs on 2008-07-22
i got the same problem on my Pavillion P4 HT the splash screen is missing,, is their away to use the wireless connection in ubuntu?

---

