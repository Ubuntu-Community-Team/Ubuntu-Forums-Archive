---
title: "ubuntu 12.04 dual boot Windows 7: intermittant GUI problem; filesystems question"
date: 2015-01-14
forum: General Help
---

### Post by jacklex on 2015-01-14
Hello, I have been using Ubuntu 12.04 (64 bit) dual boot on top of Windows 7 (32 bit). My processor is intel i5, and the hd is an electronic one of ~120 GB. I downloaded the iso and installed from the internet. I have had some problems but the system usually works ok. Lately, the system, configured to boot to Linux GUI when chosen from the Windows boot menu, sometimes boots ok with the Launcher, and all features accessible. But other times, it boots to a black screen with very small font resembling a runlevel 3. If I do "startx" I get a GUI but there's nothing to do with the GUI, no launcher. Other times it boots to that empty dark red GUI.  At present, I can't get the launcher at all. I can get a menu to look at certain files or create a document; no Firefox. Since the hd is small I need to add to this space, and I want to shift things around to utilize another electronic hd. Using Windows I formatted another hd with NTFS, which is usable with Ubuntu Linux. This drive is now called "New Volume" which is annoying, but looking at a Ubuntu forum or website, it is usable when enclosing the name with single quotes (else Linux or C won't recognize the name). So, copying cpp files to the new drive went fine, except when I tried to execute the executable file from the cpp file, the permissions denied execution. Then I found out NTFS doesn't like chmod. This I find peculiar because I never had problems changing permissions with the old hd. I am trying to find out what filesystem is on my old drive, which I thought was NTFS. If I ever am able to get a terminal to run on this Linux installation it might be possible to enter some queries to find a solution. Right now it looks like my only option is to copy all my files onto an external HD and reinstall both OS. Does Ubuntu make some kind of non-NTFS partition when installed over a Windows 7 OS? The files are visible from each OS. Could you also indicate if the boot problem is likely due to low memory on a given hd partition. Hope you can help me and probably others...

---

### Post by Impavidus on 2015-01-14
> **jacklex said:**
> ... on top of Windows 7 ...
... boot to Linux GUI when chosen from the Windows boot menu...
Sounds like wubi. Did you install Ubuntu using wubi? The last Ubuntu release for which this is supported is 12.04 (and as far as I am concerned, it was never recommended).

Ubuntu can't be installed on an NTFS partition and NTFS partitions don't support Unix style permissions, so you can't run your executables from one of those. Linux always needs a partition of its own. In case of wubi, this is a virtual partition on the NTFS partition, that from Windows's point of view is just a file. Ubuntu can read or write NTFS partitions.

If there is no disk space left, it may be impossible to create some temporary files. A full disk can also lead to things going wrong during an update. Both could explain your graphical issue.

---

### Post by oldfred on 2015-01-14
If you have an i5, you really should be running 64bit in a full partitioned install.

You cannot set ownership nor permissions on NTFS partitions, they do not support those Linux features. You only set the defaults when you mount it either automatically with default settings or with fstab with settings you desire.

Paragraphs with separate issues might help us.

---

### Post by jacklex on 2015-01-15
I installed Windows 7 32 bit because I had an old Microsoft application, which I have replaced with one from 2013. The 64 bit Ubuntu was installed as Impavidus suggested, ubuntu -11.10-wubi-amd64.tarxz, and updated to 12.04. I have used chmod to change permissions successfully (I had to create a new user to enable graphics mode options, similar problem to what I'm seeing now). Also I looked at the community page, which suggests a swap file equal to my memory. I am using 4 GB ram. Using disks$ ls -l the swap.disk space shows up as 268 MB. I have some files in the Linux partitions which could be deleted, which might get my system operable. This sharing of files has at least apparently kept me from losing everything in my Linux workspace. Previously I lost everything when attempting to adjust hd space with NTFS and ext3 partitions. I'm thinking it might be better to use Linux on a different computer. I'm glad I did not upgrade to Trusty Tahr because I expect my disk formatting would not accept it! Is there any way I can get the Linux boot to runlevel 3, so that some files can be deleted?  Thanks much for your help, Impavidus and Old Fred. I will consult also the website 22147295.

---

### Post by jacklex on 2015-01-15
I have some more information. While in Windows 7, I can see the Ubuntu files created by intrusion into Windows space (/host) but the files under Ubuntu (~17GB) can't be resolved; they appear as a single file from Windows. However, when I boot up in Ubuntu I can hit the "home" key and this gives me access to all the Linux files, through gedit. I have not yet attempted to write or modify them. I wonder if modifying one or more of these administrative files might enable booting into runlevel 3 which would allow copying individual files to a FAT USB flash drive. This would at least result in the files being useful. I already deleted some files to allow more space in the Ubuntu directory. Another aspect, I have a second Windows XP computer with Ubuntu. I copied the files onto a large hd (formatted NTFS) which I could insert in that computer. I am wondering if that Ubuntu would allow me to use the files in that computer. Another option, to boot with KNOPPIX. I have not yet attempted to use the KNOPPIX disk to boot a computer with Ubuntu, but it worked with other Linux versions, e.g. RedHat, with files in partitions formatted with ext3. Any ideas or suggestions would be helpful.

---

### Post by oldfred on 2015-01-15
If you can boot wubi, you should just be able to mount flash drive and copy /home or all your data.
The last supported version of wubi is 12.04.

       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

You can also mount wubi's root.disk which in Windows is just one large file, from Linux and then copy data also.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by jacklex on 2015-01-15
Hello, OldFred, 
thank you for addressing my issue. At present, while I have copied my ubuntu folder onto a large NTFS-formatted disk (in Windows 7, it's labeled E:) I cannot get a terminal from within Linux for command-line entries. I can only copy from within Windows. There are two options I'm considering: (1) copy to an external HD connected with USB then copy that to another computer which has Ubuntu working; or (2) remove the extra HD (on which I made a copy of the Ubuntu folder) and connect it to the other Ubuntu computer and try to use it. My question is whether the other computer's Ubuntu will recognize the Ubuntu folder and its files. 
     I read the forums suggested; they demand either using Linux command line or a live disk. Would an old KNOPPIX disk be likely to work?

---

### Post by oldfred on 2015-01-15
May depend on how old.

Better to use current version of Ubuntu. Download live Desktop version and boot in live mode.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by jacklex on 2015-01-15
I was able to get a "runlevel 3" terminal tty1 by using crtl + alt + F2 from the dark red screen. Then I got ability to see files, use the VIM editor and run executables from various users' directories. Is there some feature in dmesg or /var/log files that might enable me to fix the problem?
The download of v. 14 might not work because it does not do wubi (?) At least it seems I have access to my individual files.

---

### Post by Impavidus on 2015-01-16
An old knoppix disk may not work because it may not support the ext4 file system, which your Ubuntu 12.04 is likely to use. You could try though. But with access to tty2 (or any other console tty1–6) you can either mount an usb drive and copy the files to it, or copy them to your Windows file system in /host and then use Windows to put them somewhere safe.

Ubuntu 14.04 may not install properly using wubi, but it can read the root.disk file without problems. If you create a 14.04 live disk and boot from that, you will have access to your Ubuntu files in a GUI. Instructions for mounting root.disk are in post #6. Taking the hard drive out and connecting it to a different Ubuntu system will work too. You can mount root.disk in the same way.

You can dig into the log files and hope you find the cause of your problems. It may be difficult to find though. I have a few guesses that might fix the issue if it's something simple. You suggested it could be caused by a full partition. These commands may tell us:```
fdisk
fdisk -i
```
To clean up some disk space, try```
sudo apt-get clean
```It may not clear much, but it may be enough to get some headroom.
Maybe you have old kernels and headers filling up your disk space. You can list them using this command:```
dpkg --list 'linux-image*' 'linux-headers*'
```
When you have regained enough free disk space, maybe fixing some packages is all it takes:```
sudo apt-get update
sudo apt-get install -f
```Pay a little attention using the second command. If it suggests to uninstall a package you think you need, answer no to the prompt.
Another common cause of problems are root owned files in your home directory. This can be fixed with:```
sudo chmod -R username:username /home/username
```Substitute your own username here. Be careful when using this command. A single typo can completely hose your system.
These commands are all safe, as they can't break something that  wasn't broken already. You can suffix any of these commands with```
| tee /host/ubuntu/filename.txt
```using unique filenames. Note the first character is a pipe, on my keyboard accessed with shift+backslash. This will store a copy of the output of the command in ubuntu/filename.txt on the Windows partition, from where you can easily upload it to the forum.

You could also forget about fixing this and just backup all your files and do a clean install of either 12.04 or 14.04.

For your interest: Runlevel 3 is not used in Ubuntu. Both the consoles tty1–6, accessible using ctrl+alt+F1–F6, and the GUI, accessible using ctrl+alt+F7, work on runlevel 2. But apart from the people working on the boot and shutdown processes, nobody really cares about runlevels.
[http://upstart.ubuntu.com/cookbook/#runlevels](http://upstart.ubuntu.com/cookbook/#runlevels)

---

### Post by jacklex on 2015-01-16
Looking over my notes from y 2013, same issue.  As mentioned earlier your suggested sites showed how to get tty1 up and I was able to issue command-line options. Doing unity --reset failed (no D-BUS daemon error, etc.) but apt-get install unity did trigger installation of updated code. I shut down and rebooted, getting the GUI with the launcher (which previously had disappeared). When I reinstall Ubuntu it will be on a system with more space, and I intend to use a separate disk formatted with ext4, since wubi has issues. Disk space or wubi had nothing to do with my launcher problem, however. Thank you for the notes, all of which I will remember.

---

