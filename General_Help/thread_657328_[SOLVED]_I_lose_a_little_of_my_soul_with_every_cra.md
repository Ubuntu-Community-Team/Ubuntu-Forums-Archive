---
title: "[SOLVED] I lose a little of my soul with every crash."
date: 2008-01-03
forum: General Help
---

### Post by anc2020 on 2008-01-03
Hi, if I appear sore, its because I am. The computer I am using ran happily under windows. Under Ubuntu 7.10, the screen would freeze often, and I would have to turn off, completely unplug power, and restart. To this day I do pretty much the same thing, every day. Flash sound didn't work either, so I decided just to do a fresh install on Kubuntu 7.10. It worked great, thanks for asking. Flash had sound, the screen didn't freeze, then something horrible happened. I used the network GUI to try to use the DHCP option for wireless. It didn't work, there was no "Return to defaults" option, it just crashed. I left it alone, opting wired instead. Long story cut short, I am probably the most afflicted user to have ever existed, and am blessed with every crash to have existed. Kernel panic, tick. Firefox crash when I type a URL, tick. Random KDE apps crashing, tick. Adept manager broken, tick. Network wireless broken, can't return to default, tick. Screen freeze and death, tick. So maybe you can understand where my soreness came from. Why oh why did I change that one option on wireless? I don't care. This kind of thing should not make a computer unusable. GUI changes should be un-GUI-able. Of course I would just re-install, but I'm not entirely convinced it won't just die again.

Oh, some technical info. The install CD had correct hash, no defect, memory passed test.

---

### Post by shad0w_walker on 2008-01-03
And through all of this you haven't once asked for help on the forums? Seems you don't have a giant amount of right to complain if you didn't even try to sort it out, Also from the sounds of it, sounds most likely you have some dodgy piece of hardware that windows can just about ignore or has some strange work around for.

---

### Post by Mithrilhall on 2008-01-03
If you're looking for stability and your system doesn't have cutting edge hardware try running Debian. Etch is extremely stable.

---

### Post by Kzin on 2008-01-03
> **anc2020 said:**
> Hi, if I appear sore, its because I am. The computer I am using ran happily under windows. Under Ubuntu 7.10, the screen would freeze often, and I would have to turn off, completely unplug power, and restart. To this day I do pretty much the same thing, every day. Flash sound didn't work either, so I decided just to do a fresh install on Kubuntu 7.10. It worked great, thanks for asking. Flash had sound, the screen didn't freeze, then something horrible happened. I used the network GUI to try to use the DHCP option for wireless. It didn't work, there was no "Return to defaults" option, it just crashed. I left it alone, opting wired instead. Long story cut short, I am probably the most afflicted user to have ever existed, and am blessed with every crash to have existed. Kernel panic, tick. Firefox crash when I type a URL, tick. Random KDE apps crashing, tick. Adept manager broken, tick. Network wireless broken, can't return to default, tick. Screen freeze and death, tick. So maybe you can understand where my soreness came from. Why oh why did I change that one option on wireless? I don't care. This kind of thing should not make a computer unusable. GUI changes should be un-GUI-able. Of course I would just re-install, but I'm not entirely convinced it won't just die again.

Oh, some technical info. The install CD had correct hash, no defect, memory passed test.

I also do not touch my GUIthingie for the Roaming/Wired network option.  I ended up having to change it manually (I was going to static from DHCP).  There is probably an error log somewhere for that, but I got it working so I never checked.

The relevant file is /etc/network/interfaces
You will probably have something like...
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.x.x

auto eth0

```

Where eth may not be eth, but something else.
You would want to change that to 

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

```

Then sudo /etc/init.d/networking restart

Let me know if this helps

---

### Post by cdenley on 2008-01-03
> 
Kernel panic, tick. Firefox crash when I type a URL, tick. Random KDE apps crashing


Any of these problems would make me suspect a hardware problem. The reason you never had any problems with Windows could be that something began failing recently, or maybe you have a bad sector on your hard drive, and ubuntu just happens to write something important to that sector. I would test the memory and hard drive, then start swapping parts out if you have spares.

---

### Post by fireboy129 on 2008-01-06
> **Kzin said:**
> I also do not touch my GUIthingie for the Roaming/Wired network option.  I ended up having to change it manually (I was going to static from DHCP).  There is probably an error log somewhere for that, but I got it working so I never checked.

The relevant file is /etc/network/interfaces
You will probably have something like...
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.x.x

auto eth0

```

Where eth may not be eth, but something else.
You would want to change that to 

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

```

Then sudo /etc/init.d/networking restart

Let me know if this helps

i am having the same problem. it says permission denied when i try to go to /etc/network/interfaces even if i'm root. help?

---

### Post by fireboy129 on 2008-01-07
bump.

please help.

---

### Post by forestpixie on 2008-01-07
I can't actually help as such - but you've appended your problem to one of those 'I hate this' please help me threads - unless you actually get a reaction from someone who happens to be looking you would be much better of with a thread of your own.

---

### Post by oldb0y on 2008-01-07
anc2020... You still there, or have you completely given up? Don't be afraid of asking about your problems, we all try to help, but we can't help unless you want to.

---

### Post by Kzin on 2008-01-07
> **fireboy129 said:**
> i am having the same problem. it says permission denied when i try to go to /etc/network/interfaces even if i'm root. help?

Do you know how to use vi commands?  If so type sudo vi /etc/network/interfaces.  If not, I'll suggest some other potential ways to edit.

---

### Post by fireboy129 on 2008-01-08
nope. dont know.

info plz!!

---

### Post by forestpixie on 2008-01-08
try 

```
sudo nano /etc/network/interfaces
```

although I've never needed to do it myself - but it would let me open it

do a backup first just in case

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak.0811
```

---

### Post by anc2020 on 2008-01-10
Very sorry to everyone, I was pretty pissed that day.
I'm amazed that even the negative replies to this thread were constructive.
Thankyou for the support, even though the post has silly amounts of attitude.

I ended up reinstalling kubuntu. The first login was for about 40mins, just updating the system. The second login it started crashing in parts after 30 mins, so it is my hardware at fault somehow. The starter panel died and the rest fell soon after.

I've done the mem-test a fair few times and no problem was found, but I'll give it another whirl. I think that my last system, the one I was moaning about, had an fsck problem at some stage, so it would seem to be the hard drive thats wrong.

Please could someone say whether that sounds a correct diagnosis before i mark as solved?

Really sorry for the pointless moaning

---

### Post by fireboy129 on 2008-01-11
its still not working...

have another thread going on... search for GUI Freeze.
thanks.

---

### Post by anc2020 on 2008-01-11
The live CD crashed, and considering my previous Ubuntu installation also crashed a bit (though not as much as these ones), I reckon its the memory, thread complete

---

