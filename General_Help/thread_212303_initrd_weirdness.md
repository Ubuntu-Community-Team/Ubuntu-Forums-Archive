---
title: "initrd weirdness"
date: 2006-07-09
forum: General Help
---

### Post by v4169sgr on 2006-07-09
Couple of days ago, my kubuntu install suddenly started having problems at boot time. It could not mount /dev/sda1 and complained that /sbin/init could not be found on the target filesystem. Of course this meant that the computer could not be booted, even though grub worked.

I'll cut out a lot of fiddling around with the grub menu, the live install CD for LTS, mkinitramfs etc, and cut to the chase.

I made it all work again by [in essence] doing the following:

cp initrd.img-2.6.15-25-386 initrd.img-2.6.15-25-386.07July2006
rm initrd.img-2.6.15-25-386
cp initrd.img-2.6.15-25-386.07July2006 initrd.img-2.6.15-25-386

At which point I was happy but dumbfounded. Great, it works again, but why? Of course it is a worry if it happens again and this little trick doesn't work again ...

---

### Post by mlind on 2006-07-09
What you're basically doing there is copying the same file back again?
I don't know how it could have solved your issues..

You can make completely new initrd image using initrd tools, but I think the problem is something else here. Any messages on /var/log/messages about this behaviour?

---

### Post by v4169sgr on 2006-07-10
I wish ... :razz: 

Actually I completely agree, this should not make a difference. The fact that it does suggests I am missing something.

What I was doing was this:

* Booted up using the liveCD, mounted /dev/sda1 to /mnt, chrooted to /mnt/, copied away the existing initrd file, and ran mkinitramfs;

* Then unmounted, power cycled etc, and tried booting up, which failed due to something I didn't understand about write access to something in /lib/modules;

* Power cycled again [lots of these that evening:-({|= ], booted back into the liveCD, mounted, removed the offending file, copied back the original, unmounted, and rebooted.

And everything just worked - talk about weird.

The thing that worries me is that since I don't understand what caused this error, what do I do when this happens again??

---

