---
title: "[SOLVED] Black screen after installed xorg-driver-fglrx 8.3 with ATi X1950 pro"
date: 2008-04-24
forum: General Help
---

### Post by garferi on 2008-04-24
Hi!

I have downloaded and installed the final version of Hardy today.
When I enabled the xorg-driver-fglrx with the hardware-manager, after restart I got black screen with total freeze, just the reboot help.
I have an ATi X1950 PRO, 512 MB, 8x AGP.
In previous Hardy versions was the same problem. I tried many ways to install the ATi driver: Envy, official ATi driver, many trying in xorg.conf, many system reinstall, without success.
Now in a final Hardy with a new installation it's also dud.
I disabled compiz in xorg.conf, but not helped, I think it is an fglrx problem.
When Ubuntu 7.10 released I installed it and worked fine. I just enabled restricted driver, installed xserver-xgl and worked, also compiz-fusion.
In Hardy it's total craze!
I'm waiting for the possible solutions...

I attached xorg.conf, and Xorg.0.log

Thanks any help!
Bye!

---

### Post by trekkie0927 on 2008-04-26
I also have the exact same problem.
I even manually installed the official fglrx 8.4 driver, but still get a black screen accompanied by total system freeze

I have an ATI X1600 Pro 512MB, also AGP.. maybe that's the cause of the problem... AGP...

I'm pretty sure I'm not doing anything wrong with settings (like xorg.conf), since I am not a new linux user; especially since a lot of the settings are automatic nowadays.

I am not sure which log to post, but if someone point it out for me, I will gladly do it. Thanks,

---

### Post by ndale686738 on 2008-04-26
boot into recovery mode and run "envy --uninstall-all" this should restore default drivers and allow you to try another driver whether older or newer.

---

### Post by rbmorse on 2008-04-27
FGLRX seems to have a very hard time with the AGP > PCI bridge chip used in the AGP cards. I don't think there is a fix short of using either the VESA or the still not yet feature complete radeonhd open-source drivers.

---

### Post by olskar on 2008-04-27
I have this problem too, but I never had it in Gutsy. But I am using the same Atidrivers as I did in gutsy. This makes me believe it hsa something to do with Hardy. Perhaps this is the famous freezebug many people are having problems with in hardy?

---

### Post by trekkie0927 on 2008-04-28
I just tried the driver with Gutsy, and it DOES work.
So... do we just wait it out to be fixed in Hardy or do I report it or something?

---

### Post by Riptr on 2008-05-01
Bah, I get this issue too with my Sapphire ATI Radeon X1950 GT AGP 8X 256MB.

Envy fails, officials fail and to top it off - the restricted's fail too.

---

