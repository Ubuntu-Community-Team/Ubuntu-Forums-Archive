---
title: "Windows/Ubuntu Shared libraries"
date: 2014-09-26
forum: General Help
---

### Post by kamhagh on 2014-09-26
hi, is there anyway i can make my library shared between two? like when i open documents from file browser i get to my second hdd(E:/Libraries/Music) ?

---

### Post by deadflowr on 2014-09-26
Ubuntu can see/read the Windows partitions,but Windows can't see/read the Ubuntu partition, at least not normally. I think there is an app to help with that for Windows, but not sure.
So on the Ubuntu side, you can mount the windows partition and browse it.
It'll be listed in Ubuntu's file manager's left side pane under the section for Devices.

Don't really know how helpful that will be.

---

### Post by kamhagh on 2014-09-26
thanks

so atleast is there anyway i can make my documents and downloads to automatically get inside my windows partition's document? not ubuntu's

---

### Post by ajgreeny on 2014-09-26
The best and safest way to share data between Windows and Ubuntu is to have a separate ntfs data partition where all the data sits and then link the Documents, Music, Video, etc etc folders in that to the same named folders in Ubuntu.

Come back and ask about this if you want to look in more detail; it is easier to set this up at installation time but can be sorted later if there is enough space to move files around on your hard disk.

If you just want to carry on according to your last question you will need to edit /etc/fstab in Ubuntu to mount the Windows partition at boot time, and then link the Document folder in your Ubuntu /home to the Documents folder in Windows.

---

### Post by Mike_Walsh on 2014-09-26
I will back up what AJ has said about this.

I no longer use Windows (any sort!), but I have a TON of stuff from my XP days. It sits on an NTFS partition on my external, portable hard drive. This way, I can view/use it from within Ubuntu; and if I want to use any of the data on any computer running Windows, I just take the HD with me, plug it in.....and away I go.

It's definitely the easiest way of handling your problem. NTFS is viewable by both Windows **and **Ubuntu.


Regards,

Mike.

---

### Post by kamhagh on 2014-09-26
ok i already have an NTFS partition, i have 2 storage (ssd and hdd)

is doing it risky/hard? because if it is i can just navigate to the folder myself ! now im thinking i can make a desktop shortcut!

---

### Post by Mike_Walsh on 2014-09-26
No risk at all, as far as I'm aware.

It should simply be a case of storing whatever folders/files you wish to be able to access from both OSs **into **the NTFS partition. I have mine set up with separate folders for Documents, Media, Applications, etc., etc; obviously, you call **your** folders and sub-folders what you like, but anything you want to use in either Windows **OR **Ubuntu, make sure to save it to the NTFS partition.

That's how **I **do things. There is another way, I believe, involving setting-up a 'Home' partition on your external drive; but AJ, & others like him who have more experience with Linux than me, will be better able to advise you on that one.

Regards,

Mike.

---

### Post by oldfred on 2014-09-26
If you want to share the NTFS partition you need to permanently mount it with fstab or else it will not work correctly. And in Windows you need to be sure it is not hibernated or it will restore an older version of files making anything from UBuntu disappear.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

Mounting NTFS partition:
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
[       ]("http://ubuntuforums.org/showthread.php?t=2227574") [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)

---

### Post by kamhagh on 2014-09-27
```
 while(true)
     thank("all");
```

:)

---

