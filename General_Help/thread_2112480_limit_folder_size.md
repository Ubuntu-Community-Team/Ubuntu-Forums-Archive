---
title: "limit folder size"
date: 2013-02-04
forum: General Help
---

### Post by conradin on 2013-02-04
Hi All, 
I have an FTP server that has multiple users with write permissions.
For all users, (present and future), I want the ftp shared folder to not exceed 100MB. All users share the same root folder. 
If the folder ever becomes full, I want users to get a write error message or something.
Is this a quota issue?
I do not want to repartition my File-system.

---

### Post by conradin on 2013-02-04
[http://www.linuxquestions.org/questions/linux-server-73/directory-quota-601140/](http://www.linuxquestions.org/questions/linux-server-73/directory-quota-601140/)

I found this thread helpful in creating the virtual-disk space, but I am not sure about how to set user permissions. I was thinking about using the usermod command to give new users access to the folder. But I am not sure if that is the best way. 

The ftp users are all only ftp users. they don't log in locally, nor should they access any other service besides the ftp server. I was using the user mod command to give users access to the same folder, but maybe there's a better way?

---

### Post by LewisTM on 2013-02-04
What you seek can be obtained with XFS project quotas. You will have to reformat your partition with XFS. Don't worry, you won't suffer any penalty, it's basically as good as ext4 but has a few more powerful features, including the ability to restrict given directory sizes.

First install **xfsprogs** package to get the necessary utilities. Then mount your xfs partition in fstab with the **pquota** parameter. Next, create /etc/projects and /etc/projid where the project info - the restricted pathname(s) - is found. If you have a single shared folder to restrict, you would have only one project. It might not work as a root FTP folder but it could be moved to /<ftp_root>/shared for example.

The necessary syntax can be found with [FONT="Courier New"]man xfs_quota[/FONT], **xfs_quota** being the main tool for manipulating quotas in XFS filesystems.

More info:
[http://oss.sgi.com/projects/xfs/training/xfs_lab_05_quotas.pdf](http://oss.sgi.com/projects/xfs/training/xfs_lab_05_quotas.pdf)
[http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-104-4/index.html](http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-104-4/index.html)

Cheers!

---

