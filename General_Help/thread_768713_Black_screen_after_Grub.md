---
title: "Black screen after Grub"
date: 2008-04-26
forum: General Help
---

### Post by CarnivorouZ on 2008-04-26
This is the same issue I had with 7.10
When I enable my ATI graphics card (Radeon x1650) or I install it with Envy and restart the computer.  The screen will flicker and go to a black screen immediately after the Ubuntu load screen.  I can not enable desktop effects until I enable my card.
To date, the only version of Ubuntu that I have been able to run desktop effects is Ultimate Edition 1.7
Thanks for any help,
Chase

---

### Post by CarnivorouZ on 2008-04-26
bump

---

### Post by CarnivorouZ on 2008-04-27
Any response.  Please

---

### Post by tosoth on 2008-04-27
Try to find AGP aperture size in BIOS, and set it to higher value (ie. 512MB).

---

### Post by deeminter on 2008-04-27
When I enabled the ATI accelerated drivers I also had the black screen after the reboot into Ubuntu. I followed the suggestion of increasing the AGP aperture to 512, and saved the setting and rebooted. I was able to get Compiz to work correctly.

My hardware is as follows:

AMD64 3500 single CPU
K8N Neo2 Mother board
2 gig Memory
ATI Radeon 1300 AGP
200Gig Maxtor Hard drive

Hope this helps someone.

deeminter

---

### Post by CarnivorouZ on 2008-04-27
Thanks for the tip deeminter.  Unfortunately it did not work for me.  I couldn't find AGP aperture size in BIOS and I did look all through it.  I did however find Frame Buffer Size with different values I could select and one of them was 512mb.  So I went with that, saved and enabled my graphics card but on restart it still would not pass the blank screen after the Ubuntu load screen.
I believe the answer lies in what is the difference, graphically, between say 7.10 and Ultimate Edition 1.7
Because I am having the same issue with 8.04 that I had with 7.10
I hope someone can figure this out.

---

### Post by CarnivorouZ on 2008-04-27
Went ahead and did a complete removal and fresh install of Compiz as well as my restricted drivers with Envy and still get the black screen.  Kudos to whatever developed came up with xfix, that thing is such a time-saver.

---

### Post by CarnivorouZ on 2008-04-27
bump

---

### Post by captain_frostbyte on 2008-04-27
had the same issue, and it's tied to splash.  when your grub loader comes up, edit the start line  as by default it looks like:
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=92360ebc-1779-44fc-952b-d6fde9f004ac ro quiet splash

just delete "splash" and it will work.  I've been having this problem with my PCI-E ATI cards since 6.06.  I'm sure there is a real fix, but I'm too lazy to look for it.  if you want test it, start the system in "recovery mode" then start up X with startx.  it should work fine.

to make the change permanent just edit /boot/grub/menu.lst.
Good luck

---

### Post by CarnivorouZ on 2008-04-28
Thanks for the tip, I will let you know if it works out for me as well.

---

### Post by CarnivorouZ on 2008-04-28
Unfortunately the outcome was still the same.  Only this time is went to black screen after running all the startup script instead of after the splash screen.  Thanks for the help though.
Any other ideas?

---

### Post by CarnivorouZ on 2008-04-28
So if I run compiz --replace.  The screen will flicker and then switch to white screen.  I assume this is related to whatever is the bigger problem.  Still looking for someone with a bright idea on how to fix this. Thanks

---

