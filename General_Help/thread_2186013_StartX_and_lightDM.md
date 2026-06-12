---
title: "StartX and lightDM"
date: 2013-11-05
forum: General Help
---

### Post by ibjsb4 on 2013-11-05
I recently did a fresh install using startx instead of the lightdm package, so no DM installed. I had expected this to speed up the boot process, but no.  I see very very little speed improvement.  I have a script installed to auto-start startx at boot.  It then goes to a login screen.

I just find this odd or did I expect too much?

---

### Post by Bashing-om on 2013-11-05
ibjsb4; Hello !

Do not know what I can say.

I boot up in less than 5 seconds, no DM. I have xfce4 as my desktop user interface and start "X" from the config file ~/.xinitrc.
```

exec startxfce4 --with-ck-launch > /home/sysop/errors-boot.txt 2>&1

```
To start the GUI session , the command :
```

startx

```works great or me.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2013-11-07
> **Bashing-om said:**
> I boot up in less than 5 seconds, no DM.

Hi Bashing

I would like to achieve that.  I am in the 12 to 15 second range.  Could be just asking for too much.

When I find things that work sweet on this older dual core desktop, I incorporate that into my newer laptop (which boots in <10 seconds).

You run startx.  Anyway to dress up the tty screen at boot?  When I boot, I go to a tty login screen with text setting in the top left corned of my screen (uses full screen).  I would be nice if it pop up in the middle of the screen.

Thanks for the input :)

---

### Post by Bashing-om on 2013-11-07
ibjsb4;

I also run an old dual core ( AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ ) desktop, on a scary obsolete Abit motherboard.
My "working" every-day use install is from a minimal install, xfce4 for the DE and only added what applications I do indeed want.
The only eye candy I have is grub's boot screen, and that only as an added thought in configuring boot options to control my booting kernels (presently with 4 'buntu installs in this box). This "working" install is much faster in all respects to any of the other installs. - Now if I can just get over the acquired habit of slamming my cursor against the left edge of the screen! - 

Dressing up the TTY1 terminal, That one I can not address directly. It is after all a terminal. Now that is not to say we could not load a background image, set the terminal to be transparent and play with some pretty colors for the text. I bet though that would slow the boot down to a crawl, Having to wait for the processes to load to even find the image for the background, much less the application starting up to apply that image would knock a big hole in boot time ! However, I think I have seen documentation where grub can do that !

Faster  is better,


Personally, I value functionality over looks and I want it as simple as my simple little mind can conceive of. However, if you want to pursue setting a pretty background, heh I am your man - will be happy to assist.

[INDENT][INDENT]it's ubuntu, all things are possible
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2013-11-08
> I bet though that would slow the boot down to a crawl, Having to wait for the processes to load to even find the image for the background, much less the application starting up to apply that image would knock a big hole in boot time ! However, I think I have seen documentation where grub can do that !

Nope, I am not for slowing anything down, faster is better :)  Just would like the sign-in in the middle of the screen at boot, nothing more.  I will have a look at grub docs and console configure.

I have startx running on my laptop, but lightdm is still installed.  I think if I remove lightdm, that could speed up boot or is that another pipe dream.

> My "working" every-day use install is from a minimal install, xfce4 for the DE and only added what applications I do indeed want.

That sounds fast.  I did similar by installing only fallback and metacity with the mini iso.

> However, if you want to pursue setting a pretty background, heh I am your man - will be happy to assist.

I am themed (metacity) and happy with what I have.  But I will take a rain check on that offer :)

---

### Post by Bashing-om on 2013-11-08
ibjsb4; Good morning !

Lightdm; In my opinion, a resource hog because of all it drives. It sure makes for a nice desk top if one is in to all the bells and whistles, If you do not use it, it can be removed but in all honesty I do not know what the effects would be if there is no other DM installed to takes it's place in a standard install. Just how deep lightdm is ingrained into the operating system I truly do not know. I recon I could risk trashing  my test install and for sure find out ! Be a great incentive to burn a liveCD (upgraded this one from on-line, testing to see how it went [only small problems]).

In theory one could:
Stop LightDM
Uninstall LightDM  and an alternate installed DM is supposed to replace it after reboot.
Edit /etc/X11/default-display-manager and set it to /usr/sbin/<DM> - If one is using a Desktop Manager.

But, but, but, What happens with no manger in place ? I am not familiar enough with the deep inner workings at this time to hazard a guess as to what would result. ~/.xinitrc to the rescue ? -- Hey That Is My Guess !-

[INDENT][INDENT]it is it is, a process of learning
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2013-11-09
Hay Bashing

Well, I played around with grub and console configure settings and have not hit on a 'center of the screen' answer yet.

> Lightdm; In my opinion, a resource hog because of all it drives.

So I thought, thus my changing to an Xorg system and then to just xserver-xorg.  The download breaks down like this on a fresh install:

Lightdm - 300MB download - replace with:
Xorg - 120 MB - which I have replaced with:
Xserver - 80MB

> ~/.xinitrc to the rescue ?

Exactly.  Thats the way I am set up.

Could it be that my cpu (core2@2.4) is just fast enough for me to not see a bigger improvement in boot speed?

I also think I have kicked this thread around long enough and its time to put it to rest.  I think its time to pursue other channels.

Thanks for the input :)

---

