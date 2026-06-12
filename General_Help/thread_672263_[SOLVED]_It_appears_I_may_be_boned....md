---
title: "[SOLVED] It appears I may be boned..."
date: 2008-01-19
forum: General Help
---

### Post by denali on 2008-01-19
I installed the Xorg-Xserver-core update, then installed the rollback.  Now, the only program that runs without causing xwindow to restart is Firefox and Synaptic

Help?

---

### Post by dslehman on 2008-01-19
Same here. Running Gutsy Desktop x386, X was taken out on my 3 machines. X appears to restart after I initially log in to my account. I'm wondering if it is the combination of my nvidia driver and the new release of xserver-xorg. I ran this which switched me back to the "nv" driver and things appear to be at least functional now:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by denali on 2008-01-19
> **dslehman said:**
> Same here. Running Gutsy Desktop x386, X was taken out on my 3 machines. X appears to restart after I initially log in to my account. I'm wondering if it is the combination of my nvidia driver and the new release of xserver-xorg. I ran this which switched me back to the "nv" driver and things appear to be at least functional now:

sudo dpkg-reconfigure -phigh xserver-xorg

Yep, that has me going.  Pity this is my gaming system. :(

---

### Post by dslehman on 2008-01-19
I reverted back to the old version of xorg. Now my nvidia and glx work again. However, i'm feeling vulnerable.

# apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8

---

### Post by denali on 2008-01-19
> **dslehman said:**
> I reverted back to the old version of xorg. Now my nvidia and glx work again. However, i'm feeling vulnerable.

# apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8

I had already reverted back, but it didn't fix my problem.  However, reverting back to the 169.04 version of the nVidia drivers did fix my problems.  it sucks, because 169.07 was working REALLY well for me!  Darn it! :confused:

Thanks for your help dslehman!

denali

---

### Post by astoltz on 2008-01-19
The new xorg install overwrites a file from the nvidia install. Both the new xorg and the 169.07 nvidia driver will work together.  You just have to re-install the 169.07 nvidia driver AFTER the xorg update.

You could also just fix the file that xorg overwrites.  After you update xserver-xorg-core, then do the following:```

cd /usr/lib/xorg/modules/extensions/
sudo mv libglx.so libglx.so.backup
sudo ln -s libglx.so.169.07 libglx.so
```

---

### Post by dslehman on 2008-01-21
Thanks astoltz.

Here's exactly what I had to do in order to get my machine working again:

[INDENT]
ctrl+alt+f1

sudo -s

aptitude update; aptitude dist-upgrade # update all xserver-xorg packages
cd /usr/lib/xorg/modules/extensions/
cp libglx.so libglx.so~orig
rm libglx.so
cp /etc/X11/xorg.conf /etc/X11/xorg.conf~orig
dpkg-reconfigure -phigh xserver-xorg
/etc/init.d/gdm stop
sh NVIDIA-Linux-x86-169.07-pkg1.run uninstall
sh NVIDIA-Linux-x86-169.07-pkg1.run
/etc/init.d/gdm start
[/INDENT]

---

### Post by astoltz on 2008-01-21
Cool, glad you're up and running again.  That update broke my system as well and it took a lot of head scratching to track it down.  I guess it's the price you pay for installing a non-standard driver.  But it seems like the xorg update ought to be smart enough to pick that up.

---

### Post by CheShA on 2008-01-21
This seems to have got me too, I've not tried the fix here yet,it's late and I wana go to bed but this looks exactly like what I've got - thanks  for the advice. 
Interestingly, I didn't even search for this topic, I picked it out by name first time!!:lolflag: Actually, thinking abut it... if this update is going to affect a lot of nvidia users  (maybe all those that used envy like me?) then maybe you could change the title to something more descriptive for those less perceptive than me ;)

---

### Post by denali on 2008-01-22
> **astoltz said:**
> The new xorg install overwrites a file from the nvidia install. Both the new xorg and the 169.07 nvidia driver will work together.  You just have to re-install the 169.07 nvidia driver AFTER the xorg update.

You could also just fix the file that xorg overwrites.  After you update xserver-xorg-core, then do the following:```

cd /usr/lib/xorg/modules/extensions/
sudo mv libglx.so libglx.so.backup
sudo ln -s libglx.so.169.07 libglx.so
```

You nailed it on the head.  It appears nVidia took notice of this as well, as their new driver (169.09, released 1/21/08 ) builds in some workarounds to this issue.

Thanks!!!
denali

---

