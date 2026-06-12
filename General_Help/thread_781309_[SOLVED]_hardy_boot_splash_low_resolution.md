---
title: "[SOLVED] hardy boot splash low resolution"
date: 2008-05-04
forum: General Help
---

### Post by Jose Catre-Vandis on 2008-05-04
When I switched to Hardy, I noticed that the boot splash with the progress bar has gone all big and low res. On my Gutsy it was alot smaller and seamingly high res. can't see any grub settings that make this, can anyone advise where to revert to a high res boot splash?

---

### Post by sabi on 2008-05-04
Install StartUp-Manager and you can easily reset the resolution.

---

### Post by angry_johnnie on 2008-05-04
Somebody else posted this, and rather than keeping a bookmark, I just copied it to tomboy :-)
Anyway, it's quite handy.

640x480 800x600 1024x768 1280x1024
..768..........771.........773.........775............256 colors
..784..........787.........790........,793.................(8 bit)
..785..........788.........791.........794.................(16 bit)
..786..........789.........792.........795.................(24 bit)

Edit /boot/grub/menu.lst
add **vga=XXX** at the end of the **kernel** line (where XXX is any number from the chart).
Save and exit.


Edit:  It's hard to guess what it's gonna look like after saving this, and those darn dots refuse to stay put, but you get the idea, don't you?   640x480=first column.  800x600=second column, and so on.

---

### Post by Jose Catre-Vandis on 2008-05-04
> **sabi said:**
> Install StartUp-Manager and you can easily reset the resolution.

That worked a treat, many thanks

---

### Post by keforex on 2008-05-17
I installed the Start-Up manager under KDE 4 but I can't find its entry on any menus. How do I run it from the terminal?

---

### Post by Jose Catre-Vandis on 2008-05-20
under gnome it is started with
```
gnome-splashscreen-manager
```

---

### Post by aasche on 2008-06-14
An alternate way: look at */etc/usplash.conf*. In comparison to Gutsy, under Hardy the values for *xres* and *yres* are missing, i.e.

```
xres=1024
yres=768
```

Finally, use *update-initramfs*:

```
sudo update-initramfs -u
```

---

### Post by Jose Catre-Vandis on 2008-06-17
Thanks aasche - useful addition :)

---

### Post by editrix on 2008-06-17
Could someone please explain something to a total idiot?

My usplash.conf says my resolution is 
xres=1024
yres=768

But startupmanager says 640x840 and 8 bits

I've been trying to fix the black bootup screen issue and only made things much, much worse. Is that 640x840 for my normal resolution, or is it something specific to the screen that displays during bootup?

---

### Post by VMC on 2008-06-17
> **editrix said:**
> Could someone please explain something to a total idiot?

My usplash.conf says my resolution is 
xres=1024
yres=768

But startupmanager says 640x840 and 8 bits

I've been trying to fix the black bootup screen issue and only made things much, much worse. Is that 640x840 for my normal resolution, or is it something specific to the screen that displays during bootup?

Look at the end of the line on your kernel boot in /boot/grub/menu.lst. 
For example mine says:
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d8533154-cef1-4cce-a823-9f3f74aab65b ro quiet splash vga=773

Notice the vga=773 on the end of the line. Now go up to @angry_johnnie's graph to show values.

---

### Post by mempman on 2008-06-17
> **angry_johnnie said:**
> Somebody else posted this, and rather than keeping a bookmark, I just copied it to tomboy :-)
Anyway, it's quite handy.

640x480 800x600 1024x768 1280x1024
..768..........771.........773.........775............256 colors
..784..........787.........790........,793.................(8 bit)
..785..........788.........791.........794.................(16 bit)
..786..........789.........792.........795.................(24 bit)

Edit /boot/grub/menu.lst
add **vga=XXX** at the end of the **kernel** line (where XXX is any number from the chart).
Save and exit.


Edit:  It's hard to guess what it's gonna look like after saving this, and those darn dots refuse to stay put, but you get the idea, don't you?   640x480=first column.  800x600=second column, and so on.


This doesn't work with HardyHeron.  It makes changes to the bootup screen but not as desired.  It used to work fine for fiesty fawn for me.

---

### Post by VMC on 2008-06-17
Did you install Startup Manager? Then run it and choose the screen size you want. there's a lot of things that program will allow you to do. I could NEVER get any splash screen or 1024x768 on my boot-up until I installed that program. It updates Grub automatically also.

---

