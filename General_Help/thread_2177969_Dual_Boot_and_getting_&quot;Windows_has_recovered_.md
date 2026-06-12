---
title: "Dual Boot and getting &quot;Windows has recovered from a serious error&quot; What's wrong?"
date: 2013-10-01
forum: General Help
---

### Post by 777funk on 2013-10-01
Curious what I could be doing wrong here. I'm getting this message most times I boot into Windows... especially if it's been a while. I mount the Windows 'C drive' from Ubuntu so I don't have multiple My Documents, My Pics, etc. 

Anyways, any help is greatly appreciated. I don't want to mess anything up of course.

---

### Post by oldfred on 2013-10-01
Are you hibernating? Usually then you cannot even mount the NTFS partition to write into it.

Do you have a shared NTFS data partition as Windows often does not like a lot of writing into its system partition. 

The Linux NTFS driver exposes all the hidden files & folders that Windows usually hides and it is easy for a user to accidentally do something they should not. I used to turn on show the hidden files in Windows and corrupted system on regular basis. I would often click on wrong folder and move too quick and it would instantly move a system folder under another. Once I learned that was a problem it was easy to fix from another system.

---

### Post by coffeecat on 2013-10-01
> **777funk said:**
> I mount the Windows 'C drive' from Ubuntu so I don't have multiple My Documents, My Pics, etc. 

Not a thing I like to do. I'd recommend you think about setting up a separate NTFS partition for shared data. To get round the problem of multiple document folders, etc, you can symlink from the data partition to your home in Ubuntu (so long as you mount the NTFS partition by means of /etc/fstab) and you can set up shortcuts in your Windows home folder to do much the same thing.

---

### Post by 777funk on 2013-10-02
Excellent and thank you! So what would be best to do now? Here's what I'd suspect:

1. New NTFS partition
2. Move all Windows to new folders in this partition
3. automount this partition in Ubuntu
4. Create the Symlinks in Ubuntu
5. Create shortcuts in Windows

Question (besides if that's the correct steps to take), can I somehow redirect the Windows Doc Folders to the new locations so that I can just click the original doc folders like nothing ever happened?

---

### Post by oldfred on 2013-10-02
Found this but no idea if it works. I used to use XP but now have no Windows.

       Shared NTFS partition but some of the Linux instructions could be better:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

Better mount in fstab:
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

