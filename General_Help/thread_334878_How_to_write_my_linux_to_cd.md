---
title: "How to write my linux to cd?"
date: 2007-01-09
forum: General Help
---

### Post by Dr Small on 2007-01-09
Hey,
I was wondering how I would write MY linux, what I have customized after the installation, with all my apps and files, to a cd or dvd as an ISO file, so all I have to do is pop in my cd or dvd and can have my entire Linux system on cd or dvd.

Just basically like the ubuntu cd that I got in the mail, only it's of MY computer.
Anyone know how to do this?

Thanks,
Dr Small

---

### Post by kebes on 2007-01-09
If you just want a CD backup of your current installation, you can boot into a LiveCD and use "partimage" to create a disk image, then burn it to a CD/DVD.

However it sounds like you want to create a "custom" LiveCD that has all your options, programs, etc. loaded. Doing this is somewhat complicated, but possible... [look here]("http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm") for one tutorial (no doubt there are others...).


One thing to note is that some LiveCD distros let you save your settings to a USB-key, so that when you boot into it next time (even if on a totally different computer), all your settings and files are retained. One I've used in the past is [Mandriva Move]("http://www.mandriva.com/en/individuals/products/move"). (There are probably others.)

---

### Post by Dr Small on 2007-01-09
I might figure it out, after I read that tuturial long enough.

---

### Post by Dr Small on 2007-01-09
Would this app do what I want?
[http://linuxappfinder.com/package/bootcd](http://linuxappfinder.com/package/bootcd)

I'm not sure if I should try it or not.
Dr Small

---

### Post by rioghal on 2007-01-09
Have you looked at Reconstructor?

From the reconstructor site:

*Reconstructor is a Live CD creator for Ubuntu Linux.*
*It uses the **Ubuntu Linux Live CD** as a base, and then allows customization of boot screens (usplash), gnome settings, and software (you can also use the chroot environment to make other changes before creating the live cd).*
*Reconstructor uses the solid Ubuntu foundation, and allows for extensive customization.  For example, create a custom Live CD with blender, inkscape, etc. included for a friend in graphics, or simply use reconstructor to re-brand your environment (wallpaper, fonts). *
[I]Reconstructor is written in python and is licensed under the GNU General Public License (GPL) 
[/I]



The Reconstructor site can be found here:
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)



There is also some info here:
[https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo](https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo)

---

