---
title: "Redirect /tmp to /home/user/tmp?"
date: 2007-04-13
forum: General Help
---

### Post by thayerw on 2007-04-13
I seem to recall reading someone's blog that, because their /home partition was the largest on their hard drive, they redirected /tmp to a directory within /home.  Can anyone offer some advice on how exactly that's done?

I have a root of 8 GB and a /home of about 85GB.  I would simply like to have large caching files (such as ISO burning, etc) dumped onto the /home partition instead of trying to squeeze it onto the smaller partition.

Is it just a matter of a symbolic link from one dir to another?

Thanks in advance!

Thayer

*EDIT*

Resolved... see thread #4 for answer.  Thanks!

---

### Post by rai4shu2 on 2007-04-13
Something like this?

sudo -i
mkdir /home/tmp
chmod 777 /home/tmp
ln -s /home/tmp /tmp

---

### Post by kerry_s on 2007-04-13
Bad idea. /tmp is actually in ram, so on reboots it's all cleaned out, if you try and link it your just going to get a tmp file with all the stuff for that session, but /tmp will return to ram on next boot.

---

### Post by thayerw on 2007-05-04
In case anyone else stumbles onto this thread, I did find a solution and it's surprisingly easy.  Open a terminal and type:

```
sudo mv /tmp /home/tmp
sudo ln -s /home/tmp /tmp
```

Reboot and you're good to go.  Of course, you can substitute any other partition in place of /home.  It's just that in my case, my root partition is only 8 GB and my /home is 80+ GB.  Now I have plenty of free space for caching ISO's etc.

Cheers!

---

### Post by boobis on 2007-05-04
> **kerry_s said:**
> Bad idea. /tmp is actually in ram, so on reboots it's all cleaned out, if you try and link it your just going to get a tmp file with all the stuff for that session, but /tmp will return to ram on next boot.

I know this used to be the case on Solaris (and might still be) but is this really the way Ubuntu works? Shouldn't you see a special entry using 'df' or something?

---

### Post by thayerw on 2007-05-04
I believe kerry_s was mistaken, because the method I posted is working great for me. I stumbled onto it here:

[http://ezine.daemonnews.org/200212/symlink.html](http://ezine.daemonnews.org/200212/symlink.html)

---

