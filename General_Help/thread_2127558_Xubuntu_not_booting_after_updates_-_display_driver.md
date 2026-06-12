---
title: "Xubuntu not booting after updates - display driver?"
date: 2013-03-20
forum: General Help
---

### Post by kkelly77 on 2013-03-20
A friend of mine has an Asus eee PC 1015CX laptop. It was running extremely slow with W7 on it so I installed Xubuntu for them. I read on another thread there is an issue with 3rd party display drivers for this particular laptop, so I did not check the checkbox allowing 3rd party drivers. The laptop was in 800 x 600 VGA mode but my friend didn't mind this as long as she could use the laptop.

However, she has since told me that she was installing updates and when she restarts the laptop it just has a black screen and is not booting. This is what initially happened to me when I first installed Xubuntu and allowed 3rd party drivers to be installed. Somehow the driver must have been installed.

Is there a way to get back into Xubuntu and remove the recently installed updates, similar to Safe Mode in Windoze? Thanks.

---

### Post by MG&amp;TL on 2013-03-20
[LIST=1]
[*]Hold the shift key before boot, you should get to a boot menu (purple or black screen, "Ubuntu, with linux kernel x.x.x.x."). 
[*]Select 'recovery mode' for the menu item of your current kernel (if you don't know, it's the second one down), then you should get into an old-school screen. Blue and red, if I recall. 
[*]Select 'root prompt' from the list of options, then you should have a prompt. 
[*]You'll need to find out what the graphics driver package for this laptop is. Once you've found it out, move to step 5. 
[*]In your prompt, type: ```
apt-get remove *<package>*
```paying close attention to spelling, and replacing *<package>* with the name you found in step 4. 
[*]Check that you're not removing anything that looks unsafe. If you're not sure, post back here. 
[*]When you're happy, press 'y', then return, and let the uninstall run. 
[*]Reboot. Either press the power button or type 'reboot' at the prompt. 
[/LIST]

If you're lucky and it really was the driver being installed, that'll be it and you should be able to reboot back into driver-less mode. Otherwise you'll still have problems. If you've got problems with any step, post back here before continuing. Don't want to break anything else now, do we? :)

---

### Post by kkelly77 on 2013-03-20
Thanks for the advice MG&TL. I'll try that as soon as I get my hands on the laptop in question.

Here is a screen shot of the driver in question which I believe is causing the issue:

[IMG]http://i49.tinypic.com/coqag.jpg[/IMG]

Where can I find the package name for it so I can remove it in recovery mode?

---

### Post by MG&amp;TL on 2013-03-20
Hi,

After some googling, it seems to be the *cedarview-drm* package. [https://launchpad.net/ubuntu/precise/+package/cedarview-drm](https://launchpad.net/ubuntu/precise/+package/cedarview-drm)

Cheers.

---

### Post by kkelly77 on 2013-03-20
> **MG&TL said:**
> Hi,

After some googling, it seems to be the *cedarview-drm* package. [https://launchpad.net/ubuntu/precise/+package/cedarview-drm](https://launchpad.net/ubuntu/precise/+package/cedarview-drm)

Cheers.

Thanks again MG&TL :)

So my removal code will be? - 

```

apt-get remove cedarview-drm
```

---

### Post by kkelly77 on 2013-03-20
UPDATE

Just got hold of the laptop. Looks like I was given some wrong information.

The laptop is booting to the Xubuntu screen but is not booting any further.

If I go into recovery mode, is there a command to revert back to state prior to most recent updates?

---

### Post by MG&amp;TL on 2013-03-20
> **kkelly77 said:**
> Thanks again MG&TL :)

So my removal code will be? - 

```

apt-get remove cedarview-drm
```

Yup, should be. :)

No problem.

---

### Post by MG&amp;TL on 2013-03-20
> **kkelly77 said:**
> UPDATE

Just got hold of the laptop. Looks like I was given some wrong information.

The laptop is booting to the Xubuntu screen but is not booting any further.

If I go into recovery mode, is there a command to revert back to state prior to most recent updates?

Cool, this is (probably) easier then. :)

