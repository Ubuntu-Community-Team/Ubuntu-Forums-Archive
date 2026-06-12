---
title: "Hangs on Light Dislay Manager"
date: 2016-01-02
forum: General Help
---

### Post by fisheye11 on 2016-01-02
My machine will NOT boot into the OS.  Instead, it hangs on the LDM.  Here's a pastebin of my failed boot:

[http://paste.ubuntu.com/14368041/](http://paste.ubuntu.com/14368041/)

Can anyone tell me what happened?

---

### Post by Dreamer Fithp Apprentice on 2016-01-02
I'm assuming "LDM" refers to lightdm. Is that correct? I suggest you tell EXACTLY what happens when you boot instead of just summarizing "it hangs on the LDM". In other words, how far do you get before there is indication of a problem and EXACTLY what text appears on the screen?
Without that, it's hard to guess. I just had a problem with lightdm-gtk-greeter that turned out to be a script I had it running at startup. You might like to look at that thread to see if it might be relevant:
[http://ubuntuforums.org/showthread.php?t=2306351](http://ubuntuforums.org/showthread.php?t=2306351)

Have you made any tweaks to any of the config files of lightdm or the greeter?

If it hangs while lightdm is doing something, that implies you got past grub, or whatever bootloader you use. Have you tried any of the safe boot or boot with earlier kernel options?

---

### Post by fisheye11 on 2016-01-03
Sorry for the lack of info....I'm still learning.  I get past GRUB, into the logo boot screen, then I get a text screen showing each program starting up.  Down the list, "Starting Light Display Manager.... and deal with any system changes..p link was shut down" comes up and the machine hangs here.  I haven't made any changes....this just happened.  What do I do?

---

### Post by Dreamer Fithp Apprentice on 2016-01-03
If those strings of "."s (elipses or something like that, I think they are called) are yours, post the full text of the messages. If that is the way they appeared on the screen you could try find the messages in the logs and post the full content, assuming they didn't originally have the dots. To do that, boot the system with something else, maybe a live disk and search some of the logs in /var/log and /var/log/lightdm/ for the original of that. It will probably be informative and might be useful. I somewhat like gnome-search-tool for that kind of task but you may have to install it in the live disk, which you do the same way you would on a regular HD based system.

But since you haven't made any mods, you don't have any tweaks to preserve, so maybe it would be easier to try this:
Once the system hangs on boot, hold down the cntrl and the alt keys and press the F-3 key.
Hopefully you'll get a tty  with a "login:" prompt. Other text may be printing to the screen. Ignore it. Type your user name. Press enter. Type your login password. Press enter. If it doesn't work the first time keep trying until you get a normal prompt. Typically it looks like this:
username@systemname:~$
Again, there may be error messages appearing on the screen. Ignore them and type:
startx
and then press the enter key.
If that brings up your normal "desktop environment", we can work from there.

If you know the package name of your greeter, open a terminal and type:
sudo apt-get purge lightdm
and press enter. It will want your password. Type it and press enter again.
When it finishes do the same thing for the greeter:
sudo apt-get purge whatever-the-greeter-package-name-is
etc.

If you aren't sure what the greeter is called, just do this instead:
sudo apt-get purge lightdm*
etc.
sudo apt-get purge unity-greeter
etc.
That should get anything you are likely to have. It may purge a few things you like but you can reinstall them later.

Assuming all that is sucessful:
sudo apt-get install lightdm lightdm-gtk-greeter
etc.

I specified lightdm-gtk-greeter because it is simple, light, it should work, I understand it, and it's what I use. If you prefer a different greeter, you can try with the appropriate package name. I think the flagship version of Ubuntu now comes with "unity-greeter". I assume that works with lightdm, but you might want to research if first, if that is what you want to use. Of course, you can just install it and at worse you won't be any worse off than you are now and will just have to try something else. 

Then try rebooting. If this work, great. If it doesn't, at least we are making what Edison called "progress".

---

### Post by fisheye11 on 2016-01-03
Turns out 15.10 didn't come with unity-greeter, so nothing there to lose.  I purged/installed lightdm and the greeter.

After the reboot, I'm now stuck in a new spot (progess nonetheless):

Its now on fsck, which i know checks for bad files and blocks.  Pressing any key doesn't help.

I've booted into the installation CD and tried to run fsck, but it comes up clean.

---

### Post by Dreamer Fithp Apprentice on 2016-01-03
EXACTLY what happens when you reboot now?

---

### Post by fisheye11 on 2016-01-05
It goes into fsck, tells me what blocks are free, and shows no signs of going forward.

---

### Post by fisheye11 on 2016-01-05
Specifically, it says:

fsck from util-linux 2.26.2
/dev/sda2: clean, 835120/30236671 files, 93743183/120945664 blocks

The cursor blinks below, and I don't see anything happening.

---

### Post by fisheye11 on 2016-01-10
Since I've stumped the crowd here, I'm just going to wipe the drive and reinstall.

---

### Post by Dreamer Fithp Apprentice on 2016-01-14
Sorry I didn't get back around sooner.  Almost sounds like the drive might have problems. Unless you have a ton of tweaks that would be hard to redo, reinstalling probably is your best bet. If you haven't already done it, and you want to tinker some more, there might be a way to reinstall grub, lightdm, and the greeter by booting from another system, like a live disk maybe, and chrooting. Not something I've done so I'm guessing, and it might come under the heading of "doing things the hard way 'cause I'm stubborn". Good luck with that.

And, btw, unless you have some real good reason to think it isn't the drive beginning to get unreliable, it would be prudent, if and when you get it working right, to back up the system (not talking about your data, presumably you already do that) as soon as you do. Restoring is easier than reinstalling. I use fsarchiver while booted from another partition myself. You can run it in the background, which makes it pretty easy.

---

