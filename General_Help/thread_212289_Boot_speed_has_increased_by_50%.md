---
title: "Boot speed has increased by 50%"
date: 2006-07-09
forum: General Help
---

### Post by ahaslam on 2006-07-09
Over the last month my boot time has gone from 1 minute, to 1 min & 30 secs.
When I timed the 1 min boot, it was shortly after my install of Dapper. Since then I have installed both xubuntu-desktop & kubuntu-desktop and then removed them (I prefer gnome, but wanted to try these). I have also created a new partition on the same drive with Gparted. I haven't manually changed any configuration files since the initial benchmark,  once booted I have no problems with anything.

Any ideas why it's now taking me 50% longer to boot? Has anyone else experienced this? All comments are welcome.

Thank you,

Tony.

---

### Post by rejser on 2006-07-09
I think there are allot of junk files left from your xubuntu-desktop install and the kubuntu-desktop install. This combined with maybe prelink could couse the time delay. 
If you install by synaptic or apt get and then uninstall it don't remove all extra installed that is necesary to make the other stuff work. Only program that keeps track of this is aptitude I belive? 
Is there any specifik part that takes longer time?

---

### Post by ahaslam on 2006-07-10
Thanks for your reply.

True, after removing the extra DE's there was a lot of stuff left over. I then used the [pure gnome guide]("http://www.psychocats.net/ubuntu/puregnome.php") to do as the title suggests.

What's 'prelink'? I've installed 'preload' to help load programs slightly faster, are they related? Could it be loading extra stuff into memory during boot?

Thank you,

Tony.

---

### Post by Shikai on 2006-07-10
Preload does increase your boot time as it loads commonly used stuff, but that's mitigated by a faster start time for programs when they're first run.

You have a choice. Either a faster boot, but it takes longer for programs to start when you first use them. Or a slower boot, but programs start faster.

---

### Post by ahaslam on 2006-07-10
Thank you for clearing that up for me, it certainly makes sense.

Does anyone know the difference between 'preload' & 'prelink'? And known advantages/disadvantages?

Thanks again,

Tony.

---

### Post by huwnet on 2006-07-10
> **Anthony Haslam said:**
> Thank you for clearing that up for me, it certainly makes sense.

Does anyone know the difference between 'preload' & 'prelink'? And known advantages/disadvantages?

Thanks again,

Tony.

preload loads parts of common programs like Firefox and Openoffice at boot.

prelink shares librarys so that less needs to load when you start certain programs.

---

### Post by ahaslam on 2006-07-10
Thank you.

---

### Post by ahaslam on 2006-08-25
I have recently de-selected preload in BUM and un-installed it, I didn't notice any difference worth a 50% slower boot.

My boot time remains at 1.5 mins, what could be slowing it down? 
Has anyone else noticed a slower boot over the months?

I hope it isn't taking a leaf out of M$'s book.

Tony.

---

### Post by sitedesign on 2006-11-16
if you want to remove all the left over files that are not needed any more then run this in a terminal:
sudo apt-get autoremove

That should remove any files that are no longer needed by the system, like the other desktop environments and extra files they installed.

---

### Post by ahaslam on 2006-11-16
> **sitedesign said:**
> if you want to remove all the left over files that are not needed any more then run this in a terminal:
sudo apt-get autoremove

That should remove any files that are no longer needed by the system, like the other desktop environments and extra files they installed.

Thanks for the advice but that's for Edgy, I'm on Dapper.
I found gtkorphan that sounds similar, it cleared some space but made it no faster. 
I've done loads of tweaking that has helped, but It's still significantly slower than a fresh install. I've tried a server install of Edgy with xfce on another partition and even that was slower than a fresh Dapper install.
Maybe something's not right with my hardware, as lightweight distro's such as Zenwalk are no quicker :-k

Tony.

---