### Post by editrix on 2008-06-18
> **VMC said:**
> Look at the end of the line on your kernel boot in /boot/grub/menu.lst. 
For example mine says:
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d8533154-cef1-4cce-a823-9f3f74aab65b ro quiet splash vga=773

Notice the vga=773 on the end of the line. Now go up to @angry_johnnie's graph to show values.

Oh, VMC, thanks for this. I think I'm finally getting somewhere.

I currently have 4 versions of the menu.lst (one active, 3 backups of variations) and the [COLOR="Red"]only one[/COLOR] that has any vga information [COLOR="Red"]at all[/COLOR] is the one currently being used, which runs okay until the login screen--which is unusable, and I have to reboot into recovery mode, which then fixes my xorg.

**If** I understand what's going on:

Since my monitor is 1024x768, the line should read:

 ro splash vga=773

Is that correct?

Except mempman says that doesn't work for Hardy :-(

Needless to say, I am very, very reluctant to change things and make them even worse.

---

### Post by cpetercarter on 2008-06-18
I have had the "blank boot screen" problem since I first installed Hard Heron several weeks ago, and had given up on fixing it. Since the computer booted OK, it didn't seem to matter. I had tried resetting the x and y values in etc/usplash.conf and then running update-initranfs, but it made no difference. Still a blank screen during boot-up.

Earlier today, I decided to play around with the little buttons on my monitor. These produced a menu which, among other things, told me what the screen resolution was (1280 x 1024). Since I had already tried using these figures in etc/usplash.conf, I was unimpressed. However, I then pressed the buttons during boot-up, and found that the menu told me that although the optimal screen resolution was indeed 1280 x 1024, the actual screen resolution (ie during boot-up) was 720 x 400. I put these lower figures into etc/usplash.conf, ran update-initramfs, and I now have a proper boot splash screen, oscillating orange bars etc, and am generally a happy bunny.

I guess the moral of this is that screen resolution values during boot-up are not necessarily the same as the values after successful boot-up and log-in; that the Ubuntu installation process does not necessarily identify the correct screen resolution values for usplash.conf; and that it is worth trying to establish for your monitor what the correct boot-up screen resolution values are.

---

### Post by Pjotr123 on 2008-06-18
This will probably help:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 3 )

---

### Post by cpetercarter on 2008-06-18
@Pjotr123
Yes - [http://ubuntutip.googlepages.com/]("http://ubuntutip.googlepages.com/") is a very valuable guide. I have followed it with good results on several points. 

It suggests that you should if necessary change the values in etc/usplash.conf to xres=1024, yres=768. I found that this did not solve the "blank boot screen"  problem on my monitor. It needed xres=720, yres=400.

---

### Post by editrix on 2008-06-18
Ack! I am doomed!

After reading the posts by cpetercarter and Pjotr123 I pressed all the buttons on my monitor (no joy) and then tried to run startupmanager. Lo and behold, I got a message saying there's a new grub menu.lst and what do I want to do, with several options....

EDIT: I tried to post last night, but the forum was closed for maintenance. Basically, whatever that upgrade was fixed my problem, except now I have duplicate entries in the Grub menu. But I think I can fix them myself. I'm leaving in what's below in case someone encounters the same problem and goes searching. The "fix" for the black screen was to hit the tab key.

[COLOR="Plum"]BEGIN NO LONGER RELEVANT TEXT:
I tried to see the difference between the two files, but only one file was visible, so I clicked on maximize for the Konsole window. At that point the screen went black! I cannot get that message window back.

Then I tried to run startupmanager again and it told me that menu.lst was missing the line:

### END DEBIAN AUTOMAGIC KERNELS LIST

Except it isn't.

So then I looked at what was in the terminal (I'd started a second session) and found this:
> 
Grub2 not detected
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Grub Legacy detected
Usplash detected
Splashy not detected
User requested shutdown.

The other thing is, I have both the -16 and the -18 kernel, which used to show up when I booted, but now only the -16 is there. So how do I get the option to use the -18 kernel, which is what the default was?

It's not listed in any of my previous menu.lst copies, but can I just copy the -16 data and change it all to 18?

EDIT: I have something called QGRUBEditor, which seems to give me the option of adding the -18 kernel (NB: It is NOT listed in the current menu.lst). The only thing is, I seem to have TWO -18s now. And I really have no idea what the consequences of anything I do will be. I'm afraid to shut down.[/COLOR]

---

