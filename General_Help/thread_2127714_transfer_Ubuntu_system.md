---
title: "transfer Ubuntu system"
date: 2013-03-20
forum: General Help
---

### Post by Ice Chua on 2013-03-20
**[FONT=arial][SIZE=5][SIZE=2][B][[COLOR=#800000]How do I move or copy my entire Ubuntu system to a different hard disk?[/COLOR]]("http://askubuntu.com/questions/151127/how-do-i-move-copy-my-entire-ubuntu-system-to-a-different-hard-disk")**[/SIZE][COLOR=#800000]:confused::confused::confused:[/COLOR][/SIZE][/FONT][/B]

---

### Post by oldfred on 2013-03-21
Changed font size. Seemed like you were shouting at us. 

Will old hard disk still be installed in same system? 
Is new disk smaller or larger than old disk.

Some suggest clonezilla.
       Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

But if you are going to use old drive in same system you will have problems of duplicate UUIDs, and have to reinstall grub. I suggest copy /home to a new separate partition if not separate already, export list of installed apps, and do a clean install. My backup assumes I will do a new clean install and restore my data, so it is the same thing as you want.

      
 Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541

      [/URL]
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    [URL="http://ubuntuforums.org/showthread.php?t=1748541"]
[/URL]

---

