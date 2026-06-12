---
title: "Removing an old kernel"
date: 2014-09-28
forum: General Help
---

### Post by craig10x on 2014-09-28
I noticed there is an ever-growing list of kernels on the grub menu as newer kernel updates come in on my ubuntu 14.04...
Now, if i wanted to remove a kernel, using synaptic package manager, i notice when i type in a particular kernel, it will shows exactly 4 INSTALLED files...which include the 2 header files (the alldeb and the 64 bit specific one) and then there is the image file and lastly, the "extras" file....

If i mark all 4 for complete removal, would that do it?   And then i assume when i re-boot, it will be automatically removed from the grub menu? 
Is this a safe way to do it and avoid any problems?

I was wondering if that would work as it seems to me the easiest way...i think i'd prefer using package manager over doing it with terminal commands...

Thanks in advance for all input ;)

---

### Post by blackbird34 on 2014-09-28
As far as i know, ```
sudo apt-get autoremove
``` removes all unneeded packages INCLUDING old kernels all in one go. Can"t get much easier than that.

---

### Post by craig10x on 2014-09-28
Never heard of using that command to get rid of old kernels...anyway, i would rather go a safer route and remove one at a time...don't want to take a chance on messing things up...so, i am wondering if the method i described would be efficient and safe...

---

### Post by rbmorse on 2014-09-28
What you want to do works.  Run sudo grub-update afterwards to remove unneeded entries from the GRUB boot menu.

---

### Post by d4m1r on 2014-09-29
If you would like to selectively (pick and choose) which kernels in particular you'd like to remove, all in a clean UI, I would recommend "Ubuntu Tweak Tool". You can search for it in the Ubuntu Software Centre and it may already be installed on your system by default.....

Basically, it has a "Janitor" section that displays all the in-active (old) kernels still saved on your system but not in use, and allows you to check them for removal. I would also recommend however, that you always keep 1 old kernel saved locally just in case (for a backup if anything goes wrong with the latest kernel).

---

### Post by Impavidus on 2014-09-29
Yes, uninstalling those 4 packages works and they will be removed from the grub menu. Instead of the command line with autoremove, you can also use synaptic, which wil list some old kernel packages as autoremovable. It will keep one or two old kernels as a fallback, so not all old kernels are autoremovable. There is no need to run grub-update afterwards as that is done automatically when you remove or install a kernel package, but running it anyway won't harm.

Searching in synaptic for packages with the old version numbers and purging those works too. That's what I always did on Ubuntu 6.06 through 12.04. Nowadays I use autoremove.

---

### Post by craig10x on 2014-09-29
Great suggestions guys! Also appreciate your confirming that the method i wanted to use would work fine...
I have heard of being able to do it with Ubuntu Tweak Tool but can't seem to find it in the software center, is it perhaps no longer available?

And yes, impavidus, that was the way i was going to do it (type in the number of the individual kernel i was going to remove and then have it uninstall the 4 packages together at one time for complete removal)...

I was curious though, how would you do autoremove using synaptic package manager? 

I once installed (and installed) a mainline kernel using the deb files (and gdebi) and removed it with package manager and it worked great...and as you said, you don't really need to use the update grub command as it is automatically removed from the menu...so, i just wanted to know that the method would work fine with the ubuntu installed kernels...
Also, i do realize that you should leave at LEAST 1 extra kernel (for fallback purposes)...

---

### Post by linux_dream on 2014-09-29
To remove all unused kernels, headers, images and modules: ```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge 

```
So be sure to be currently using the kernel you want to keep before typing this command.

---

### Post by craig10x on 2014-09-29
Oh, i see you can download the deb file for ubuntu tweak from their website...i guess i could do that then (surprised it isn't available on the ubuntu software center)...sounds like a neat way to do it... ;)
I was still curious about using autoremove in package manager, though...

---

### Post by Impavidus on 2014-09-29
On the lower left of synaptic, click **status**. Then in the left pane, select **installed (autoremovable)** (or something like that). It should list the same autoremovable packages as those that apt-get autoremove would remove.

---

### Post by craig10x on 2014-09-29
Thanks so much :D  Everyone has been so helpful...

---

