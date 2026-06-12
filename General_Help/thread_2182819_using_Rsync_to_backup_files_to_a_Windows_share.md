---
title: "using Rsync to backup files to a Windows share"
date: 2013-10-22
forum: General Help
---

### Post by Q64LzQm on 2013-10-22
Environment 
VM Windows Server 08 - File Server
VM Ubuntu desktop

I am running Rancid to back up the configurations of each of our switches and it stores the files locally on the Ubuntu workstation. This is working correctly using a Crontab schedule.

I have mounted the Windows Share using CIFS/ Samba. And installed and configured GAdmin-Rsync and configured the profile for the backups to work. And I have added the script that GAdmin-Rsync created to Crontab. 

Now the only problem I am having is that the only way for Rsync to copy the files to the Windows Share is if I sudo and input the sudo password. To properly run the crontab schedule I can not have this. How would I go about allowing a certain user "rancid" access the windows share without inputting a sudo password?

---

### Post by Lars Noodén on 2013-10-22
You can allow specific combinations to be run by sudo without a password.  You need to be very precise with what you put in /etc/sudoers

```

%backup ALL=(ALL) NOPASSWD: /usr/bin/rsync -a /home/q64lzqm/ /smb/foo/

```

That allows anyone in the group "backup" to run just the program rsync with just the one option -a on just the two directories named.  

Be sure to use visudo for editing or else test sudo before closing /etc/sudoers or both.  A mistake there will lock you out.  See the manual page for [sudoers](http://manpages.ubuntu.com/manpages/raring/en/man5/sudoers.5.html) for more details than you need.

---

### Post by Q64LzQm on 2013-10-22
Excellent! Thank you very much this worked perfectly! 100 thumbs up!

---

### Post by SeijiSensei on 2013-10-22
Remember that any symlinks and hidden dot-files may not be correctly transferred to the Windows share.  You can tell rsync to ignore symlinks and copy the linked file instead, but there is no solution I've found for dot files.  

This may have something to do with the version of Windows Server my client is using; they're still on 2003.  If you find that these problems don't exist with Server 2008, I'd like to hear about it.  I believe that there have been some changes to NTFS that may be more compatible with POSIX file systems like Linux uses.

If you want to automate the backup process, put an entry in /etc/crontab or in root's crontab.  Then it will automatically run with root privileges rather than messing with sudo.

---

### Post by Lars Noodén on 2013-10-23
One way to include dot files would be to use --filter.

```

rsync -a --filter='+ .' [/i]source[/i] *dest*

```

It's not obvious nor convenient to remember, so I usually have the important ones symlinked elsewhere.

---

### Post by SeijiSensei on 2013-10-23
The problem with dot files is a limitation in at least some versions of NTFS.  I don't think changing the rsync syntax will fix that.  My rsync sessions try to copy over the files, but get errors back from the NTFS target.

---

