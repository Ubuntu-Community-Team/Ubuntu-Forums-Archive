---
title: "update killed system"
date: 2020-07-02
forum: General Help
---

### Post by neoneuro on 2020-07-02
Hi All,

I'm running kubuntu 20.04. Yesterday a bunch of system updates came in. Seemed like the usual stuff, so I let them install. It took a little longer than usual, but there were quite a few, so I just let it do its thing. After they completed it notified me that it needed to do a reboot to complete the install. I did that and it took a long time. It was several minutes before I got back to the desktop. Even then it was very sluggish. Windows were only partially drawing, clicks didn't do anything, and so forth. There was no drive activity or network activity, or even CPU load beyond a regular idle state. After a few minutes I decided to try and reboot it again. This time it dumped me into the emergency mode and that's where it is now. I'm not sure what to do with it at this point. Any suggestions?

(I was going to post this on the kubuntu forums, but they appear to be down. Wonder if the same issue hit them?)

Thanks for any help you can offer.

---

### Post by neoneuro on 2020-07-02
Sorry, I forgot to post the errors I'm seeing on the screen. See below.
```

Initramfs unpacking failed: Decoding failed
ACPI BIOS Error (bug): Could not resolve symbol [\SB.PCIO.GP17.V
ACPI Error: Aborting method \_SB.PCIO.GP17.VGA.LCD._BCM due to pr
ACPI Error: Evaluating _BCM failed. (20190816/video-357)
kfd kfd: error getting iommu info. is the iommu enabled?
kfd kfd: Error initializing iommuv2
kfd kfd: device 1002:15d8 NOT added due to errors.
You are in emergency mode. <And so forth...>

```

---

### Post by monkeybrain20122 on 2020-07-02
Sounds like a bad kernel update. When you reboot, hit esc, from the grub menu choose advanced options, it will list two kernel, boot into the previous kernel  (the one with lower number) and see if it works. If it works, go to muon or synaptic to remove the new kernel stuffs (search for linux image and linux headers and uninstall everything with the highest number)

---

### Post by mastablasta on 2020-07-03
make sure you use wired connection when updating. you can get corrupted package easily via Wi-fi.

---

### Post by monkeybrain20122 on 2020-07-03
> **mastablasta said:**
> make sure you use wired connection when updating. you can get corrupted package easily via Wi-fi.

?? I always use only wifi, a lot of us in shared accommodation don't have access to wired connections (modem is upstairs, separate entrance) A wired connection to me is like cable TV, desktop computers, landline phones and Windows. Haven't used any of those for more than 10 years.

---

### Post by ActionParsnip on 2020-07-03
If you boot an older kernel is it OK?

---

### Post by SeijiSensei on 2020-07-03
I'm running Kubuntu 20.04 and have kernel 5.4.0-40-generic and as a backup 5.4.0-39-generic.  A check for updates shows that -40 is the most recent kernel.  No problems here for me.

---

### Post by Yellow Pasque on 2020-07-03
Possibly related to?: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1870260](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1870260)

---

### Post by neoneuro on 2020-07-03
> **monkeybrain20122 said:**
> Sounds like a bad kernel update. When you reboot, hit esc, from the grub menu choose advanced options, it will list two kernel, boot into the previous kernel (the one with lower number) and see if it works. If it works, go to muon or synaptic to remove the new kernel stuffs (search for linux image and linux headers and uninstall everything with the highest number)
Looks like I have kernel versions 5.4.0-40, -39, -37, and -33. Tried them all. Get the same errors with all of them.

---

### Post by neoneuro on 2020-07-03
> **ActionParsnip said:**
> If you boot an older kernel is it OK?
No. Didn't work with any of them. Something else went sideways.

---

### Post by neoneuro on 2020-07-03
> **Yellow Pasque said:**
> Possibly related to?: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1870260](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1870260)
I had high hopes for this. Edited the file to reflect gzip and ran the update-initramfs command. The initramfs error is gone, but it still doesn't boot. The remaining error lines are still there.

---

### Post by kneutron on 2020-07-04
--Not being able to boot sucks, but FYI this is why I **do full bare-metal backup to a separate drive before doing any apt upgrades**.  My 20.04 zfs boot/root install got borked a few weeks ago when I reverted to a previous snapshot.  Only thing that saved me was my habit of running a ' bkpcrit ' script before installing any new software, cuz IIRC /var/lib/dpkg did not have anything useful in it after reverting and I was able to do a tar restore.

