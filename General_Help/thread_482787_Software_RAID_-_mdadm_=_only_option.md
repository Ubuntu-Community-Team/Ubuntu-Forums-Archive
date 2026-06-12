---
title: "Software RAID - mdadm = only option?"
date: 2007-06-24
forum: General Help
---

### Post by BassKozz on 2007-06-24
Hello my name is BassKozz and I am a Winblowz Aholic,  But I am getting help thanks to Ubuntu, and hopefully I can make my life M$ free with some help :D

Seriously thou, I am switching to Ubuntu, and one of the features I am really looking forward to is Stable/Reliable/Efficient Software Raid,  I've been looking for a solid system to run a fast and reliable Software Raid setup on, and I was initially referred to OpenSolaris because the new ZFS file system.  But to jump from Windows to Solaris is a bit much for me, so I've decided to stick with Ubuntu (for now)...

Any idea on when linux (Ubuntu) might support ZFS, I know there are a few ongoing disputes over the subject of the different licenses on the [forums]("http://ubuntuforums.org/showthread.php?t=470533&highlight=ZFS+support") and on [Launchpad.net]("https://launchpad.net/distros/ubuntu/+spec/zfs-filesystem"), but anyone have a rough estimate on how long it might take for something like this to get developed?

Also for now, while ZFS is not an option is *mdadm* the best option for setting up Software RAID in Ubuntu? Are there any other alternatives?  Is there any documentation on what happens during a drive failure and replacement?  I'd like to get a feel for this before I jump into the deep end.

Thanks in advance,
-BassKozz

---

### Post by moshuptrail on 2007-06-24
Here's a little article that might help:
[http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html?page=1)

Explains a little of the history of RAID on Linux and provides instructions for mdamd set-up.

---

### Post by BassKozz on 2007-06-24
moshuptrail,

Thanks for the linky, google has been my friend and I've found lots of articles on the use of *mdadm*, but I am wondering if this is the only option for setting up a software raid in Ubuntu, and if not is it the BEST option?

Thanks,
-BassKozz

---

### Post by moshuptrail on 2007-06-24
It depends what you mean by "best".

If you want easy install and plenty of folks to share experiences with (support), then I think it's (mdadm) the "best" for Ubuntu.  In my brief travels I didn't come across any other software-only options except the earlier one mentioned in the article, but I'm sure you can find something. But you'll probably have to work hard to get it installed, and when you come on these boards looking for help you won't find much.  And since the developers working on Ubuntu seem to be including it in all the distros along with detect and install features, that's a good indicator to me that it's the best choice.

Good luck tho!

---

