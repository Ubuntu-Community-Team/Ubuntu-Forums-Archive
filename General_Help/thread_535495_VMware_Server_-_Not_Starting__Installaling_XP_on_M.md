---
title: "VMware Server - Not Starting / Installaling XP on Mounted NTFS drive"
date: 2007-08-26
forum: General Help
---

### Post by ashishgoel on 2007-08-26
Hi all,

Currently, I'm dual bootin Ubuntu 7.04 and Win XP. - becuase 1. Novice Linux User ; 2. Few programs which r required are not supported on Linux

After readin and learnin about VMWare Server - i thought to give it a shot. After installing the Server - On tryin to makin a new virtual drive/operatin system (Win XP) - if i choose a directory/location that is on NTFS/Win XP system which is automatically mounted for read/write in Fiesty Fawn - the VMware doesn't load even after it recognizes the mounted drives (after clickin POWER ON - I get only blank screen and again goes back to main console - askin to power on) and hence unable to install a virtua machine.

But if i change the location of a new Virtua Machine to my /home (or any directory on Linux System) - it works perfectly - I'm able to Install windows and work on it.

My Linux System has only 900 MB free (Total Size 5 GB with 750 Swap)- and to Install windows I had to use small xp installation (only 400 MB in size - TinyXP - Beast edition) and keepin the size of Virtua system to 600 MB max, as regular XP cannot be installed.

Problem / Questin 1 :- How Can I install VMware on NTFS drive in Ubuntu ?? (If not possible, then please tell me so that i can drop the Idea - Needed so that I can have regular XP installation as my apps are not supported on TinyXP as needs .Net 2 and other updates.)

Problem/ Question 2 :- I've free 5 GB space on NTFS system and I have Acronis Disk Utility - Is it possible to Increase Ubuntu Disk Space without disturbing the Ubuntu File System and the GRUB loader - as it took me approx 2 hrs to thoroughly update and bring it present condition after fresh Ubuntu 7.04 installation. I read about Gparted - but have apprehensions about disturbing the XP file system then..
I mentioned GRUB also, because when i partiotioned my new Dell Laptop (other machine) in Windows XP with the Acronis Disk Utility - that messed up with the Boot Loader - and then had to completely format and install everythin as the Recovery option also didn't worked owin to boot failure.

Please help.

Thanx alot

---

### Post by ashishgoel on 2007-08-27
"help"

---

### Post by bryonak on 2007-08-27
First of all, could you give a bit more specific information about your disk layout?
One HDD? How many/how big partitions?
Did you use ntfs-3g to mount the Windows partition? You can check by typing "cat /etc/fstab" into your terminal and look your Window's partition mountpoint, the third column should be "ntfs-3g". If not, [here's a  short HowTo]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G").

I myself have a 80GB Linux hard disk and another 40GB with Windows, loading the existing Windows partition in VMware. Of course, you should have at the very least 1GB RAM (but rather more, I have 1.5GB) to run a VM efficiently...
I recommend that's what you should do, since it spares you reinstalling all your applications and wrestling with Windows' post-install configuration, plus you need less space since you get virtual and "real boot" windows in one. Just follow [this HowTo]("http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/"). I had to do a repair-install in VMware afterwards, but that's because that HDD's MBR was screwed anyway (I just used the drive as storage).

Which version of VMware-server are you using?
I'd suggest you [download v1.0.3 here ]("http://www.vmware.com/download/server/"). Also don't forget to install VMware-tools (included in the server), especially for the mouse performance.

As for your first problem...
Because ntfs is quite different from Linux' ext3 filesystem, there might be problems with the permissions. You should check the permissions on your .vmx, .vmdk and the other files in your config folder (you can view/set it in the server's preferences) aswell as on the virtual image itself. Try running VMware as root.
Perhaps adding yourself to the disk group (Users and Groups in Gnome's System->Administration) might help. Gotta admit, I simply don't know whether you can have the virtual image on ntfs, because I've never toyed around with that.

The other one...
GRUB is easily reinstalled via "sudo /sbin/grub-install" from your Ubuntu-install or Live-CD, you just need to backup your menu.lst file, since it's the only relevant configuration file.
I know absolutely nothing about that Acronis thingy, so no help in that case.
Gparted is my partition-editor of choice, epecially the even more powerful Live-CD version (you can download it [here]("http://gparted.sourceforge.net/livecd.php")). Resizing ntfs should be just fine, I'm not sure about moving the Ubuntu partition afterwards, you might have to delete it and make a bigger one.
For rescuing lost partitions/screwed up boot records, there's an amazing tool called TestDisk ([download here]("http://www.cgsecurity.org/wiki/TestDisk_Download"))... I have yet to encounter a HDD this program can't save ;)


Besides, have you tried running your apps in wine? (open a terminal, type: sudo aptitude install wine, double-click on your exe's...) You get native performance (almost, startup takes a little bit longer), unfortunately many apps won't work. Still it's preferable to emulating a whole OS, if your programs work...

Oh and.. welcome to the wonderful world of free choice and software!


*edit: further discussion [here]("http://ubuntuforums.org/showthread.php?p=3261750#post3261750")*

---

### Post by ashishgoel on 2007-08-27
THREAD CLOSED AND MOVED TO [http://ubuntuforums.org/showthread.php?p=3261750](http://ubuntuforums.org/showthread.php?p=3261750)

---