### Post by bpl07 on 2008-04-28
Any time I boot and get the blank screen, I reboot in recovery mode and choose reconfigure Xserver.  Envy is supposed to configure Xserver the correct way for your setup,  haven't had any issues since using it.  Sorry it didn't work out the same for you :(

---

### Post by CarnivorouZ on 2008-04-28
Your post reminded me that I had disabled xserver-xgl b/c of the lag it caused.  So I reinstalled that and ran Envy again but still with the black screen :(
Please help,
Dedicated Ubuntu Newbie

---

### Post by CarnivorouZ on 2008-04-28
bump

---

### Post by gunbladeiv on 2008-04-28
I have made a tutorial for this kind of issue, so could you please try it?
I wonder why you use envy while there is a gud restricted on ubuntu repo.

[http://blog.gunbladeiv.com/2008/04/ubuntu-ati-crash-on-hardy-upgrade.html](http://blog.gunbladeiv.com/2008/04/ubuntu-ati-crash-on-hardy-upgrade.html)

If it's helpful please let me know.  But if it's not helping you out from the black screen, then I would gladly to find another solution:guitar:

---

### Post by CarnivorouZ on 2008-04-29
Thank you for your response.  Your tutorial sounds like it's right out of my alley of problems.  I followed the directions to the letter and after running Envy my xorg automatically looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```
The only problem I ran into during the tutorial was when I ran sudo aticonfig --inital -f
in which case this happened:
```
chase@chase-linux:~$ sudo aticonfig --inital -f
aticonfig: unrecognized option `--inital'
aticonfig: parsing the command-line failed.
```
I will now reboot and let you know how it works out.

---

### Post by CarnivorouZ on 2008-04-29
Nope, no good.  Still with the black screen after the Ubuntu splash screen.  Back to default xorg config now.  Please let me know if anyone has any recommendations.  I can't be the only guy running this video card and has this problem.
Thanks,
Chase

---

### Post by Traceur-UK on 2008-04-29
I'm having this exact same problem. I'm using an ATI Radeon 9600. If I run xserver-xgl without enabling my card, everything lags. If I enable my graphics card, I get black screen. It's a lose-lose situation.

---

### Post by gunbladeiv on 2008-04-29
Have you try the driver provided in the repo instead of using envy?
I think you should give a try on the ubuntu driver for ATI.. 
I'm not using the envy method, but i use simple apt-get method which lead me to successfully configure my ATI with compiz enable work out of da box.

---

### Post by gunbladeiv on 2008-04-29
> **CarnivorouZ said:**
> Thank you for your response.  Your tutorial sounds like it's right out of my alley of problems.  I followed the directions to the letter and after running Envy my xorg automatically looks like this:


Do you use ENVY to install your cards or the apt-get method? i'm confused:confused:

---

### Post by CarnivorouZ on 2008-04-29
> **gunbladeiv said:**
> Do you use ENVY to install your cards or the apt-get method? i'm confused:confused:

I have used both Envy and System>Admin>Hardware Drivers to install the driver for my ATI card and both get the same black screen effect.  I am still somewhat new to Linux, so what script do I need to run in terminal to get the restricted drivers to load from the repo?

---

### Post by CarnivorouZ on 2008-04-30
bump

---

### Post by Kowalski_GT-R on 2008-04-30
I'm posting so everyone feels less lonely with their ATI problems :)

Hardy/Radeon X1600 here......and black screen after the boot bar fills (while the system loads up the graphics drivers, i think)

I'm not activating the proprietary drivers, and my system runs very well: multimedia ok, I have sound and Open Office is great.
Since my rig is mission critical, I'm not going to be the most active user: i'll just wait for updates to come (either form the devs or ATI) and check the forums regularly.


p.s. Envy didn't work on my PC in the past (7.10)

---

### Post by Saint Angeles on 2008-04-30
after the progress bar loads and the black screen comes up, try hitting ctrl+f1...

heres a little tutorial that seems to work for some:

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by CarnivorouZ on 2008-05-01
Thank you Saint Angeles for once I am getting somewhere with this issue.  After following your tutorial I can now get Ubuntu past the splash screen with the ATI driver running.  But now with desktop effects: When I choose normal or extra effects it will change to the white screen :confused:

thanks for the help so far

---

### Post by CarnivorouZ on 2008-05-01
Something to note: When I try to enable desktop effects or I run compiz --replace, it will go to white screen as I mentioned.  But I noticed that when I click around like an idiot on the screen I can indeed see the desktop effects working like window transitions and the animations.

---

### Post by CarnivorouZ on 2008-05-01
bump

---

### Post by CarnivorouZ on 2008-05-02
help please

---

### Post by CarnivorouZ on 2008-05-02
still looking for assistance with this if anyone can help.

---

### Post by CarnivorouZ on 2008-05-03
bump

---

### Post by CarnivorouZ on 2008-05-03
should I just give up? lol

---

### Post by shwick on 2008-05-04
I have the same problem, but there doesn't seem to be a fix for this yet... I'm hoping it gets resolved quickly.

---

