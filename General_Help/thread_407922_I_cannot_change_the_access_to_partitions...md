---
title: "I cannot change the access to partitions.."
date: 2007-04-12
forum: General Help
---

### Post by billdotson on 2007-04-12
I have gparted installed and I run it w/ sudo gparted.  I made a ext3 partition on /dev/sdb6 then I made a mount point /media/Windows_backup2 and mounted it.

I cannot make a file or folder in there so I went to the terminal and ran chown sgtmattbaker /media/Windows_backup2 (after cd ..'ing back twice)

and then I ran chmod 777 /media/Windows_backup2

I have done the same thing when it is unmounted as well.  

The owner and permissions do not change and I still cannot write to it.

I have also tried doing sudo nautilus and changing them manually while it is mounted and not.  Nothing.

Thanks.

Also what is man chmod and man chown not reallt tell me anything?? it doesn't even show the numbers that are options..

---

### Post by DoubleQuadword on 2007-04-12
> **billdotson said:**
> I cannot make a file or folder in there so I went to the terminal and ran chown sgtmattbaker /media/Windows_backup2 (after cd ..'ing back twice)

and then I ran chmod 777 /media/Windows_backup2

Both as root user?

Nevertheless, check this thread: [http://ubuntuforums.org/showthread.php?p=2437617&posted=1](http://ubuntuforums.org/showthread.php?p=2437617&posted=1)

Regards.

---

### Post by aysiu on 2007-04-12
Please don't use *sudo nautilus*. ```
gksudo nautilus
``` is the proper way to do it. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

As for changing ownership of a partition that's now Ext3, you need to use the *-R* flag to make the *chown* recursive (that is, applying to all the files and folders within the top-level directory): ```
sudo chown -R bill:bill /media/Windows_backup2
sudo chmod -R 755 /media/Windows_backup2
``` If *bill* isn't your username, put in your real username. More details here:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

