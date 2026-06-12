---
title: "Crap, I accidentally deleted my &quot;user/Home&quot; partition."
date: 2008-01-25
forum: General Help
---

### Post by brjoon1021 on 2008-01-25
Hi,

I have Gutsy as my main distro installed on hda2. Well, I wanted to try out PCLinuxOS TinyMe so I installed it on hda3 which is all fine, but the problem is that I screwed up and overwrote Ubuntu's "user/Home" partition which was on another disk at hdi5. I must have accidentally installed the PCLOS TinyMe "user/Home" over it on hdi5, like an idiot. 

So, when I try to boot Ubuntu, it takes a long time to boot, there is just a cursor in the upper left hand corner of the screen for a true minute or so. Then when I do get to login screen and try to login, I am told (essentially, in a confusing Linux kind of way...) that there is no "/Home" and that I probably can't run unless I use a failsafe mode. I have tried everything I know to do from there and nothing works. I can't run KDE or Gnome, I end up back at the login over and over again.

What can I do ? I have a really customized Gutsy install, lots of FF bookmarks, emails, KDE, etc... I don't want to reinstall unless I HAVE TO.

Now, on my disk that is for the "/Home" partitions, /dev/hdi, I have two partitions that are empty, hdi2 and hdi3. Maybe I just need to make a "/Home" partition for Ubuntu in one of them using a LiveCD ? If that is the fix, please tell me how to put a "user/Home" on one of the partitions.  I am booted up with a LiveCD right now. If I can successfully fix whatever it takes to be able to log in and run Gnome or KDE, then I can see what the situation is since I lost all of the data that was in the original "user/Home" partition. Maybe I will have to reinstall anyway... Can you help ?

I have to go to work in about a half hour. If you see this and post, I will check after work. Please take a look again tonight or tomorrow to see if I posted back with problems. Help, please...

B.

---

### Post by opscure on 2008-01-25
on your login screen you can ctrl+alt+f1 and then login as root.  from there you can startx and attempt to repair your home directory, but since you destroyed your home directory most of your user specific settings will be lost.

---

### Post by meindian523 on 2008-01-25
your stuff is gone,that is any settings,docs,music,videos etc are gone but you can rescue your install by formatting one of you hdi2/3 as ext3 and modifying /etc/fstab to reflect the new setup.

---

### Post by brjoon1021 on 2008-01-25
poop. Anyone got a glimmer of hope?

1. What kinds of user settings: which apps, etc... would likely be in there ? I didn't have any other files there other than the user settings because all files go to another partition. There was only one "user" on the computer. I named that user, "user" creatively enough. So only the profiles, user settings, etc... that were created for the single user were there.

2. Can you be a little more explicit for a novice on how to either repair from the command line or to make another partition and to make the fstab changes that are necessary ?

Thanks,

B

---

### Post by meindian523 on 2008-01-25
Ans to:
1]ALL personal settings for ALL apps got folders in your /home/<username>/<.appname> folder,so that's that.You better remember what you liked for each app.
2]Since you are on Live CD,you will have GParted in System>>Administration.Fire it up and make sure which partition you are formatting.

Click Partition>>Unmount(if it is mounted)The again select the partition you unmounted and click Partition>>Format-To>>ext3.

---

### Post by fish2ways on 2008-01-25
Ubuntu and linux store all the configuration files specific to you as a user in your home folder. They are too numerous to list and a lot will depend on what you had installed and changed since initial install. most will be hidden files (they begin with a . ) For instance if you use firefox all your bookmarks, add-ons, themes etc. Most likely all your email info will be there and will be gone. 
My personal advice is accept the fact that it's gone, put it down to experience (don't make the same mistake again) and do a fresh install. You've nothing much (left) to lose.
Then back-up, back-up, back-up your home folder regularly to a seperate drive, DVD whatever.

---

### Post by meindian523 on 2008-01-25
Not exactly,if he's using APTonCD or has not run apt-get clean,he doesn't need to lose any of his programs and have to reinstall them later.Since he has a partition free,it can be formatted as ext3 and mounted as his NEW /home partition.

---

### Post by meindian523 on 2008-01-25
Ah,I forget,after creating your new /home partition,be sure to create a "user" folder on it before trying to reboot into your sick installation.(sick as in diseased)

---

