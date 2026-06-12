---
title: "nvidia driver help?"
date: 2007-10-19
forum: General Help
---

### Post by kooldino on 2007-10-19
I posted this on the [compiz forums, ]("http://forum.compiz-fusion.org/showthread.php?t=4823")but they told me that it's probably not a compiz issue...

I've had a long history of not being able to get compiz or beryl to work properly on any of my machines, regardless of hardware.

Currently, I have a machine that's running KDE on Gutsy Gibbon.  It's got an Nvidia geforce 4 mx 420.

I've tried installing both the nvidia-glx and the nvidia-glx new drivers.  After I install them, I enable them, and reboot.

That will generally result in me not booting straight into X when I reboot.  I then will have to run "sudo dpkg-reconfigure xserver-xorg" to get the thing to run.

At that point, I reboot, and I can log into KDE as normal.

But when I go to run compiz, I get...

> compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

What do I have to do to get this thing working?

---

### Post by El Cabrón on 2007-10-20
I have the same card and after I upgraded to Gutsy I am experiencing mucho problemas. 

I tried Envy but it's missing a dependency, "linux-headers-2.6.20-16". (For Gutsy?)

Nvidia gforce4 (generic) is the only driver that boots me into X without having to repeatedly going through displayconfig-gtk 

It's crippled.. screen savers cause it to crash, restarts randomly. I'm trying to find a solution.

---

### Post by Jaynix on 2007-10-20
> **El Cabrón said:**
> 
It's crippled.. screen savers cause it to crash, restarts randomly. I'm trying to find a solution.

I had the same problem with a 7900gtx in feisty. Screen savers would cause crashes and I was not able to get compiz to work.

I gave up and used windows on that machine until today. I installed gusty on it, and after enabling the restricted drivers, the screen just goes berserk. I haven't tried envy with gutsy though. I don't even know if it would work with gutsy. This just sucks. I'd really like to try compiz. Or play games...

---

### Post by kooldino on 2007-10-21
> **El Cabrón said:**
> I have the same card and after I upgraded to Gutsy I am experiencing mucho problemas. 

I tried Envy but it's missing a dependency, "linux-headers-2.6.20-16". (For Gutsy?)

What's Envy?

Did you try adding that dependency module?

> Nvidia gforce4 (generic) is the only driver that boots me into X without having to repeatedly going through displayconfig-gtk.

ah, so you didn't specify the 420?  You just manually selected Geforce 4 (generic) under the nvidia-glx driver?

Also, the error message "Checking for Xgl: not present."...how could I remedy that?

---

### Post by kooldino on 2007-10-22
Monday morning bump.

---

### Post by kooldino on 2007-10-23
This is driving me mad.  It's an NV17...a P73 card.  It's either a geforce 4 MX 420 or MX 440.  It's an AGP card.

I can't get the nvidia driver working to save my life.

---

### Post by kooldino on 2007-10-23
I just tried the nividia-glx-legacy driver, which will show the full screen Nvidia logo (with a white background) and get me a graphical login.

Once I log in, it will just show me the background that's behind the default login screen, and do nothing for a few minutes.  Eventually it reloads the login prompt.

Are there any other drivers I can try?

---

### Post by kooldino on 2007-10-23
I tried "nvidia-glx-new" as well, can't even get a login GUI when I do.  Same results as on the first post. :(

---

### Post by kooldino on 2007-10-24
Ok, so I figured it may have been a problem with the video card.  

So, I tired a Geforce 3 Ti200, and I also tried a Geforce 2 MX.  The results were the same in both.

---

### Post by ztirffritz on 2007-10-24
I have an nVidia Quatro FX something or other.  The machine will load the login screen correctly, but the desktop just fails at a white screen.  I have a twin-head set up.  It worked under Feisty just fine.  I uninstalled and re-installed Envy and uninstalled and re-installed the nVidia drivers but that didn't help either.  Anyone have a solution for the White Screen bug?  I need to use this computer, even if it is without the eye-candy.  

I know that there is a place where I can create a file that will tell it not to start Compiz, but I can't find it now.  My laptop told me during the upgrade where to create the file.

---

### Post by kooldino on 2007-10-24
Well, I got mine sorted out using the nvidia-glx driver, but I had to do a fresh install of kubuntu for it to happen.

I still have the previous install on another HDD...I'd still like to know what the issue was.

---

### Post by El Cabrón on 2007-10-24
> **kooldino said:**
> What's Envy?

Did you try adding that dependency module?

1. Envy is a Python application for installing NVIDIA drivers, effortlessly.

2. That module no longer exists in the repositories.



> **kooldino said:**
> ah, so you didn't specify the 420?  You just manually selected Geforce 4 (generic) under the nvidia-glx driver?

1. Well, there is no GeForce 420 to select.

---

