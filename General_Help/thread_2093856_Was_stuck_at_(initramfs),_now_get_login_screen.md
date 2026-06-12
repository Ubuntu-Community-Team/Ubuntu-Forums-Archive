---
title: "Was stuck at (initramfs), now get login screen"
date: 2012-12-12
forum: General Help
---

### Post by MichaelGld on 2012-12-12
For a while I was getting a blank screen for some reason, even after trying a couple of the boot parameter fixes, like nomodeset.  So after reading a lot of posts here I ran the Boot Repair CD and let it do its thing. 

One thing it did was update GRUB by adding a second Windows menu entry. I am running a dual-boot system with Windows 7 on one drive and 11.10 64-bit on the other.

The other thing it did was allow me to get past the intramfs thing, taking me to my login screen. But when I type in my password, I get a black screen with a mouse pointer, nothing else.  I'd be grateful for any help.

---

### Post by ohnonot on 2012-12-12
if you get to the login screen and a mouse pointer i'd say you're on the winning side.

do you know which session the login manager chooses when you log in?

---

### Post by MichaelGld on 2012-12-13
> **ohnonot said:**
> if you get to the login screen and a mouse pointer i'd say you're on the winning side.

do you know which session the login manager chooses when you log in?

The default session is Cairo-Dock (Gnome & Effects).  The others available are:

Cairo-Dock (Gnome no effects)
Cairo-Dock (with Unity Panel)
GNOME
GNOME Classic
GNOME Classic (No Effects)
Recovery Console
Ubuntu
Ubuntu 2D
User Defined Session

I have tested out some of the above, here are my results.
GNOME - After a delay, I get the desktop wallpaper and mouse pointer only. No panels or menus of any kind.
GNOME Classic - Same as above. At this point, I did CTRL-ALT-F1 and "sudo service gdm start" which took me to a purple login screen. Any of the choices there gets me a black screen with a mouse pointer.
Ubuntu - Delay, wallpaper and Conky display. Still no panels or menus. Conky disappears after about a minute.
From the command prompt, "sudo reboot" hangs.

Thanks for your help.

---

### Post by Rexilion on 2012-12-14
Could you paste the output of:

```
sudo dmesg
```

and paste it at pastebin.com? Especially the 'reboot' command haning might indicate the kernel is having trouble. Especially since you mentioned issue's with initramfs.

---

### Post by MichaelGld on 2012-12-15
> **Rexilion said:**
> Could you paste the output of:

```
sudo dmesg
```

and paste it at pastebin.com? Especially the 'reboot' command haning might indicate the kernel is having trouble. Especially since you mentioned issue's with initramfs.

I don't know how to upload it when I ctrl-alt-f1 to a shell. How do I copy and paste the output without a web browser?

---

### Post by Rexilion on 2012-12-15
Not tested, but this should work. Provide the link it gives you.

```
sudo aptitude -yR install pastebinit
sudo dmesg | pastebinit
```

---

### Post by MichaelGld on 2012-12-15
> **Rexilion said:**
> Not tested, but this should work. Provide the link it gives you.

```
sudo aptitude -yR install pastebinit
sudo dmesg | pastebinit
```

Now I am getting only a blank screen. No login prompt, not even a blinking cursor!

P.S. Okay, I ran Boot Repair again. After letting it repair, I ran Iceweasel and was able to create the Pastebin link: [http://pastebin.com/drJBGfxR](http://pastebin.com/drJBGfxR)

Thanks for your help, I appreciate it.

---

### Post by Rexilion on 2012-12-15
The dmesg you provide indicates a livecd with an 2.6.32 kernel.

Your rig looks like it's pretty new and booting old Linux on new hardware is not recommended.

My biggest bet is that the kernel is having trouble handling your hardware. I would recommend to install a bleeding edge distro (Fedora?) and see if things go smooth.

I'm sorry I don't have any more definitive answers. What I find frustrating is that your situation regresses pretty badly with each attempt to fix it. Narrowing down the problem becomes harder and harder each time. You just want stuff 'to work'.

I therefore recommend to restart with a newer distro. The main reason for that is the fact that you probably need a newer kernel.

---

### Post by MichaelGld on 2012-12-15
> **Rexilion said:**
> The dmesg you provide indicates a livecd with an 2.6.32 kernel.

Your rig looks like it's pretty new and booting old Linux on new hardware is not recommended.

My biggest bet is that the kernel is having trouble handling your hardware. I would recommend to install a bleeding edge distro (Fedora?) and see if things go smooth.

I'm sorry I don't have any more definitive answers. What I find frustrating is that your situation regresses pretty badly with each attempt to fix it. Narrowing down the problem becomes harder and harder each time. You just want stuff 'to work'.

I therefore recommend to restart with a newer distro. The main reason for that is the fact that you probably need a newer kernel.

That's because the only way I could boot Linux is with the live cd. The installed kernel on my system's hard drive is 3.0.0-28 generic.

---

### Post by MichaelGld on 2012-12-24
> **Rexilion said:**
> The dmesg you provide indicates a livecd with an 2.6.32 kernel.

Your rig looks like it's pretty new and booting old Linux on new hardware is not recommended.

My biggest bet is that the kernel is having trouble handling your hardware. I would recommend to install a bleeding edge distro (Fedora?) and see if things go smooth.

I'm sorry I don't have any more definitive answers. What I find frustrating is that your situation regresses pretty badly with each attempt to fix it. Narrowing down the problem becomes harder and harder each time. You just want stuff 'to work'.

I therefore recommend to restart with a newer distro. The main reason for that is the fact that you probably need a newer kernel.

I finally figured out what it was. While in Windows, I looked at Device Manager and saw a problem with one of my two DVD drives. I recalled that I didn't see it at POST. I powered down and unplugged the drive. When I powered back on, Ubuntu loaded with no problem.  I recall seeing a message to the effect of "waiting for drive " such and such. I guess it was hanging trying to get the drive to respond. Funny that it crippled Ubuntu but Windows was able to run in that situation.

In any event, thank you for your efforts to help me.

---

### Post by Rexilion on 2012-12-25
My guess that Ubuntu is indeed not able to handle broken devices all that well while Windows does. Still a bug, but glad you found 'your way out'.

---

