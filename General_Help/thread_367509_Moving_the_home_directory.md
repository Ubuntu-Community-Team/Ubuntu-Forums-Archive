---
title: "Moving the home directory?"
date: 2007-02-22
forum: General Help
---

### Post by bone2006 on 2007-02-22
I've seen tutorials and people who suggest putting the home directory on a partition.   I looked into my home folder and there really isn't much there, except a few folders, one being the desktop folder and a few other folders.  My question is if I'm moving from windows to linux, would the home directory be compared to my documents folder in windows?

---

### Post by louis_nichols on 2007-02-22
The home directory can be compared to My Documents in windows but it's much more than. Apart from those few files and directories you see there, there are many others that are hidden. Those will store settings for each application that you've even run. Unlike in windows, a user doesn't have write access to another one's home folder, unless explicitly given, so there's a plus of confidentiality. Another advantage is that, since each application can only store settings in the user's home folder, each user can personalize everything about the Linux experience the way they want. This is very different from windows, which has the bad habit of storing many settings and files in common places for all users.

---

### Post by bone2006 on 2007-02-22
I'm a little bit confused though.
Say I installed a lot of programs and I have the home directory on another partition.  If I reformatted the main partition that the OS is on, then installed the OS back on the partition and some applications I didn't reinstall, would that mean I would have a lot of hidden data there with settings about applications that I may not even be using?

Do the majority of linux users who have been around awhile place their home in another partition?

---

### Post by louis_nichols on 2007-02-22
Yes, the majority do place the home partition on a separate partition, precisely because you can reinstall the system and keep all personalised user settings. The amount of data taken by settings is trully negligible.

That hidden data is not unaccessible, anyway, so you can easily delete it if you really want. I think it's better than personalising all your desktop every time you want to reinstall. Reinstalling is trully a rare necessity anyways, in Linux, compared to windows. Keep in mind that these settings are the same irrespective of the distro you use (with very few exceptions). So it is even possible for example to have 2 instances of Linux installed (say, 2 different distros you want to try) and have the exact same desktop and settings for all apps in each of them, by mounting the same partition as home in both.

---

### Post by ~LoKe on 2007-02-22
The thing about your home directory is that almost all the configurations are saved there.  This includes which theme you're using, conky settings, firefox settings & cache, gaim accounts, beryl settings, etc.

So, having it on a separate partition means that you can easily reinstall then have your system running up the same way it was before.

---

