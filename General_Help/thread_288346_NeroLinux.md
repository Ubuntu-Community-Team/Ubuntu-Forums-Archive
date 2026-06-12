---
title: "NeroLinux"
date: 2006-10-29
forum: General Help
---

### Post by Osamabingandhi on 2006-10-29
I have installed nerolinux through their website and everything works fine. But how do i start the program? No icon in any menu. How do i add an icon to start nerolinux? I have tried everthing to get my burner to work and this seems like my last resort...

---

### Post by moore.bryan on 2006-10-29
[I]i'm not sure where nero puts it stuff, but you could try, in terminal ```
whereis nero
``` to see if it will tell you where it is.  if it's named something funky, that might not find it, though...

out of curiosity, why nerolinux?
[/I]

---

### Post by Osamabingandhi on 2006-10-29
I get this message: nero: /usr/bin/nero /usr/X11R6/bin/nero /usr/bin/X11/nero /usr/share/nero

How do i make an icon and a shortcut or how do i start the program?

I am trying nerolinux cause i don't get any other linuxprogram to burn a cd or dvd. It seems that everthing works but it don't, it just write a tiny part of any file. I have tried to get windows nero to work through wine but i didn't get it to work....My windows i busted and there seems to be something wrong with my hardware when i use windows but works fine with ubuntu.

---

### Post by yabbadabbadont on 2006-10-29
Did you try killing gnome-panel so that it would restart?  (killall gnome-panel)

It shows up in both Sound & Video and System Tools on my Dapper installation.

To the second poster: I use nerolinux since I already had a license from winblows and it works fine for me.

---

### Post by Osamabingandhi on 2006-10-29
Thanks it worked and i got nerolinux to start, but when i tried to burn a dvd with file on it i got this error: dma-driver error, crc error. Can i fix this?

I use NEC DVD_RW ND-3520AW\H0 T0

any clues?

---

### Post by yabbadabbadont on 2006-10-29
Other than making sure that DMA is enabled for the drive, I don't know what else to try.  Run: sudo hdparm -d /dev/??? <---replace with the correct device for your drive.  It should show you if DMA is enabled or not.

Example:```
/home/bubba $ sudo hdparm -d /dev/hdc
Password:

/dev/hdc:
 using_dma    =  1 (on)

```

---

### Post by Shay Stephens on 2006-10-29
Probably already mentioned, but you usually have to create your own launcher for nerolinux.  the command is simply ```
nero
``` and the icon is located in ```
/usr/share/nero/pixmaps/nero.png
```

---

### Post by Osamabingandhi on 2006-10-29
DMA is on...i guess it's another problem with dma.

---

### Post by Osamabingandhi on 2006-10-29
ok thanks, the icon is a good thing. But nerolinux doesn't work so i guess it doesn't matter. Any other program that uses another basic dvd/cd burner other than gnomebaker k3b disc burning application or nerolinux. Any windows burner that works in ubuntu with wine?

---

### Post by moore.bryan on 2006-10-29
[I]crc is usually a data error (bad cd/dvd)...

xcdroast works incredibly well for me; unfortunately, i don't have a dvd burner, so i can't offer any help there.
[/I]

---

### Post by Osamabingandhi on 2006-10-29
how do you configure xcdroast? I installed the program but it tells me to configure with administrators rights....

I'll try another cd, and holding my thumbs.

---

### Post by moore.bryan on 2006-10-29
*the [manual]("http://www.xcdroast.org/manual/") will help tremendously with all the basic setups... all it's telling you is to use sudo when editing config files.*

---

### Post by Osamabingandhi on 2006-10-29
Ok, thanks. It doesn't work with a blank good quality cd  either. The error i got this time was: invalid write state. Plus the old error of crc error and dma-driver error. Maybe i should reinstall dma-driver...?

---

### Post by Osamabingandhi on 2006-10-30
I have found the error!! Everywhere i read it said that you should activate the dvd burner DMA. That was the big problem. I had to turn my DMA off with "sudo hdparm -d0 /dev/cdrom"....So if there is anyone else out there with cd/dvd write problems check DMA and try it off or on(0 or 1). Thanks for all the help, now finally my ubuntu is acceptable for me (except i cant get my lcd-tv to work in the right resolution...my hardware is a bit old)

---

### Post by moore.bryan on 2006-10-30
*glad you figured it out!  also, kudos for posting the solution in case someone else falls into the same problem... too often, users just post "never mind, solved."*

---

### Post by Osamabingandhi on 2006-10-31
I agree...But i got another problem with the dma, i think it's easily fixed but haven't got around to fix it yet or search for the solution. When i restart ubuntu DMA is back on again, so i have to switch it of every time....If you have a quick answer i would be happy, otherwise there should be an easy solution for it.

---

### Post by yabbadabbadont on 2006-10-31
Add:
```
/dev/cdrom {
       dma = off
}

```
to the end of /etc/hdparm.conf and reboot.

/dev/cdrom is probably a symbolic link to the real device, so you may need to change it to the real device for it to work.  For example, here is how it looks on my system:
```
/home/bubba $ ls -l /dev/cd*
lrwxrwxrwx 1 root root 3 2006-10-31 08:48 /dev/cdrom -> hdc
lrwxrwxrwx 1 root root 3 2006-10-31 08:48 /dev/cdrw -> hdc

```
So if I wanted to disable DMA, I would use /dev/hdc instead of /dev/cdrom in /etc/hdparm.conf

I hope that helps.

---

### Post by learning curve on 2006-10-31
use K3B
it is the best

in terminal type:

sudo apt-get -i K3B

or you can look in synaptic package manager.  I'm sure it is there.  I have found that K3b is the best for CD's and DVD.:p 

Learning Curve

---

### Post by David Corrales on 2006-10-31
I've had some permission problems with cd writers before. Make sure the device in /dev has RW-RW-RW permissions.

---

### Post by Osamabingandhi on 2006-11-02
now i can burn in any program, k3b works good. The only thing is that it takes about 16 minutes for a dvd to burn. With dvddecryptor in wine it takes about 5 minutes with 16x.

My problem was that i have to have dma off.

I'll try to make dma permanent, i will tell how it goes when i do.

---

### Post by stumpalump on 2008-03-14
Turning off DMA also worked for my CD Burning issues! Couldn't burn anything before and now I can! Thank you, world!

---

