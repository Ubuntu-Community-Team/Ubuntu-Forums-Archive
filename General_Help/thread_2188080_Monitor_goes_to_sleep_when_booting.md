---
title: "Monitor goes to sleep when booting"
date: 2013-11-15
forum: General Help
---

### Post by gordan-vrbanec-vepar on 2013-11-15
Ok, so i've been having this problem since i installed lubuntu 13.10.
It's for an older machine, it's a Celeron with 512 MB RAM.

I had to use the alternate installer because the mouse and keyboard wouldn't work in the normal one, but it installed just fine.
What's not fine is booting.

I get the splash screen with the dots at the bottom, and after that, nothing.
Monitor goes to sleep and says "no signal".

I've been searching the net, and looking up boot options, but none say really where to add them.
I know i'm supposed to hold shift, then "e" to edit options, but i'm greeted by a screen that's kinda beyond me. I don't know what to do.
I'm suppesed to add "nomodeset" there to fix it, but it's already there, and it's not working.

Here's how it looks like:

```
setparams 'Ubuntu'

recordfail
         load_video
         gfxmode $linux_gfx_mode
         insmod gzio
         insmod part_msdos
         insmod ext2
         set root='hd0,msdos1'
         if   [ x$feature_platform_search_hint = xy ]; then
            search --no-floppy --fs-uuid --set=root --hint-bios=hd0,ms\
dos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  e1297181-c\
b7f-4eeb-b6a0-7a38cedd6109
         else
             search --no-floppy --fs-uuid -set=root e1297181-cb7f-4eeb\
-b6a0-7a38cedd6109
         fi
         linux            /boot/vmlinuz-3.11.0-12-generic root=UUID=e1297\
181-bc7f-4eeb-b6a0-7a38cedd6109 ro nomodeset   quiet splash $vt_hando\
ff
         initrd           /boot/initrd.img-3.11.0-12-generic
```

I'm not sure where to put what option, and i'm not sure what option does exactly what.
As you see, "nomodeset" is already there, so it should work, but it doesn't.

I've been trying to put other options as suggested on various forums on this topic but it's still the same, and i don't know what i'm doing so yeah...
Some of the options include a "=" sign which i can't input. I tried every button on the keyboard. It's not there for some reason. o.O
Others say that i should change one line with another, but those lines are just not there. All there is, is what i wrote above.
I wrote it manualy because i couldn't get a screenshot, so there are some typos maybe, but that's that all in all..

I should mention that i did a memtest, and everything is ok, no errors.
Another thing is, BIOS doesn't show. There's no POST screen, monitor only turns on when i either blindly hold shift to get to grub, or when the splash screen shows up.
Spamming DELETE doesn't do anything, i can't get into BIOS...

And it's not the monitor's fault, i'm using the same monitor for my main computer (from which i'm writing now), and i'm using Ubuntu here with no problems.


Anyway, i've hit a wall, and don't know what to do anymore, and editing this options is beyond me...
Can anyone help?

---

### Post by ibjsb4 on 2013-11-15
Hi again :)

Please navigate to /etc/default/grub and verify that nomodeset is present.  

```
cat /etc/default/grub
```

The line your looking for should read like this:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

I am going off line, hopefully others will jump in.

---

### Post by gordan-vrbanec-vepar on 2013-11-15
Hi again! :)

Can if do this from grub? Because i can't get into the OS and use the terminal.
If i can do this from grub command line, i'll try it and post the results...

---

### Post by gordan-vrbanec-vepar on 2013-11-16
Ok. I did this and found the line you mentioned. 

It only had "quiet splash" in it. 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

There's a line below it though. The same one but without "default" part. 

GRUB_CMDLINE_LINUX="nomodeset"

So there is "nomodeset" present, but not at the line you mentioned. Not the one with "default" in it.

How can i edit this without booting into Linux?

---

### Post by ibjsb4 on 2013-11-16
Ok, you need to change that to read:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 
GRUB_CMDLINE_LINUX=""

You can do this in terminal using a terminal editor called Nano.  Its already installed on your system.

[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

```
sudo nano /etc/default/grub
```

But first make a backup of grub.
```

sudo cp /etc/default/grub /etc/default/grub.old
```

Edit:  I forgot.  Update grub after the edit.

```
sudo update-grub
```

---

### Post by gordan-vrbanec-vepar on 2013-11-16
Ok, i did that. First it gave me and error writing to a read only file system.

I seached a bit on the net and found this:

```
mount -o remount,rw /dev/sda1
```

After that, it allowed me to make changes.



I made a copy of grub, edited it with nano like you showed me, saved and updated grub.

Still nothing. The monitor still goes to sleep.
I really don't get it. :/

Is this maybe an issue with the hardware?
Maybe the graphic card? It's an on-board integrated card.
I'm just throwing wild guesses here, i don't know why it won't boot.

It should. I previously had Bodhi linux installed on that computer, and it was fine, it even played youtube videos, so it can't be the graphic card. It may be weak, but it's not so weak that it can't display a desktop environment.
What else can i try?

---

### Post by ibjsb4 on 2013-11-16
You mention other changes that were made.  That would explain to me how nomodeset was on what I consider to be the wrong line.

I can think of other things to try, but wonder for you if a reinstall would be better.  Nomodeset could be installed as part of the default install when the 'Function Options' pop up.  I think its F4 and click on nomodeset.  Then its done from the start.

As I recall Bodhi is built on Ubuntu 12.04.  So that would only add to the mystery.

---

### Post by gordan-vrbanec-vepar on 2013-11-16
Yeah, Bodhi is built on Ubuntu. That's why i'm wondering this too.
I mean, it should work if Bodhi did.

I can't recall now if i set nomodeset during install (it's F6 i think), or not...
I used the alternate install. 

