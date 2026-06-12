---
title: "Repair system -  fglrx driver"
date: 2014-05-19
forum: General Help
---

### Post by eduardoflsantos on 2014-05-19
Hi,

I was having trouble to install my proprietary graphic driver in Ubuntu 14.04.

This is usually my problem and how to fix it:
[http://amitks.github.io/blog/2013/04/06/ati-radeon-4330-configuration-ubuntu-12-dot-10/](http://amitks.github.io/blog/2013/04/06/ati-radeon-4330-configuration-ubuntu-12-dot-10/)
My card is a ATI Mobility Radeon HD 4330.
But this ppa was no longer working, so I needed to get fglrx somewhere else.

So, someone recomended me to follow this [guide]("http://www.edivaldobrito.com.br/como-instalar-os-ultimos-drivers-da-nvidia-ou-ati-no-ubuntu-e-derivados/") (in portuguese). Its a different ppa, and I did install fglrx with a simple command
```
sudo apt-get install fglrx
```


But I screwed it up, don-t know why.

After the reboot, I could reach the login form and login, but no further. The screen resolution was different, and I only get the background image and the cursor, nothing else, not even the terminal via ctrl alt t. My instalation its useless at the moment, Im running a live version from a pen.

So, how can I reverse this simple command ```
sudo apt-get install fglrx
```
If I can-t get to terminal?

Thanks

---

### Post by Bashing-om on 2014-05-19
eduardoflsantos; Hello,

Be aware that downgrading the Xserver version is not a supported alternative on the forum. But, let's get you squared away.
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


At the login screen do key combo ctl+alt+F1 to access a console. Login -> username and pass word

Terminal commands:
To remove the FGLRX components and install the Open Source graphics driver:
Try this:
Make sure you don't see lines "blacklist radeon" with this command:
```

grep -ri nouveau /etc/modprobe*
This one is OK: "/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb"

```
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u

```
Then reboot your system and when it comes up it will be running with Open Source radeon.

[INDENT][INDENT][INDENT]workie great, last long time
[/INDENT][/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2014-05-19
nouveau is for nvidia cards. You meant 'xserver-xorg-video-radeon'

---

### Post by eduardoflsantos on 2014-05-19
Hi Bashing. 

Glad to see they gave you Ubuntu membership. Last time I was here you were the one to help me and you were applying for it :P Well deserved, nice to see how you keep sharing your knowledge and helping people! (and the problem was about some damn graphic card too! xD)



Before I saw your message, I manage to unninstall gflrx via recovery mode / root. So, I got acess to my system again. \o/

But may I ask you to put some context in all of this? because I'm kinda lost... I don't know much about this graphic / drivers thing. All I see is commands, without quite understanding what is this all about.
My main problem was that the AMD driver for this graphic did not support Xorg (no idea what is that xD), and someone suggested to downgrade Xorg. This was in Ubuntu 12.04. 
And now, with the new Ubuntu LTS, I faced the same problem. Is this a good or bad alternative? Is there another way?

So, given that I uninstalled gflrx, am I not automatically using the open source driver now? If so, which of those commands should I use, and for what? 
And what is nouveau, google seems to say it's a Nvidia thing, not AMD?

Sorry, I look like a 6 y.o. with all the questions :P

Edit:[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") I replied before seeing [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") answer. Seems I was right xD

---

### Post by Bashing-om on 2014-05-19
@ Temüjin; Thanks as always for having my back. My posting corrected.

@ eduardoflsantos; I appreciate the congrats, things still have a "orange" glow !  Regret the error I did so make - yeah we be talking ATI here, not Nvidia !
As to what we are doing:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

Now the why to go back to the current X-server:
Unfortunately, the link you used to install the proprietary driver seems to be popping up in every thread where folks want to get AMD restricted drivers working with their HD 2x/3x/4x-series chipsets.

Problem being that people don't read through the thread to notice that it requires downgrading your X-server to an older version.
This is trading short-term gains resulting from AMD driver installation to long-term risks of system corruption due to messing around with the X-server.
This is very likely to cause serious complications down the road as other updates come through.

You are trading a short-term improvements for serious long-term risks of system damage.

So the bottom line is: use the Open Source driver with your card.

[INDENT]whatcha recon now
[/INDENT]

---

### Post by eduardoflsantos on 2014-06-01
Hi Bashing!


Thanks so much! You didn't need to explain every single command, just give an idea of what we were doing and -most importantly- why.

I'm kinda sad I can't use the proprietary drivers, they achieve better performance :( . But that's AMD fault...

Anyway, I followed your wise words and steps to get things rights again. Once again, thank you. Take care!

---

### Post by Bashing-om on 2014-06-01
eduardoflsantos; Hey, Great !

Pleased it worked out for ya.
Situation could be worse, at least there is a driver available that does get you up and running.
(there are hardwares out there that has no - to very limited - support )

we just keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT]

---