### Post by shwick on 2008-05-03
I have the same problem with Xpress 1100. If i don't fix this, i'll have to go back to Gutsy :(

---

### Post by strabes on 2008-05-03
You do not need to use xserver-xgl anymore. The new fglrx supports AIGLX. Do not use envy. Do not use the driver from the ATI website. Both cause serious problems.

For a temporary fix, you can blacklist fglrx, forcing your x server to use the mesa driver. This should allow you to get to a GUI, but you will not be able to run compiz fusion. Once you get to the black screen, hit CTRL+ALT+F1 to get to a virtual terminal. Log in, and enter the following commands.

```
echo "blacklist fglrx" | sudo tee -a /etc/modprobe.d/blacklist
sudo reboot
```

Let me know if this works at all.

---

### Post by shwick on 2008-05-03
This works for me, but it's not really nice...

---

### Post by garferi on 2008-05-03
> **strabes said:**
> You do not need to use xserver-xgl anymore. The new fglrx supports AIGLX. Do not use envy. Do not use the driver from the ATI website. Both cause serious problems.

For a temporary fix, you can blacklist fglrx, forcing your x server to use the mesa driver. This should allow you to get to a GUI, but you will not be able to run compiz fusion. Once you get to the black screen, hit CTRL+ALT+F1 to get to a virtual terminal.
Under black screen there is totaly freeze, the CTRL+ALT+F1 not responding, just the hard reboot help. Then recovery mode, root shell: ```
apt-get remove xorg-driver-fglrx
``` ```
dpkg-reconfigure -phigh xserver-xorg
``` ```
reboot
```
I always use this method to get back the GUI.

---

### Post by trekkie0927 on 2008-05-04
yeah... I don't think the problem is getting the GUI back, but really I was just wondering if there is a fix for this bug/problem. If there isn't, is there a procedure to report this officially? I mean obviously there are ppl who uses ATI cards, and not all of them are PCI-E...

And no, mesa driver is not an option, because there's no point switching if you can't use Compiz-fusion to beat Vista Aero Glass.

---

### Post by Nephilim2012 on 2008-05-08
> **trekkie0927 said:**
> yeah... I don't think the problem is getting the GUI back, but really I was just wondering if there is a fix for this bug/problem. If there isn't, is there a procedure to report this officially? I mean obviously there are ppl who uses ATI cards, and not all of them are PCI-E...

And no, mesa driver is not an option, because there's no point switching if you can't use Compiz-fusion to beat Vista Aero Glass.


Count myself amongst you. I currently have in my possession an ATI Sapphaire pro x1950 512mb AGP video card. Needless to say, at the time, the video card suited my circumstances, short of assembling an entirely new pc from scratch. Currently, not a viable option. Seeing as how I am a first time user of this particular distribution. The installation went  smooth as silk. My primary disconcerting issue at hand is this bug which manifests each time I attempt to install new ati drivers; be it proprietary or ubuntu's. As it stands now, I have one hard drive dedicated to Ubuntu8.04 that is in operative due to this happenstance.


Garferi: I have a logical suggestion for you. Have you attempted to use much the older ati drivers, such as driver 7.11? My hypothesis is this(very brief), I have observed on the windows system utilizing any catalyst driver beyond 7.3 or 7.4 for the agp version of the sapphire x1950, results in a absence of 3drendering, especially the newer 8.3 and 8.4 drivers! In short, I've scoured the internet and managed to  download the ati catalyst 7.11 driver for Linux. I am going to attempt to utilize this driver set instead, in the interim.

Against the darkness and take care,
Nephilim2012

---

### Post by garferi on 2008-07-26
Any good news with this card?
In every months I tried install the latest ATi driver on a freshly installed Ubuntu Hardy system, without success, always got black screen. Tried any driver from 8.3 to 8.7 with [Ubuntu Hardy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29")
[Here]("http://ati.cchtml.com/show_bug.cgi?id=1176") is my bugreport on ATi bugzilla page.
Thanks any idea to fix this.

---

### Post by kirsch92 on 2008-07-30
[http://ubuntuforums.org/showthread.php?t=681895](http://ubuntuforums.org/showthread.php?t=681895)

This may help.
I suggest reading through the entire post and all links for some insight.
Post #27 in particular may give some help to AGP/PCI-E bridge issues...

Hope it helps.

---

### Post by garferi on 2008-07-30
The link what you posted didn't work.
My AGP during installation was detected fine, I think isn't that the problem.
Thx!

---

### Post by kirsch92 on 2008-07-31
I tried it this morning, and it worked for me, with the x1550 AGP card.

I don't know if you read through all the posts and links but this happened to all the windows drivers for AGP cards too.  They of course got a bugfix, while we are out in the cold.

Sorry this didn't work for you, but you're on the right track.  It's certainly AGP related.  There are several other threads on AGP floating about.  I think me might be a very small percentage of users, having newer AGP cards.

I read through all the release notes from 8.3 thru 8.7 and there is no mention of this issue of course.

Good Luck

---

### Post by kirsch92 on 2008-07-31
Sorry, I misread your post.  **I have fixed the link.  It should work now.**
I thought you meant the fix didn't work.
My card was detected just fine, and ran with VESA driver, so no 3D.  It was after the install of resticted drivers that I would have the black screen lockup when X tried to start.

Then it was recovery mode time, fix X server and and boot in using the VESA driver again.

The ATI drivers can't read the AGP.  This happened to the windows drivers as well, but they got a Bugfix.  I believe it started right around 8.3 drivers.

I haven't tried 8.7 driver, but I got it to work using the 8.6 driver.
Interesting reading if you follow the links into the ATI bugzilla.

---

### Post by SpaTule on 2008-08-07
hi all,

I join you because i have the same problem on lenny 2.6.25-2. A lots of people and distrib are concerned, look this [Google Search]("http://www.google.fr/search?hl=fr&client=firefox-a&rls=org.mozilla:fr:official&q=black+screen+fglrx+ati+1950&start=30&sa=N") for example. I think that it's caused by the AGP-PCI bridge on those kind of cards because i have encoutered same problem on Windows System with catalyst >7.11. After lots of research, i have found [this trick]("http://www.linuxmint.com/forum/viewtopic.php?t=6317") which seems very interesting. I ve to wait this evening to test, so i invite you to test with me.


Perhaps there's hope for us :confused:

---

### Post by SpaTule on 2008-08-08
Solved for me ! :tongue:

But I didn't follow my previous method. 

I've just change the Agp texture Size in BIOS to 128Mo. It works with 32, and 64 too but not with 256Mo. (My card is a PowerColor 1950 pro AGP 512Mo)

And I ve edited my kernel options in menu.lst like this :

```
title		Debian GNU/Linux, kernel 2.6.25-2-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.25-2-686 root=UUID=9abeaf31-f7dd-4db1-bf38-79601a8a6ff6 ro quiet [COLOR="Red"]**vmem=512**[/COLOR]
initrd		/boot/initrd.img-2.6.25-2-686
```

And xorg.conf

```
Section	"ServerFlags"
	Option "AIGLX" "on"
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "XVideo" "off"
EndSection

```

*Option	    "XVideo" "off"*  otherwise video don't work with compiz-fusion


I use 8.50.3v for fglrx driver. It's the lenny repository version

---

### Post by garferi on 2008-10-18
ATi driver version 8.10 sooolved the problem on my Ubuntu Hardy Heron 8.04.1 system! :) 6 months needed to solve this, lol :D
Download it from [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run").
Put it to your home folder and copy the code to the terminal, than follow the instructions of the graphical installer.
```
sudo sh ati-driver-installer-8-10-x86.x86_64.run
```
After the installation paste these to terminal:
```
sudo aticonfig --initial -f
```
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

Restart your computer.

The newest driver in every month is [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").
I also have Compiz-Fusion working, and about 4000 FPS in glxgears. :)
Now I have just one problem, the videos are blinking in the players. I have waiting for the solutions...
Thx!

Good luck All!

---

### Post by ToXicSham on 2008-10-19
This update finally solved my X1600 AGP black screen issue too...
Thanks for the advice!

---

### Post by pullasorsa on 2009-08-19
Hi guys,

I'm running Jaunty and had the same problem. The screen totaly freezed up and couldn't even enter the console with CTRL+ALT+F1. The most worrying thing is that Ubuntu automatically installed this faulty package and I just tried adding software from the menu Application --> Add/Remove software. I managed to locate the problem with the help of another thread, a recovery boot and /var/log/dpkg.log. The packege was recently installed and looked suspicious. Once it was removed the system worked like a charm again.

I'm a CS student so I have some understanding of how the system works which propably helped in fixing the problem. What I'm worried about if some new Ubuntu-user can hang his/her system by just adding some completely innocent looking (I think..) applications thru Application-->Add/Remove Software, that might be the end of that persons relationship with Linux and Ubuntu all together. I think this is a really serious issue that should be addressed.  The problems with *xorg-driver-fglrx* seem to be well documented so I won't bother posting a detailed error report. 

- Antti

---

