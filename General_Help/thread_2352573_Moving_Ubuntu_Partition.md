---
title: "Moving Ubuntu Partition"
date: 2017-02-13
forum: General Help
---

### Post by box02-0 on 2017-02-13
Hi.

I'm currently running a dual boot system &#8211; the very FIRST Partition is Windows and the very LAST Partition is Ubuntu 14.04. I want to expand the Ubuntu Partition, but there is no room 'after', only room 'before'.

I will make a NEW Ubuntu Partition just 'before', and copy the CURRENT Ubuntu to it. (I will have to work out uuid issues.). Later I will expand this into the ORIGINAL Ubuntu Partition. 

My problem is how do I change the MBR to boot the NEW Ubuntu Partition **INSTEAD** of the ORIGINAL Ubuntu Partition?

If I try:  ** sudo grub-install /dev/sda**, how do I tell it to boot the NEW Ubuntu Partition ??
                OR
Should I try **update-grub** to see if it will detect the NEW Ubuntu partition, and how do I tell it to boot the NEW Ubuntu Partition ??

Should I delete the ORIGINAL Ubuntu Partition first - a little scary since I would like to ensure the NEW Ubuntu Partition is working before wiping anything out.


Thanks,

M&#8230;.

---

### Post by yancek on 2017-02-13
It would be much simpler and less problematic to simply create another partition for data out of the unallocated space you have.

---

### Post by oldfred on 2017-02-14
I prefer new install if you have room.
When ever upgrading I always install to a new 25GB / (root) partition. I keep old one for a while.
And I have all data normally in /home in a /mnt/data partition that is large, my /home is actually tiny with only the user settings, as mostly hidden files & folders.

If you clone/copy you have all the duplicate UUID issues that you must correct. And then reinstall grub using new/copied installs UUID. You have to edit fstab with new UUID and some other configuration files may need changing.

Also a good time to test that your backup procedures for installed apps, system wide configurations in /etc, and user data & settings in /home are all correct. (which you must have no matter what you decide to do.)
Or good time to upgrade to 16.04.

---

### Post by box02-0 on 2017-02-14
Hi.

Thanks for the prompt responses.


Yancek:
[I]“It would be much simpler and less problematic to simply create another partition for data out of the unallocated space you have. “
[/I]
I have lots of room – about 60 gb of unallocated space on the SSD. And I do have a 200gb Partition for Data. My concern is the ever shrinking Ubuntu Partition.


oldfred:
[I]“I prefer new install if you have room.
When ever upgrading I always install to a new 25GB / (root) partition. I keep old one for a while.
And I have all data normally in /home in a /mnt/data partition that is large, my /home is actually tiny with only the user settings, as mostly hidden files & folders.”
[/I]
Currently I have a 200gb Partition strictly for Data i.e. business files, photos, music, documents, etc. 

Back in the old dreaded Windows days, I had a stripped down Windows System Partition, and all Programs (apps) (WordPerfect, Text Editors, CADs, Photoshop, etc.) and Data were installed in other Partitions. Windows gave you a choice as to where you could install a Program.

Now I have a 40gb Ubuntu Partition which is slowly filling up because all the Programs (apps) that I download, Text Editors, CAD programs, Graphics programs, utilities (Cairo, TomBoy, stickies,….), Programming languages, DataBase programs, etc., end up intertwined in the Ubuntu Partition. I don't have a choice as to where they are to be installed .

Ideally I would have stripped down Ubuntu Partition, containing ONLY Ubuntu System, with Downloaded Programs (apps) in another Partition – but I don't believe this is possible.


 *“If you clone/copy you have all the duplicate UUID issues that you must correct. And then reinstall grub using new/copied installs UUID. You have to edit fstab with new UUID and some other configuration files may need changing.”*

I have handled changing UUIDs before – but you are right, it is a pain.

*“Also a good time to test that your backup procedures for installed apps, system wide configurations in /etc, and user data & settings in /home are all correct. (which you must have no matter what you decide to do.)”*


My backups are on other off line SSDs and USBs, and are current, and tested cloned copies of my Active SSD. They are totally independent bootable drives. If my Active SSD was destroyed, I would plug in one of  these cloned drives and be up and running in minutes.

“Or good time to upgrade to 16.04. “

I have a BIG problem updating to a newer rev of Ubuntu – I would have to re-install dozens of Programs (apps). The update from Ubuntu 12.04 to 14.04 took me many, many days (weeks), and is now working like a charm. I do not know how to upgrade to Ubuntu 16.04 and NOT have to re-install all my Programs (apps). So for now, I would like to go the CLONE route to expand the Ubuntu Partition.


After some cleanup like Bleachbit, and removing unused Programs (apps), I have 6gb free in my 40gb Ubuntu Partition. I have some time, but sooner or later it will be full because I am Program (app) crazy. 

I have worked out a procedure to clone my Ubuntu Partition, but the new Ubuntu will be in a different Partition. The scary part for me is the MBR, which is pointing to the ORIGINAL Ubuntu Partition, and how to make it recognize the NEW cloned copy.

Of course I will test all this out on one of my backup cloned drives first.

Any advice you have to get the existing MBR to point to a new Partition would be greatly appreciated.


Thanks again,

M...

---

### Post by oldfred on 2017-02-14
You have to change UUID & edit fstab first.
Then you just need to run a full uninstall/reinstall of grub. Easiest with Boot-Repair and its advanced mode.

Also check these files:
 more /var/cache/debconf/config.dat  | grep /dev/disk
UUID in grub, fstab &
more /etc/initramfs-tools/conf.d/resume
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid 

I export list of installed apps. It is just a text file, so I do make sure nothing I do not want is still in list like old kernels.
Setting for apps are all in /home.

      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install 

My system over about 2 years between LTS, grows to 12 or 14GB with lots of apps installed. And I do regularly houseclean old logs and obsolete stuff.

---

