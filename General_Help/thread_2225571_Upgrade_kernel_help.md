---
title: "Upgrade kernel help"
date: 2014-05-22
forum: General Help
---

### Post by arshb on 2014-05-22
Hey guys, first time messing with the kernel.  I know it's not recommended for noobs but I want to learn, so why not learn when it'll actually be beneficial for my laptop?


I've installed Ubuntu 14.04 and everything has worked out of the box, no additional drivers originally required.  So I'm confused as to why exactly something gets messed up when I upgrade the kernel?  Here's what I've done:

downloaded linux-image-3.13.0-27-generic_amd64, linux-headers-3.13.0-27-generic_amd64 and linux-headers-3.13.0-27_3.13.0-27.49_all.deb
cd to Downloads
sudo dpkg -i linux*3.13*.deb

and then reboot into the correct kernel but I lose wi-fi.  So I just use grub to get back to the old kernel and alls well.  I've searched and seems like I may need to learn to use DKMS?  If so, I will need further help :D.

This is on the Dell XPS 13, Haswell model.  Not the Developer edition, but instead a clean install single boot of Ubuntu 14.04.

---

### Post by Bucky Ball on 2014-05-22
Please provide the link that you downloaded the .debs from. Cheers. And by all means, experiment! You have a working kernel to fall back on so all good. ;)

FYI: [http://ubuntuforums.org/showthread.php?t=2225577](http://ubuntuforums.org/showthread.php?t=2225577)

---

### Post by arshb on 2014-05-22
Thanks, I got it from here.  [http://people.canonical.com/~acelan/bugs/lp1305522/20140515/](http://people.canonical.com/~acelan/bugs/lp1305522/20140515/)

Here's a quick question, if this one that I posted has the proper synaptic drivers for i2c touchpads, will the one you posted have it as well?  Since that one is a higher kernel version is this safe to assume?

And also, how can I remove the kernels that I install if they don't work properly so I don't have to boot into grub each time?

edit:

Tried the 3.15 RC and the touchpad fix was not included in that one, which makes sense since these are all unnoficial test kernel upgrades I assume.  I redownloaded the kernel .deb files I previously tried, and also got the extras one as well, and it worked this time.

And another sidenote, I learned how to delete a kernel but somehow deleted both 3.13 kernels even though I specified 3.13.0-27, maybe I can't be that specific?  Oh well everything works now :D.  Thanks Bucky.

---

### Post by Bucky Ball on 2014-05-22
All good and glad to see you're getting somewhere. I usually use Synaptic Package Manager to delete kernels. Just look 'em up and remove. ;)

---

