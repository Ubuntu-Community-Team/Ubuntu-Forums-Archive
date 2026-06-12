---
title: "Folder create in NTFS root directory disappears"
date: 2014-01-15
forum: General Help
---

### Post by vishal733 on 2014-01-15
I am facing a very weird problem.

Here are my system details:
Laptop: Lenovo T430
Dual Boot b/w Windows 8.1 and Ubuntu 13.10

There are few ntfs partitions for Windows, and ext4 paritions for Ubuntu 13.10.

I have made the following entry in /etc/fstab in order to automount my ntfs partition:
*/dev/sda5	/media/dataDrive	ntfs-3g	rw,auto,user,fmask=0111,dmask=0000	0	0*

Now this is my observation for this drive.
(1) If I create any folder/file on the root directory of the ntfs drive from Ubuntu, upon restart of system the file is not visible either from Windows or from Ubuntu.
(2) If I create any folder/file inside an existing directory on the ntfs drive, it is visible even upon restarts.
(3) To correct (1), I need to enter Windows, and do a check for errors on the disk. Upon error detection, Windows recovers the lost files/folders on the ntfs drive.

The package ntfs-3g is already installed on my system.

Kindly suggest a solution.

---

### Post by Bucky Ball on 2014-01-15
Delete your fstab line for the NTFS partition and allow ntfs-config to create it for you.

You can install ntfs-config from the repos. It should then appear under apps in I think System. Launch it and select the drive you want to mount at boot. It will rewrite the fstab for you. Reboot and see if you get the same issues.

If all is well it might be an idea to compare your original fstab line with the one ntfs-config creates to see where you went wrong.

PS: don't know where you got the instructions for constructing the fstab line, but the convention /dev/sd** is old and not used anymore. UUIDs are used now. For instance:

```
UUID=6B8E2F2A62CEE191   /mnt/Misc       ntfs    defaults,locale=en_AU.UTF-8 0 0
```  

You can find the UUID number for your NTFS drive with:

```
  sudo blkid
```  

Replace '/dev/sda5' with it, same syntax as above. The line you provided would then look like:

```
  UUID=<uuid of /dev/sda5>  /media/dataDrive ntfs-3g rw,auto,user,fmask=0111,dmask=0000 0 0
```

I'm presuming this mount point: /media/dataDrive exists in /media?

---

### Post by sisco311 on 2014-01-15
You have to fully shut down Windows before you boot into Ubuntu. You can't left Windows in hibernation and you have to disable the fast restart feature. As an Administration in Windows you can use below command to disable both hibernation and fast restarting:
```
powercfg /h off
```

---

### Post by zemega on 2014-01-15
In Windows 8 or 8.1, there is no complete shutdown, what Windows 8/8.1 does is actually hibernate. That is why any changes made to the NTFS partition using Ubuntu will be reverted back. If you want to make changes using Ubuntu, you have to completely shutdown, either by the Windows 8 restart command or turning off the Fast Startup function, see link below. Do note, disabling this will allow you to safely make changes to your NTFS partition using Ubuntu, the only possible downside is that you may feel booting and shutting down Windows 8.1 is slower than before.

[http://www.ghacks.net/2013/01/10/windows-8s-fast-startup-does-not-play-well-with-dual-boot-systems/](http://www.ghacks.net/2013/01/10/windows-8s-fast-startup-does-not-play-well-with-dual-boot-systems/)

PS: You know how Microsoft treat Windows Vista, how Vista is being forgotten in place of Windows 7. That is Microsoft plan with Windows 8, they want to forget it and move on to Windows 9 which set to release in 2015.

---

