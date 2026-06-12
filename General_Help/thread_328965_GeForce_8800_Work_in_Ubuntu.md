---
title: "GeForce 8800 Work in Ubuntu?"
date: 2006-12-31
forum: General Help
---

### Post by taekwondodogoof on 2006-12-31
Does the Nvidia Geforce 8800 GTX work in Ubuntu? I just got one, and I had to change to Vesa because Nvidia drivers would crash. I've tried updating them, and doing every how-to thread I can find. I've tried reinstalling Ubuntu, but the liveCD crashes! I used to have a Nvidia GeForce 6800 and it worked fine, but when I switched everything got messed up. With the Vesa drivers, I get this wierd laggy scrolling in firefox and in file browsers, and many multimedia players don't work.
     Thanks for the help :KS

---

### Post by MetalMusicAddict on 2006-12-31
Wow. A 8800GTX. Nice. I would use the nVidia drivers right from them or install Feisty and get the drivers from the repos. I was in your position when I got my 7900GT.

---

### Post by taekwondodogoof on 2006-12-31
I'm sorry, I'm new at Ubuntu, but what's feisty?

---

### Post by taurus on 2006-12-31
Feisty Fawn is the next release, 7.04.  It's in a testing face right now so unless you want to play around with it, crashing and filing bug reports, stick with Edgy...

---

### Post by fokuslee on 2006-12-31
follow this guide from tseliot for installing nvidia-glx (proprietary driver) 

[http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)

use method 1 unless u have custom kernel

it should solve all your problems 
and yeah 8800 is a nice card.
SLI?

---

### Post by taekwondodogoof on 2006-12-31
Lol, putting two of those in SLI would be like running over a squirrel ( :(  ) then backing up over it again!

---

### Post by taekwondodogoof on 2006-12-31
Right after I installed everything it worked fine. Then, when I restarted, it came back with an error. It said warning, Nvidia kernel is 1.0-7184 and Xmodule has 1.0-9746 kernel. ALso.. the NVIDIA driver said screens found, but none have usable config.. lower Xsever said fatal server error-no screens found.
     Thanks for the help again!

---

### Post by pseudonym on 2006-12-31
> **taekwondodogoof said:**
> Lol, putting two of those in SLI would be like running over a squirrel ( :(  ) then backing up over it again!
Yeah, I imagine it'd be fantastic. For all those games that.....don't work in Linux ;)

---

### Post by taekwondodogoof on 2006-12-31
> **pseudonym said:**
> Yeah, I imagine it'd be fantastic. For all those games that.....don't work in Linux ;)

Lol... I keep windows XP on another hard driver where I play my games!! I use Ubuntu for everything else =D!

PS: Don't forget about my post two above!! That's what I need help on lol!

---

### Post by pseudonym on 2006-12-31
> **taekwondodogoof said:**
> Lol... I keep windows XP on another hard driver where I play my games!! I use Ubuntu for everything else =D!
Aah! Well, you may be interested in my little [manifesto]("http://www.ubuntuforums.org/showpost.php?p=1929486&postcount=22").

---

### Post by pseudonym on 2006-12-31
> **taekwondodogoof said:**
> Right after I installed everything it worked fine. Then, when I restarted, it came back with an error. It said warning, Nvidia kernel is 1.0-7184 and Xmodule has 1.0-9746 kernel. ALso.. the NVIDIA driver said screens found, but none have usable config.. lower Xsever said fatal server error-no screens found.
Thanks for the help again!
did you have the legacy driver installed? did you get any weird messages when you built the 9746 driver? or did you install it the 'ubuntu way'?

---

### Post by taekwondodogoof on 2006-12-31
Lol... I still love my Wintendo!! Anyways...I originally installed the driver from the one provided on their website.. then that didn't work. So I had to try it the Ubuntu terminal way provided in the guide above. It was more successful as it worked before I had to restart.

Wait... I haven't installed Xserver recently. Can you update it somehow?

---

### Post by pseudonym on 2006-12-31
> **taekwondodogoof said:**
> Lol... I still love my Wintendo!! Anyways...I originally installed the driver from the one provided on their website.. then that didn't work. So I had to try it the Ubuntu terminal way provided in the guide above. It was more successful as it worked before I had to restart.

Wait... I haven't installed Xserver recently. Can you update it somehow?
xserver-xorg will only have security fixes applied to it until the next ubuntu release. In any case, it's not where your problem lies...

I think you've got 2 versions of the nvidia driver installed on your system, according to what you wrote above. The one 'provided on their website' looks to be the 7184 version, which is an old one only used for older cards these days. Your brand spanking new 8800 is not supported by that driver, so that's why it crashed.

What you need to do is uninstall everything nvidia, then reinstall the 9746 driver. If you weren't already aware, you always need to uninstall the previous version first before you update this driver.

How you go about doing this depends on which method you used to install the 9746 version. You say 'provided in the guide above' but which method was that exactly? 1,2, or 3?....

---

### Post by taekwondodogoof on 2006-12-31
I used method 1 from the guide above

So Basically I need to uninstall everything Nvidia and just try to start fresh?

---

### Post by pseudonym on 2007-01-01
> **taekwondodogoof said:**
> I used method 1 from the guide above

So Basically I need to uninstall everything Nvidia and just try to start fresh?
Yes. For the currently installed 9746 driver you can follow the uninstall instructions for method 1 in the guide above.

Then shutdown 'X' by pressing Ctrl+Alt+F1, logging in, and typing - ```
sudo /etc/init.d/gdm stop
``` Now type ```
sudo nvidia-installer --uninstall
``` to remove the 7184 version. It will likely spit out a few messages but don't worry.

To make sure all traces of it are removed first type - ```
nano /var/log/nvidia-installer.log
``` and see if it has messages about files not being removed (you can scroll through the log using PageUp and PageDown keys).

Once you've identified what extra files need to be removed, if any, simply remove them with - ```
sudo rm filename filename
```
You should now be in a position to reinstall the 9746 driver using method 1 in the guide above. If you need to use X in the meantime you will need to temporarily re-enable the 'nv' driver in the 'Device' section of your xorg.conf.

HTH and Happy New Year! With your 8800 it's certainly off to a good start! :)

---

### Post by taekwondodogoof on 2007-01-01
I hate to be a bugger, but now when I login with Nvidia, I see the splash screen, then vertical neon green lines appear, and I can't get into console.

---

### Post by taekwondodogoof on 2007-01-01
Bump! :KS

---

### Post by jellyfisharepretty on 2007-03-11
Unfortunately, I've been stuck with using my Wintendo for 2 months now because of the problem with the NVIDIA driver (I have a 8800gts and I get those green lines when the driver loads)

How I miss Beryl... :-({|= 

Still doesn't anyone know how to fix this ?

Thanks :) 

PS nvidia just released new drivers for linux, I'll give them a try soon

---

### Post by jellyfisharepretty on 2007-03-17
Ok!  Got it working at last.

Only the official installer directly from nvidia worked for me.  Here's how I did it:

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

I accepted the license, let it compile the driver for my kernel.  The installer found the correct path to xorg and for the driver module as well.  I suspect it is using /usr/src/linux as the directory for the linux source as it didn't complain about that.

I edited /etc/default/linux-restricted-modules-common to include "nv" in the RESTRICTED_MODULES i.e. RESTRICTED_MODULES="nv" .

Rebooted, and finally no more green lines after the nvidia driver is loaded... Beryl's back baby!

Unfortunately it looks like I will have to go through this procedure every time I get a new kernel :-|

Really hopes this helps somebody.

---