I'll try to reinstall it and see what happens.

---

### Post by oldfred on 2013-11-16
Do you get grub menu? Or holding shift key from BIOS does grub menu then show up.
The recovery mode uses the nomodeset by default as that is the setting you found in grub's settings.
But you have to run the sudo update-grub in your install to get it to update the grub menu.

You can edit grub as a one time change from grub menu. Use e for edit, scroll down to linux line and replace quiet splash with nomodeset.  
If you cannot get grub menu you can press down arrow once after BIOS. Grub will see entry and then use the second boot entry or the recovery mode. Timing may be important as it has to be after BIOS, but before grub starts booting kernel.

---

### Post by gordan-vrbanec-vepar on 2013-11-16
> **oldfred said:**
> Do you get grub menu? Or holding shift key from BIOS does grub menu then show up.
The recovery mode uses the nomodeset by default as that is the setting you found in grub's settings.
But you have to run the sudo update-grub in your install to get it to update the grub menu.

You can edit grub as a one time change from grub menu. Use e for edit, scroll down to linux line and replace quiet splash with nomodeset.  
If you cannot get grub menu you can press down arrow once after BIOS. Grub will see entry and then use the second boot entry or the recovery mode. Timing may be important as it has to be after BIOS, but before grub starts booting kernel.

Yes, i get into the grub menu by holding shift after i hear a beep since i can't see the BIOS for some reason.
If i use "e" to edit, there is nomodeset already there. See the code in my first post. That's what i see when i press "e".
If i go to advanced options as i later did, i can get into linux command line mode.

The command line recovery mode is basically just linux if i understand it correctly, but without the desktop. So up to this point, it has nothing to do with grub anymore right?
There i had to re-mount the /dev/sda1 disk to make it write possible, and i could edit the grub file.
I did edit it, save it and i did run sudo update-grub so it should update the grub menu upon reboot. I got the "update successful" type message after that so i assumed everything was ok.
Still, nothing changed.

if i go to grob command line, none of those commands work. It doesn't even reckognise "sudo".

all i get is 

grub>_

and i'm guessing i can't do anything i need from there.
I'm going to try a reinstall when i get the time, and i'll see what happens, because, now i just don't know what else i can do.

---

### Post by gordan-vrbanec-vepar on 2013-11-17
Ok, i installed lubuntu again. Again with the alt install.
This time i didn't use "nomodeset" during installation.

It's still the same. Won't boot. After the splash screen, the monitor goes to sleep and i can't do anything.

I even went through all the steps like before.
Edited it with "e" for one time boot. The only difference was that there wasn't "nomodeset" present there like the first time i installed it.
I added it, booted up and nothing.

Then i went to the recovery mode, edited the grub with nano, and again. There was no "nomodeset", just "quiet splash".

It looked like this;

```
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" [/COLOR]
[COLOR=#000000]GRUB_CMDLINE_LINUX=""[/COLOR]
```

I changed it to look like this;

```
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" [/COLOR]
[COLOR=#000000]GRUB_CMDLINE_LINUX=""[/COLOR]
```

Still nothing. I don't get it...

---

### Post by oldfred on 2013-11-17
Do you have nVidia? Other older video cards/chips may need different settings.
 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

Generally you want to boot and experiment with boot parameters and only then if one works, permaently add it to grub's menu by editing /etc/default/grub and running sudo update-grub to add setting change to grub's menu file grub.cfg.

If system has 512MB of RAM, how old is video system? Full Ubuntu to run Unity needs newer systems. You may be better off with Xubuntu or Lubuntu.

---

### Post by gordan-vrbanec-vepar on 2013-11-17
Well I'm not trying to run unity. I installed lubuntu. :)

The card is on board. Integrated. I'm not sure what chip it is. 

But thank you for the link. I'm going to experiment and see.

---

### Post by gordan-vrbanec-vepar on 2013-11-19
Ok, after another day of googling and trying i finally gave up. 
I tried to install Bodhi back, but nothing. Then LXDE, and still nothing. Both crashed at install.

Lastly i have put the disk in another computer, installed it there, put it back and it finally works.
It's weird how a "light" distro doesn't have a text install...
Instead i have to boot the entire OS into what limited memory i have and hope for the best.
Of couse it failed. It took about an hour to get to the create user screen. 

Well, all is well that ends well..
I installed LXDE on it through another computer, and so far i'm not complaining.

Thanks for all the help. :)
Too bad that it didn't quite work, but i appreciate it a lot!

Thank you!

---

