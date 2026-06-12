---
title: "Handcapped adult users"
date: 2020-09-25
forum: General Help
---

### Post by az64x on 2020-09-25
I am a volunteer for a non profit center that cares for 120 mentally handicapped adults.  
The center has asked me to setup a 6 computer lab for them.

 I am using donated PCs.  I would reformat computer (replace partition) and use Lununtu 20.  The normal user ID can only use the browser, and the  word processor.  They can only see or save to their Documents directory, or to a USB drive.  I want to completely lock them down..   

 Naturally I will first setup an ID for the admin when I install Lununtu.

 I will then setup a locked down user called Angels.

 When Angels ID logs in it will first run a script automatically to erase everything in their documents directory

 We tried Windows, but they end up with many virus files or malware and in just a week or two, the machine is not usable.  

*_**Can anyone help me?????**_*

---

### Post by grahammechanical on 2020-09-25
I have a strong idea that with Ubuntu and all its flavours a non-admin user will be able to load all the applications that have been installed. So, I suggest you think about removing (uninstalling) those applications you do not wish the non-admin user to have access to. And remove the Software Centre as well. Or, consider installing a Ubuntu mini ISO image.

This will allow you to select which desktop environment you want and limit the applications installed to those you chose and you do this during the installation of Ubuntu mini ISO image.

[https://wiki.ubuntu.com/Minimal](https://wiki.ubuntu.com/Minimal)

You will have to boot the computer in legacy mode and not UEFI mode. Which should not be a problem as you will not be running Microsoft Windows on these machines.

[URL="https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"]https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall
[/URL]
If you intend to do all your admin tasks through the command line then you can remove the file manager.

Is this not at odds

> They can only see or save to their Documents directory,

with this?

> When Angels ID logs in it will first run a script automatically to erase everything in their documents directory


You know these people better than  I. Are they forgetful?

Regards

---

### Post by HermanAB on 2020-09-26
That is what the Guest Account is for.

Enable the Guest account.  You don't need to do anything else.

---

### Post by az64x on 2020-09-26
So just use the guest account.

Wow that is simple

THANKS!!!!

---