--I wrote a set of custom scripts (including restore) which utilize **fsarchiver** based on some info from the crunchbang forums years ago, but this may work for you in the future:

[https://relax-and-recover.org/](https://relax-and-recover.org/)

[http://www.linuxandubuntu.com/home/make-your-very-own-customized-linux-distro-from-your-current-installation](http://www.linuxandubuntu.com/home/make-your-very-own-customized-linux-distro-from-your-current-installation)


--If you still have the original ISO / install disc / USB installer, *you're probably looking at a reinstall* to save time and effort.  Given the error message, I hope your hard drive isn't dying.

--If you didn't have a separate /home partition, be sure to create one on the next install.  I would also start looking into testing your restores into a VM such as Virtualbox.  PROTIP: You can also take VM snapshots and try ' apt upgrade ' in-VM before making modifications to your main install, and reverting a VM snapshot is dead easy.

--In a sincere effort to be helpful, I'm including my ' bkpcrit ' script so you can start using it if you like. Don't forget to chmod +x it, and run from /root/bin

BEGIN /root/bin/bkpcrit
```

#!/bin/bash
# Backup critical files (hopefully)

# BKPCRIT BACKUP FILES SHOULD NOT BE ON THE SAME DISK AS ROOT!!
# REQUIRES: lzop

drive=/media/usb3drive # TODO EDITME

#  taropts="--use-compress-program lzop -cpf "
  taropts="--lzop -cpf "; tarsfx="tar.lzop"

rootpartn=`df / |tail -n 1 |awk '{print $1}'` # /dev/sde1
rootpedit=`echo ${rootpartn##*/}` # strip off beginning, and last slash: sde1

myhn=`hostname`
dest="$drive/bkpcrit-$myhn--linux-ubuntu2004-64-LTS-zfsrootboot-$rootpedit" #sdX1"
echo $dest 

mkdir -pv $dest
chmod 750 $dest # drwxr-x---

tdate=`date +%Y%m%d`

# Copy this bkp script to bkpdest
cp -v $0 $dest
#cp -v ~/localinfo.dat $dest
[ -e /etc/inittab ] && cp -v /etc/inittab $dest
cp -v /etc/fstab $dest
cp -v /tmp/smartctl.txt $dest
cp -v /tmp/fdisk-l.txt $dest/fdisk-l-$tdate.txt

echo 'o Clearing old files'
 # !! find bkp-gz, bkp-bz2 and flist files more than ~2 weeks old and delete
cd $dest && \
   find $dest/* \( -name "*.txt" -o -name "flist*" \) -type f -mtime +15 -exec /bin/rm -v {} \;
#   find $dest/* \( -name "*.txt" -o -name "bkp*bz2" -o -name "flist*" \) -type f -mtime +20 -exec /bin/rm -v {} \;
   

# document system state
mount |egrep -v 'tmpfs|cgroup' |column -t >> $dest/fdisk-l-$tdate.txt # xxx 2017.0218
df -h -T > $dest/df-h.txt # added 2016.april
df -T -x{tmpfs,usbfs} > $dest/df-$tdate.txt    # nice to have non-h df as well

# removed 2016.0319, not using lvm
#vgdisplay -v > $dest/vgdisplay-v-$tdate.txt

distro="ubuntu"
tar $taropts $dest/bkp-boot-$distro.$tarsfx /boot

tar $taropts $dest/bkp-ETC-$distro.$tarsfx /etc

tar $taropts $dest/bkp-NXETC-$distro.$tarsfx /usr/NX/etc
tar $taropts $dest/bkp-NXSHARE-$distro.$tarsfx /usr/NX/share
tar $taropts $dest/bkp-NXVAR-$distro.$tarsfx /usr/NX/var

tar $taropts $dest/bkp-DEV-$distro.$tarsfx /dev

tar $taropts $dest/bkp-root-$distro.$tarsfx /root

#tar $taropts $dest/bkp-usr-src-cfgs.$tarsfx /usr/src/*.cfg
tar $taropts $dest/bkp-usr-local-bin-$distro.$tarsfx /usr/local/bin

tar $taropts $dest/bkp-var-dpkg-status.$tarsfx /var/lib/dpkg
tar $taropts $dest/bkp-var-dpkg-backups.$tarsfx /var/backups
tar $taropts $dest/bkp-var-cache-apt-backups.$tarsfx /var/cache/apt
#/var/adm/inst-log

tar $taropts $dest/bkp-davesrc.$tarsfx /home/dave/src
tar $taropts $dest/bkp-davebin.$tarsfx /home/dave/bin /home/dave/.bashrc /home/dave/gonow


# Dotfiles
#cd /root
#tar cpvzf $dest/bkp-root-dotfiles--restore-locally$tarsfx .[^.]*

# thunderbird is just email, goes in bkphome
# NOTE - to see size of hidden dirs: du -hs .[^.]* # REF: http://superuser.com/questions/342448/du-command-does-not-parse-hidden-directories

# TODO EDITME
cd /home/youruseridhere
tar \
  --exclude='.kde/share/thumbnails' \
  --exclude='.kde/share/cache' \
  --exclude=".pan/*" \
  --exclude='.gqview/thumbnails' \
  --exclude='.thumbnails' \
  --exclude='.opera/cache4' \
  --exclude='.opera/thumbnails' \
  --exclude='.thunderbird' \
  --exclude=".cache/*" \
  --exclude=".mozilla/firefox/*" \
  --exclude=".moonchild productions/pale moon/*" \
  --exclude='..' \
  $taropts $dest/bkp-user-dotfiles--restore-locally.$tarsfx .[^.]*

#  --exclude=".mozilla/firefox/*.default/Cache*" \

#sync

ls $dest -lh
df -h $drive
echo $dest
echo "$0 done - `date`"

exit


```

---

### Post by neoneuro on 2020-07-05
> **kneutron said:**
> --Not being able to boot sucks, but FYI this is why I **do full bare-metal backup to a separate drive before doing any apt upgrades**.  My 20.04 zfs boot/root install got borked a few weeks ago when I reverted to a previous snapshot.  Only thing that saved me was my habit of running a ' bkpcrit ' script before installing any new software, cuz IIRC /var/lib/dpkg did not have anything useful in it after reverting and I was able to do a tar restore.

--I wrote a set of custom scripts (including restore) which utilize **fsarchiver** based on some info from the crunchbang forums years ago, but this may work for you in the future:

[https://relax-and-recover.org/](https://relax-and-recover.org/)

[http://www.linuxandubuntu.com/home/make-your-very-own-customized-linux-distro-from-your-current-installation](http://www.linuxandubuntu.com/home/make-your-very-own-customized-linux-distro-from-your-current-installation)


--If you still have the original ISO / install disc / USB installer, *you're probably looking at a reinstall* to save time and effort.  Given the error message, I hope your hard drive isn't dying.

--If you didn't have a separate /home partition, be sure to create one on the next install.  I would also start looking into testing your restores into a VM such as Virtualbox.  PROTIP: You can also take VM snapshots and try ' apt upgrade ' in-VM before making modifications to your main install, and reverting a VM snapshot is dead easy.

--In a sincere effort to be helpful, I'm including my ' bkpcrit ' script so you can start using it if you like. Don't forget to chmod +x it, and run from /root/bin



Thanks. I managed to carve out some time to do a little more troubleshooting. I booted from a fresh 20.04 USB. Interestingly, it lists the same video "errors" that I'm currently seeing, but it boots. That makes me think that it is something else going on that isn't getting logged or it's being logged somewhere else. Out of curiosity, I tried booting a Neon live USB. It boots fine and doesn't have all those video errors. Hmmm...

I've pretty much reached the same conclusion that you have. Doing a reinstall is probably the fastest way to fix this. However, since this is the second system-breaking update in as many months, I think I'll go a different direction this time. (Last month some more updates bonked my zfs RAID. The updates had nothing to do with zfs, but somehow it screwed it up so that my RAID would no longer mount. I had to rebuild the entire array from scratch to get it back. Luckily I have a good backup for that.)

I think I'll give Neon a try this time around. I liked kubuntu, but I don't like having my system down constantly. I really only have to requirements for my system, KDE and deb packages. Unfortunately those two things are becoming less and less common. Maybe going directly to KDE will do the trick.

Thanks again!

---

