---
title: "Thunderbird profile share Windows / Ubuntu"
date: 2018-08-31
forum: General Help
---

### Post by michaelbr on 2018-08-31
I just installed Ubuntu 18.04, I've been using most of the time Windows, therefore my Thunderbird has lots of folders/emails in Windows, is it safe to use the same profile/folder under Ubuntu? When I was using on and off Ubuntu 12, I remembered sharing FF/Opera profile between Windows/Ubuntu, but since then lot of things have changed, and I'm not sure if it's safe to share those profiles again.

---

### Post by walts48 on 2018-08-31
See [http://kb.mozillazine.org/Sharing_profiles_-_mail](http://kb.mozillazine.org/Sharing_profiles_-_mail)

---

### Post by michaelbr on 2018-08-31
Thanks walts48 for your reply, my understanding is that you can share safely TB profile under the same OS, but I'm trying to share between Windows & Ubuntu, is it safe?

---

### Post by walts48 on 2018-09-01
Anything in the kb article about sharing between different OS's?

Doesn't look like it is recommended or supported.

The calendar extension Lightning has to be installed to match each OS, so the user would probably have a problem with using that extension with a shared profile.

---

### Post by michaelbr on 2018-09-01
No, the article did not mention any OS, just said that you can share the profile and how to share it. I'm not using Lightning, I'm using Rainlendar as my calendar apps.

---

### Post by oldfred on 2018-09-01
I have not shared with Windows since XP.
But back then had both Firefox & Thunderbird profiles in a shared NTFS data partition.
While I updated versions, they were not always exactly the same in Windows & Linux.
I now share profiles with multiple Ubuntu installs in a /mnt/data ext4 formatted partition.

But newer Windows uses fast start up which is just hibernation. And it turns it back on with updates. 
All NTFS partition then have hibernation flag set and Linux NTFS driver will not automount.

So you must make sure fast start up is off, and when you get issues loading it in Linux, go back into Windows and turn fast start up off again. Also if NTFS needs chkdsk Linux will not mount a NTFS partition. And you can only run chkdsk from Windows or a Windows repair disk.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by michaelbr on 2018-09-02
I just shared my TB profile and data folder in Windows 8.1 & Ubuntu 18.04, seems nothing is broken, will check for few days to see if there's odd behavior.

---

