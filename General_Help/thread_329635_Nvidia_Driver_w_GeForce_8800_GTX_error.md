---
title: "Nvidia Driver w/ GeForce 8800 GTX error"
date: 2007-01-01
forum: General Help
---

### Post by taekwondodogoof on 2007-01-01
Hi,
I've had to use the Nvidia driver because I've gotten the Geforce 8800 GTX. None of the other drivers work. However, when I boot Ubuntu, the Nvidia Splash Screen appears then vertical green lines appear, and I can't get into console. Vesa currently is usable, but has many graphical errors. Does anyone know how I can fix the Nvidia driver issue? I've downloaded the newest one using [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html) method 1.
Thanks for the help!! :-D

---

### Post by Zer0Nin3r on 2007-01-02
I'm getting the green lines deal as well.  (GeForce 7900GS)  I believe it has to do with the graphics card, but I'm stuck on where to start.  Been scouring the threads for sometime now.

---

### Post by spockrock on 2007-01-02
> **taekwondodogoof said:**
> Hi,
I've had to use the Nvidia driver because I've gotten the Geforce 8800 GTX. None of the other drivers work. However, when I boot Ubuntu, the Nvidia Splash Screen appears then vertical green lines appear, and I can't get into console. Vesa currently is usable, but has many graphical errors. Does anyone know how I can fix the Nvidia driver issue? I've downloaded the newest one using [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html) method 1.
Thanks for the help!! :-D

ok method one will not work, on ubuntu and you video card as of yet....... I have not seen anyone package and create a deb for the version you need, for the 8800.  You need to go to the nvidia site grab the latest linux installer. That driver has support for the 8800 cards.

