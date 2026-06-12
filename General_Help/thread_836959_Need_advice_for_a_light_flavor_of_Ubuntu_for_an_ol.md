---
title: "Need advice for a light flavor of Ubuntu for an old laptop"
date: 2008-06-22
forum: General Help
---

### Post by Phastor on 2008-06-22
As I type this, I am running Ubuntu 8.04 on my Compaq Presario 700US laptop which has the following specs:

AMD Duron 900MHZ
256MB Memory
Compaq Twister video card which I think is really an S3 Trident.  16MB shared memory
20GB HD.

To give a little history of what this laptop runs, it came with Compaq's stripped down version of XP which ran smoothly.  However I wasn't satisfied with XP home, so I installed XP pro, which ran horribly.  It runs Compaq's tweaked version of XP just fine, however it nearly goes comatose if you try running an untampered installation of XP.

I installed Ubuntu on it a couple weeks ago and love it.  It recognized every piece of hardware in the laptop; even the volume buttons which not even XP pro recognized.  It also flawlessly connected to my WPA secured wireless network with no issues.  There is one problem, however.  Even though the laptop is running Ubuntu better than it did XP pro, it's still painfully slow.  It's just too heavy for this laptop to handle.  I have been looking at the different lighter flavors of Ubuntu.  I'm trying to find a good balance of features and a small footprint.  So far from what I have read, Fluxbuntu is the lightest you can get.  However I see that it's still on 7.10 and I know that Ubuntu doesn't have good WPA wireless support until 8.04.  So unless someone can tell me how I can get WPA working on 7.10, Fluxbuntu won't meet my needs.  I know there's a couple other light versions out there such as Xubuntu and Kubuntu.  Does anyone have any advice they could give me?  Any help would be greatly appreciated.

---

### Post by -grubby on 2008-06-22
Xubuntu should do fine on that hardware. Btw, Kubuntu is not a "light" version of Ubuntu

---

### Post by pietjanjaap on 2008-06-22
fluxbuntu.
[www.distrowatch.com](www.distrowatch.com), here you find a lot more.

A problem i see is a sis driver, so read first about this.

---

### Post by Phastor on 2008-06-22
> **nathangrubb said:**
> Xubuntu should do fine on that hardware. Btw, Kubuntu is not a "light" version of Ubuntu

I guess I threw that in there since I understand that KDE is a less system demanding environment than Gnome.  Or am I wrong on that?

So I have Xubuntu and Fluxbuntu suggested so far. I'll look into those two versions.  I'll have to do some extra research on Fluxbuntu due to my needs for WPA, or I could wait till they make it for 8.04.  I guess my next question would be alternative apps.  As much as I love Firefox, it's kind of slow.  I know about Opera, and I heard of another browser, but forgot the name.  And I don't even want to try opening up OpenOffice on this thing.  Right now I'm running Banshee for music and it seems to be fairly responsive despite Ubuntu being slow.

Any other advice on app alternatives as well as more OS suggestions would be appreciated.

---

### Post by benthegreat on 2008-06-22
Iv always found kubuntu to be slower than ubuntu actually, might just be me!

Iv got Xubuntu running smoothly on  a 700mhz P3 with 256mb memory, it'll easily fit on a 20G hdd. Id recommend Xubuntu, its exactly what it was made for.

Opera's cool, but most apps, to some extent, run as fast as the OS. So try firefox. That laptop isn't that bad as far as linux running laptops go, try running Xubuntu with firefox and openoffice, it might not be that bad and untill you try, you'll never know.

---

### Post by snowpine on 2008-06-23
> **Phastor said:**
> I'll have to do some extra research on Fluxbuntu due to my needs for WPA, or I could wait till they make it for 8.04.  

Hi Phastor, you can upgrade Fluxbuntu from 7.10 to 8.04 by following these directions: [http://ubuntuforums.org/showthread.php?t=807113](http://ubuntuforums.org/showthread.php?t=807113)

The problem with Fluxbuntu is that the project basically seems to be abandoned, so it is not being updated and there is no support. If you are up to the challenge, it is definitely the swiftest of the 'buntus. However, I think Xubuntu should run well on your hardware, too. Xubuntu is easy to use and well-supported.

Let us know more about your wireless issues, and perhaps we can give you some tips. There are workarounds for various problems. Good luck!

---

### Post by snowpine on 2008-06-23
> **Phastor said:**
> I guess my next question would be alternative apps.  As much as I love Firefox, it's kind of slow.  I know about Opera, and I heard of another browser, but forgot the name.  And I don't even want to try opening up OpenOffice on this thing.

The browser that comes with Fluxbuntu is called kazehakase. It is pretty fast (if you turn off the auto-complete in the preferences) in theory, but in practice, I prefer Firefox because of the Adblock plugin. Nothing speeds up a browser like not having to load all those ads! You could also check out swiftfox.

I am running openoffice just fine on a P3 with 256mb ram. It takes it a little while to get started, but no problems otherwise. Abiword and gnumeric are lightweight alternatives, and in fact are included in Xubuntu.

---

### Post by lswb on 2008-06-23
I have an even older compaq ES500 wtih a Pentium 3/650 and have no trouble running any variety of ubuntu, although it does have 512MB memory, not 256. Memory is pretty reasonably priced, maybe some more will help. As another poster suggested, check your video drivers too. If it is running in VESA or mode it will make any system seem slow.

---

### Post by dracayr on 2008-06-23
I recommend Gebuntu

dracayr

---

### Post by pmlxuser on 2008-06-23
did you try one version behind 8.04 i mean 7.10 it can work perfect on such a machine.
but if you still want 8.04 then Xubuntu 8.04

---

### Post by Zorael on 2008-06-23
KDE is not heavier than Gnome. They're on fairly equal foot. There's a big step down to Xfce, and you can get even further with Fluxbox and other (compared to KDE/Gnome) way lighter environments memoryprint-wise.

---

### Post by bodhi.zazen on 2008-06-23
To be honest, for old hardware, IMO, you are best off doing a minimal install and adding only what applications you need.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/](http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/)

