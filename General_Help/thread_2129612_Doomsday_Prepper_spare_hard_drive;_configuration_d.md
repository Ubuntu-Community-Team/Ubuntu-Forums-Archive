---
title: "Doomsday Prepper: spare hard drive; configuration documentation- what's needed?"
date: 2013-03-26
forum: General Help
---

### Post by ozark_hillbilly on 2013-03-26
I have upgraded to 12.04 LTS from Lucid Lynx and have sorted most things out. I have a question in regard to taking measures to facilitate recovery in the event of a future hard drive crash.

Currently I have a separate smaller hard drive that I routinely backup my /Home partition user data to. Beyond that I am wondering what steps I should take to have access to configuration data so that a replacement drive could be brought up to 'speed' with as little difficulty as possible.

Questions:

1. Should I go ahead and purchase another hard drive for on the shelf? Any suggestions as to it's desired features? Current main drive is 250 GB.
2. Is there any particular utilities I can take advantage of to record my present hard drive partitioning information?
3. Is there a way to make my backup (archive) drive bootable or should I just rely on a Live CD?
4. What is the most efficient way to collect information on downloaded/installed apps (those taken thru Synaptic Package Mgr for instance) and upgrades to establish a listing
    for future reference?

So really what is needed is a checklist of some sort that highlights all software presently installed & my present hardware configuration.

Any suggestions are welcome,

Ed

---

### Post by oldfred on 2013-03-26
I use rsync and copy primarily /home as that has user settings, /etc and maybe a few other things from the system. I assume I will just do a new clean install and restore my /home. But my /home has nothing in it other than user settings as all my data is on other drives.

I also run bootinfoscript as part of my rsync which documents booting and partitions. And I export a new list of installed applications.

I started here which is a simple rsync script. Then added to it.
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

      #I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
#Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/bootinfoscript.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt
If I manually edit some system file like grub or settings in /etc, I try to remember to copy to a folder in /home to save those settings as part of normal backup.

You can exclude some data as it is not important like caches.
      
 Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

More examples if you want to get more advanced ( I have not yet).
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

I follow this logic, but have a working copy of Ubuntu on every drive and every drive is configured to completely boot without any other. But data which may give mount errors is on various drives.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ozark_hillbilly on 2013-03-26
Thanks Fred!!!
1st things 1st...need to figure out what rsync is all about...hahahaha.....a senior citizen still learning...

---

### Post by oldfred on 2013-03-26
I used to use a .bat file in Windows to copy files from Windows to a single partition. Windows used to scatter my data files all over, even with My Documents. Many apps wanted their own place to store data.  Then I would easily write data from that backup partition to DVDs as archived backup. I now do the same with rsync.

rsync is just a smart copy program. Very powerful & efficient, but with power comes complexity. It can run locally or over network, or even Internet. Biggest issue I had was what parameters to use, so I just copied an good example. If you look at man rsync you will get overwhelmed with all the copy parameters.

---

