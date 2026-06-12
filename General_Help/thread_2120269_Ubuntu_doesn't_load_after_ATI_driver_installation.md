---
title: "Ubuntu doesn't load after ATI driver installation"
date: 2013-02-26
forum: General Help
---

### Post by captainwithershins on 2013-02-26
Yesterday I installed the latest Linux drivers from ATI. After restart Ubuntu said "/tmp can't be found. Press s to skip, m to manually mount or wait". I waited for a while and pressed S but nothing happened. Restarted and from then on it boots into the attached image. Please help, I don't want to reinstall. Thank you!

---

### Post by fuorviatos on 2013-02-26
Your problem seems not to be related to the graphic driver but rather to a partition mounting incorrectly.
Go to the recovery mode and try to issue the command below and show us the output: 

> mount

---

### Post by c2tarun on 2013-02-26
> **fuorviatos said:**
> Your problem seems not to be related to the graphic driver but rather to a partition mounting incorrectly.
Go to the recovery mode and try to issue the command below and show us the output:

Just curious: How did you figure out that problem is with partition mounting? Is there something in screenshot?

@captainwithershins: Please share the output of mount

Also please tell us the steps you followed in order to install ATI drivers.

---

### Post by captainwithershins on 2013-02-26
Got to the desktop, but now Unity doesn't load. Tried reinstalling it and compiz, but still doesn't load.

---

### Post by fuorviatos on 2013-02-26
> **c2tarun said:**
> Just curious: How did you figure out that problem is with partition mounting? Is there something in screenshot?
.

He wrote > After restart Ubuntu said "/tmp can't be found.That may mean that something is wrong with the partition.
Those may be the drivers also but unless we see the X's logs, we cannot be sure.
You're right in saying that we cannot be certain it's the partition for sure.
I need two things to start to investigate:

1. output of mount
2. Xorg.0.log attached

---

### Post by Yellow Pasque on 2013-02-26
That probably means you installed the wrong driver. What Ubuntu version are you running and what video card do you have?

If all you can access is a terminal (Ctrl+Alt+F1), you should find this helpful to get back to the original configuration: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by captainwithershins on 2013-02-26
Latest ubuntu version and ati 6770.
Edit: Downloaded this [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) installed. Didn't delete old installation first(oops?). Rebooted. That happened. I got to Desktop, no Unity. Reinstalled unity and compiz, no luck. Mount output:    :~$ mount
/dev/sda2 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/vasko/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=vasko)

unity output:   :~$ unity
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
Segmentation fault
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
Segmentation fault
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Segmentation fault

Went here [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Using_Ubuntu-supplied_fglrx.2FCatalyst](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Using_Ubuntu-supplied_fglrx.2FCatalyst) 
Did 
sudo apt-get install linux-source fglrx fglrx-amdcccle

generated a new xorg.conf. Forced it's use 
sudo amdconfig --input=/etc/X11/xorg.conf --tls=1output: 
sudo: amdconfig: command not found

fglrxinfo gives: Segmentation fault

---

### Post by captainwithershins on 2013-02-26
UPDATE: Removed the driver. Everything works fine now. Thank you for the help!

---

### Post by dcstar on 2013-02-26
> **captainwithershins said:**
> Latest ubuntu version and ati 6770.
Edit: Downloaded this [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) installed.
..........

Ubuntu provides ATI drivers that are verified to work in the Software Repository. All others run the risk of stuffing up your system - as you have experienced.

---