---

### Post by snowpine on 2008-06-23
> **Zorael said:**
> KDE is not heavier than Gnome. They're on fairly equal foot. There's a big step down to Xfce, and you can get even further with Fluxbox and other (compared to KDE/Gnome) way lighter environments memoryprint-wise.

I agree. I found there was a bigger difference between Fluxbox and Xubuntu than between Xubuntu and Ubuntu.

Another option is to install Xubuntu and then Fluxbox (not Fluxbuntu). You can choose between Xfce and Fluxbox sessions when you log in.

---

### Post by markjensen on 2008-06-23
> **snowpine said:**
> ...
Another option is to install Xubuntu and then Fluxbox (not Fluxbuntu). You can choose between Xfce and Fluxbox sessions when you log in.
That's how I did it.   XFCE is a bit peppier than Ubuntu (Gnome).   KDE and Gnome (as mentioned earlier in the thread) are about on equal footing, when it comes to resources used.  You aren't going to see significant differences on lower-end hardware; they will both be sluggish as they swap so much.

I grew very fond of fluxbox when I was using lower-end hardware, myself.  So when I got my new computer, I just threw in the Xubuntu CD I used for my wife's computer, installed it and did the **sudo apt-get install fluxbox** (and conky and the other little apps I like).

If XFCE runs acceptably fast for you, then you might prefer to keep it - it is more friendly of a WM/DE to those not familiar with the *box way of using right-click and generally not having desktop icons.

---

### Post by LambdaCalculus379 on 2008-06-23
I found Fluxbuntu to be very speedy and useful for a decrepit old P2/450 laptop a co-worker gave me. It fits comfortably in 256MB of RAM and gave them enough free space in the 10GB drive it had. AbiWord and Kazehakase work very well for light documentation work.

While Xubuntu is still pretty light and fast, IMHO Fluxbuntu works better on even older hardware.

---

### Post by Phastor on 2008-06-23
Wow.  I didn't know there were more replies here.  I haven't checked for a couple days.  Anyway here's the update.

After reading the replies here, I decided I would give Xubuntu a try.  However I could not get the laptop to boot off the Xubuntu CD for the life of me.  I'm hoping I just burned a bad disk.  I was visiting family at the moment and wasn't able to burn another.  I will try another CD when I get home.

I am at the airport as I type this.  I've been here for a couple hours and got bored, so I tried a couple things mentioned after reading these several new replies.  PDX offers free wireless, so I was able to install Fluxbox and xfce.  I've tried both.  I'm amazed at the difference when I tried out Fluxbox.  It's like a whole new laptop.  However it's a little too minimal, though I may be able to tweak it around,  I'd like to be able to set up a few monitors for my wireless and battery which I see aren't set up by default.  I was very impressed with xfce since it's very close to Gnome, but runs so much smoother, however not as peppy as Fluxbox.  I'm running xfce as I type this.

I'll play around with these some more and see which one I like best.  I imagine I'll able to explore both environments better in a comfortable setting rather than sitting at an airport terminal with a furnace of a laptop cooking my legs.

There has been a couple comments about my low memory and how I should upgrade.  I agree since I know the 256MB is my biggest problem.  However, this laptop only has room for a single memory module, and will only accept a max of 256MB per module, which is already used.  So unfortunately I am unable to upgrade.

Thanks for all the replies.  I'll give another update once I have had some time with this in a more convenient setting.  Suggestions and comments are still welcome!

---

### Post by tel93 on 2008-06-23
Mate you are never going to get Xubuntu to run well on 256mb of ram.

Try CrunchBang Linux 8.04.01 (an Ubuntu derivative with Openbox).

Or, alternatively, try Debian with XFCE.

---

### Post by RedSquirrel on 2008-06-23
@OP: As bodhi.zazen suggested above, if you want to stick with Ubuntu, a minimal installation would work reasonably well with your specs. Just pick a light window manager such as openbox, fluxbox, icewm, and then add the applications you want.

Some more links:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
[http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/](http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/)

---