No, there isn't, unless she had a backup. However, try booting into recovery mode then hit 'continue normal boot' and see what happens. I believe recovery mode disables the splash screen so you can see what's going on.

---

### Post by kkelly77 on 2013-03-20
> **MG&TL said:**
> Cool, this is (probably) easier then. :)

No, there isn't, unless she had a backup. However, try booting into recovery mode then hit 'continue normal boot' and see what happens. I believe recovery mode disables the splash screen so you can see what's going on.

Looks like an issue with the /boot partition?

[IMG]http://i49.tinypic.com/117h2fp.jpg[/IMG]

---

### Post by MG&amp;TL on 2013-03-20
Ubuntu doesn't usually have a separate boot partition, so I'd be tempted to say filesystem corruption from hardware failure or unexpected shutdown.

Try pressing 'S' and see if you can boot ([http://ubuntuforums.org/showthread.php?t=1845757](http://ubuntuforums.org/showthread.php?t=1845757) says it'll work...). We can find out why it's doing that later.

---

### Post by kkelly77 on 2013-03-20
Tried selecting 'S' but laptop just hung there doing nothing. So I rebooted to GRUB screen and selected Previous Version. Booted (eventually!) to the desktop screen and got the following crash report

[IMG]http://i47.tinypic.com/ogw4zo.jpg[/IMG]

Would I be better installing Lubuntu as it is such a low spec machine?

---

### Post by MG&amp;TL on 2013-03-20
Well, that would explain the fact the upgrade caused it. For some reason, it seems the newer kernel has broken something to do with the /boot directory (or perhaps the act of installing it broke the filesystem). You're getting the crash report because the program (unrelated, I think) tried to access the read-only filesystem.

Have you tried the other options in recovery mode? I think the filesystem check would be pertinent under the circumstances.

Lubuntu would probably not help as this isn't a problem with performance, although a reinstall would fix this problem. Up to you really. :)

---

### Post by kkelly77 on 2013-03-22
Hey,

Just wanted to update the thread.

I opted for Previous version of Ubuntu from GRUB screen and managed to get into the desktop. Got the crash report as well as 19 updates required. I installed the updates and a restart was needed afterward. However, when I restarted the laptop, all I got was the Asus splash screen. I can't even get into the BIOS now. No key options such as F2, F8, F10 or holding down the SHIFT key are working.

I ended up taking the laptop apart and pulling out the hard drive. When I tried to start with no hard drive, it booted straight into the BIOS screen. When this occurred I took the hard drive and put it in another laptop and was able to install Lubuntu on it. But when I put the hard drive back into the original laptop the same thing happens; booting as far as the Asus splash screen and no further with no Function keys working either.

HEEEELLLLLLLPPPPPPP!!!!!!!

---

### Post by MG&amp;TL on 2013-03-22
> **kkelly77 said:**
> 
I can't even get into the BIOS now. No key options such as F2, F8, F10 or holding down the SHIFT key are working.
[...]
booting as far as the Asus splash screen and no further with no Function keys working either.

HEEEELLLLLLLPPPPPPP!!!!!!!


Uh-oh. *buntu can't touch the BIOS or other firmware. As far as it's concerned (although UEFI is a different kettle of fish as far as I can tell), the BIOS is a 'black box' that boots the thing.

So I've no idea. I'd be tempted to see what happens if you do a CMOS reset by taking the BIOS battery out for five minutes or so, then replacing it. This will reset the BIOS to defaults. On some laptops, this may be a royal pain in the rear though.

Sorry. :(

Will it boot anything other than a hard disk now?

---

### Post by kkelly77 on 2013-03-22
Put the dodgy hard drive into another laptop and booted from a Lubunutu live USB. Looks like hard drive is on it's last legs.

[IMG]http://i49.tinypic.com/rvk9ef.jpg[/IMG]

With the hard drive out of the laptop in question, I can boot off the Lubuntu live USB no problem and get into the BIOS too. I'll try a known working hard drive in the laptop so soon as I get my hands on one.

Thanks for the replies folks.

---