ok never mind it seems tseliot has packaged that driver, you can go here and add the appriopriate repo
[http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

> **Zer0Nin3r said:**
> I'm getting the green lines deal as well.  (GeForce 7900GS)  I believe it has to do with the graphics card, but I'm stuck on where to start.  Been scouring the threads for sometime now.

I dunno which nvidia linux driver added 7900 GS support but I believe tseliots repostitory should have the right driver.

[http://albertomilone.com](http://albertomilone.com)

---

### Post by taekwondodogoof on 2007-01-02
I made sure I was using those reposotories and I already was, but I went back and uninstalled all the NVIDIA drivers and reinstalled again, and I'm having the same problem, vertical green lines after the splash screen.

---

### Post by spockrock on 2007-01-02
can I see your xorg.conf ??

did your run 'sudo nvidia-xconfig' after installing nvidia-glx???

---

### Post by Azakus on 2007-01-02
Ubuntu Repos for the latest Nvidia drivers (1.0-9629)
_AMD64:_
deb [http://ubuntu.lupine.me.uk/](http://ubuntu.lupine.me.uk/) edgy lrm-amd64

_i386_
{Looks like this one went down recently, looking for another}

Then just install the newer nvidia-glx.

---

### Post by gandalf027 on 2007-01-02
Thanks Azakus. But that driver seems to be a bit older then the 9746.

I too have a 8800gtx that i cannot install with all the examples given here.
I tried instaling the 9746 through alberto repos but withour sucess. After the Ubuntu splash screen i get a few white dots with a black screen.

I use ubuntu 64b primarly to fold, so i am using the vesa driver till we got a driver that works.

---

### Post by taekwondodogoof on 2007-01-03
So does anyone have the 8800 GTX working on Ubuntu?

---

### Post by gandalf027 on 2007-01-03
Doesn't seem like it.
Maybe we have to wait for feisty :(

---

### Post by taekwondodogoof on 2007-01-03
If I'm not mistaken, Feisty is being released in April, correct? What would they change about Feisty for it to support the 8800 that they could update in Edgy?

---

### Post by Azakus on 2007-01-03
Ubuntu does a freeze on all offical programs before the release. Edgy has a version freeze on nvidia-glx to the version that was official before release. Feisty will have an upgraded version of the drivers (probably with 8800 support) by its ship date.

---

### Post by pseudonym on 2007-01-03
Hi, according to the [nvidia website]("http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html") the 8800 is supported in the 9746 release of the driver. Packaging the driver shouldn't change that fact.

If you're still having trouble you could use [method 2]("http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2") in tseliot's guide with the installer from nvidia.com . Or if you're feeling adventurous you could [build your own kernel]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel") and use method 2.

I'm using the nvidia installer method on a hand-compiled kernel and my 7950 GT is working fine. Support for this card was added only very recently, too. :)

---

### Post by gandalf027 on 2007-01-04
I've tried instaling it with the alternate cd of ubuntu withi no avail.
I will try method 2 then and see if i can do it.

---

### Post by gandalf027 on 2007-01-04
Tried the second method, and it was going well until the instalation of the driver .. with the code given by the method the installer starts the verification of the package and then stops .. bah.

---

### Post by pseudonym on 2007-01-04
> **gandalf027 said:**
> Tried the second method, and it was going well until the instalation of the driver .. with the code given by the method the installer starts the verification of the package and then stops .. bah.
Are you then returned to a prompt? You could try leaving out the '-s' switch, which means 'silent'. That way you will get more terminal output which may tell you what's going on...

---

### Post by gandalf027 on 2007-01-04
Thanks pseudonym, it worked :)

But once again a new problem appeared.
This one ..[[IMG]http://img472.imageshack.us/img472/7105/dsc00042fe1.th.jpg[/IMG]](http://img472.imageshack.us/my.php?image=dsc00042fe1.jpg)
And i went forward, but after a restart X gives me an error of the nvidia module not found, i presume it's because of this error.

I then edited xorg.conf and changed to vesa. Reboot and it worked 1280x1024 very slow, but for now it gives me what i want .. folding.

It even gets the nvidia control panel .. but not working.
[[IMG]http://img469.imageshack.us/img469/8214/dsc00043xu1.th.jpg[/IMG]](http://img469.imageshack.us/my.php?image=dsc00043xu1.jpg)

Any more sugestions? 

Thanks

---

### Post by taekwondodogoof on 2007-01-07
OMG!! I got it to work!! I used method two from Albertomiles guide and it worked finally! I don't know what happened differently, but it worked! And sorry Gandalf... just keep trying.. I've been for about 2 weeks and I guess it paid off lol!! :-D

---

### Post by gandalf027 on 2007-01-07
You didn't get the error i got? The one in the first photo?

Thanks

---

### Post by regged on 2007-02-07
Hi,

I've got a Geforce 8800 and to get it working I had to remove splash and add noframebuffer to the kernel boot line in /boot/grub/menu.1st. You can also do this manually by intervening at boot time and manually editing the boot command, press e at the boot menu. This allowed me to use the console, otherwise switching to the console just gave me a blank screen - no Xwindows, no console.

Once the console was usable i changed the xorg.conf to use vesa instead of nv, once that was done i installed the nvidia drivers and Beryl.

Hope this helps

Regged

---

### Post by jellyfisharepretty on 2007-02-13
Hi Gandalf,

I have a 8800 card and I've followed pretty much the same path as you.  Can't get it to work with the NVIDIA drivers, I get those green lines.  And that's using the regular deb package method or method 2 (driver package directly from nvidia).

That screenshot you took isn't actually an error, but a warning from nvidia's intaller saying it doesn't know in what directory to put the driver module.

Upon rebooting, X gives an error saying that it can't find the module, because it's not in the directory it's supposed to be.

Unfortunately, I don't know how to fix this.

Anyone ?

I'd really like to get ubuntu working again on nvidia, it's not fully usable the way it is.

---

### Post by eyelessfade on 2007-02-14
It is a bit werd that feisty only ships with 1.0.9631 (4 des 2006) against 1.0.9746 (21 des 2006) when it is shiping with kernel 2.6.20 (4 feb 2007), not that I can use it since for some reason *-generic don't boot on my computer :/

---

### Post by jellyfisharepretty on 2007-03-17
Gandalf, if this is still not working for you, you might want to try this.  Basically, it's what you tried before, but without specifying an x-prefix to the nvidia installer.

I had the very same problem with a 8800gts but finally got it to work.

Here's how I did it:

Removed the nvidia-glx ubuntu package:
[FONT="Courier New"]sudo apt-get --purge nvidia-glx[/FONT]

Used uname -r to know what kernel I'm using (or just look at the grub prompt)
I'm using the linux-2.6.11-generic kernel, so I installed the proper linux kernel source :
[FONT="Courier New"]uname -r
sudo apt-get install linux-headers-2.6.11-generic[/FONT]

Then I made sure the "linux" symbolic link in /usr/src pointed to /usr/src/linux-headers-2.6.17.11-generic :
[FONT="Courier New"]sudo rm /usr/src/linux
sudo ln -s /usr/src/linux-headers-2.6.17.11-generic[/FONT]

then I executed the nvidia installer :
[FONT="Courier New"]sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run[/FONT]

I accepted the license, let it compile the driver for my kernel. The installer found the correct path to xorg and for the driver module as well. I suspect it is using /usr/src/linux as the directory for the linux source as it didn't complain about that.

I edited /etc/default/linux-restricted-modules-common to include "nv" in the RESTRICTED_MODULES i.e. RESTRICTED_MODULES="nv" .

Rebooted, and finally no more green lines after the nvidia driver is loaded...

Unfortunately it looks like I will have to go through this procedure every time I get a new kernel

---

