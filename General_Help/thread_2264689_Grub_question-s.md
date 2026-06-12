---
title: "Grub question-s?"
date: 2015-02-09
forum: General Help
---

### Post by Jack Sterling on 2015-02-09
My machine is an HP DM1 with 14.04 Gnome installed and I've been using Ubuntu Linux a long time. The grub file has always been somewhat of a mystery which has lately gotten even more so. At least two problems here: 

One, I tried out different desktops lately (using apt-get install xubuntu desktop for instance) and now can't get rid of the resulting trash they generated (eg: the flash screens) I have uninstalled most of them manually with terminal commands but one, Kubuntu, remains. 

Secondly: I counted 60 previous versions of the kernel in my grub this morning and am wondering if those are really full kernels cluttering up my hard drive. If so how do I get rid of most of them - I  would assume that 4 or 5 would be sufficient for backup in case of a glitch in a new one. BTW, I update daily.

Another problem which appears to be getting more frequent: I lose my keyboard input more and more often lately. I realize it could be a hardware problem; is there any way to determine that? 

Sorry if there are too many topics here. Trying to be economical.

---

### Post by oldfred on 2015-02-09
I tried installing another desktop once and never could fully restore to original, ended up with a new clean install. 
So now if I want to test another desktop, I just create another 20GB / Partition and install. Then I can test at will and not worry about my main working install.

I try to only keep one or two extra kernels and houseclean all older ones. I think system now does that automatically. But I always have used synaptic. If you have upgraded and have old kernels, those are probably not even in dpkg and eligible for standard delete. You just have to manually delete each set of kernel files. I prefer to do new clean installs to another / (root) partition just so I do a full houseclean of old kernels, log files and other cruft that builds up over time.

Do not know about keyboard issue. Maybe check for loose connection? I did have a mouse have issues because wire seemed broken inside and it would often work only if I pushed wire back into mouse.

 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

      
 With 14.04 this should keep two kernels on new kernel installs:
/etc/kernel/postinst.d/apt-auto-removal


 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
sudo apt-get -s autoremove


 I prefer synatic and keeping 2 kernels, current and one known working older on.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by grahammechanical on 2015-02-09
The Grub menu in the Advanced Option sub-menu will list two entries for every kernel found in /boot/. One of those entries will be a recovery mode option. But both entries load the same kernel. Each choice loads the same kernel but with different boot parameters.

This is the difference in boot parameters on my default Linux kernel

> linux /boot/vmlinuz-3.18.0-13-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash $vt_handoff

And now the recovery mode option

> linux /boot/vmlinuz-3.18.0-13-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro recovery nomodeset 

Notice the exact same kernel is loaded but the boot parameters at the end of the line are different. I am using Vivid Vervet (15.04 under development) not only do I have a later kernel but we now have an option to load using systemd and not upstart. Again the kernel is the same it is just the boot parameters that have changed.

> linux /boot/vmlinuz-3.18.0-13-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash $vt_handoff init=/lib/systemd/systemd

The total entries in the Grub menu do not equal the total kernels stored in /boot/. By the way, if you load recovery mode you will get the recovery menu which will have an option called Clean - Try to make free space. That will run these two commands.

```
apt-get clean
apt-get autoremove
```

Regards.

---

### Post by Jack Sterling on 2015-02-10
Thanks oldfred - I have gotten rid of the splash screen so far. Next is editing grub to reduce the list of old kernels.

---

### Post by Jack Sterling on 2015-02-10
Thanks Grahammechanical: two suggestions tried so far and both removed a lot of various junk. Getting shed of the unwanted splash screen was nice. I'm pretty sure these operations are stored in a log file but not what the name might be. Any suggestions? It would be nice to know exactly what happened but hard to read as it is happening.

---

### Post by Karlchen on 2015-02-10
Hello, Jack Sterling.

Any software installation / update / removal which is done using the software management applications (Software Centre, Synaptic, apt-get etc) should be logged in the file /var/log/dpkg.log.

And in order to get an idea how many (old) kernels have been left behind by "apt-get autoremove" you might do an ```
ls -l /boot/vmlinuz*
```

> Next is editing grub to reduce the list of old kernels. Nope, this is not the right way. This would be curing the symptoms, but leaving the root cause alone. Instead you should use e.g. Synaptic to cleanly uninstall any old kernel which you no longer need. (Personally I will always keep a minimum of 2 kernels: the current kernel and the previous kernel.)

Cheers,
Karl

---

