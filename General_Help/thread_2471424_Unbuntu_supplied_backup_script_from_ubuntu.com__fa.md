---
title: "Unbuntu supplied backup script from ubuntu.com/  failed?!?"
date: 2022-01-29
forum: General Help
---

### Post by chris53 on 2022-01-29
Hi Everyone,

I just copied the back up script from unbuntu.com --> [https://ubuntu.com/server/docs/backups-shell-scripts](https://ubuntu.com/server/docs/backups-shell-scripts).   I just copied and pasted the code.   Then I added a little bit of coding just to make the log file a little more verbose.  

I looked at the log file and I have pasted the output below:
**Backing up /home /var/spool/mail /etc /root /boot /opt to /home/mylastname/Desktop/Development/Backups/mylastname-XPS-13-9360-Saturday.tgz**
**Sat 29 Jan 2022 07:51:01 PM EST**

**tar: Removing leading `/' from member names**
**tar: Removing leading `/' from hard link targets**
**tar: /home/mylastname/Desktop/Development/Backups/mylastname-XPS-13-9360-Saturday.tgz:[SIZE=5]* file changed as we read it*[/SIZE]**
**The     backup failed...  Please Check.**

**Sat 29 Jan 2022 07:58:24 PM EST**
**total 12G**
**-rw-r--r-- 1 root root 12G Jan 29 19:58 mylastname-XPS-13-9360-Saturday.tgz**
And this is the code that I added.   Just to check the return code of the Tar process.   Thats it..
**# Backup the files using tar.****tar czf $dest/$archive_file $backup_files**
**if [ $? = 0 ]; then**
**     echo "The backup Completed Successfully!"**
**else**
**     echo "The backup failed...  Please Check."**
**fi**


Maybe this is because I wrote the Tar file to my harddrive  (I was going to move it to an external drive when it completed)  
So is this Tar file ok??   Has anyone used this script and found out the hard way?   

I'm happy to paste the entire script if you like but just a few echo's thats it.

Thanks,
Chris

---

### Post by HermanAB on 2022-01-30
You are backing up a mail spool file?
There may be in or outgoing mail while your backup is running, therefore the file changed message.  The obvious solution is to stop the mail daemon before doing the backup.

---

### Post by chris53 on 2022-01-30
> **HermanAB said:**
> You are backing up a mail spool file?
There may be in or outgoing mail while your backup is running, therefore the file changed message.  The obvious solution is to stop the mail daemon before doing the backup.

I just copied and pasted the code, I wondered why that was necessary myself but I figured if it was there it may be needed for something that I was not aware of.   I'll try removing that portion a re-run the backup and see if that solves the problem.   I cant think of anything from spool file that would be critical but I could be wrong.   

Thanks,
Chris

---

### Post by HermanAB on 2022-01-30
BTW for various reasons, rsync makes better backups than tar.

---

### Post by oldfred on 2022-01-30
I am a bit surprised they have a script using tar.
It is old school. tar - tape archive
It was ok for smaller systems, but now many other tools are better.

We typically do not suggest backing up Ubuntu system as that is easy to reinstall. But you backup your files including /home, data, list of installed apps, perhaps some files in /etc where you manually edited settings and any server type apps in / (root) like database or web apps.

What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 

My rsync is not really a backup as it is just a copy. A copy may lose files that change when you want older version, or a deleted file.
But I rsync to multiple flash drives and copy most critical files to DVD. While ok for me as a home user, not what theFu would recommend as professional way to backup.

---

### Post by chris53 on 2022-01-30
> **oldfred said:**
> I am a bit surprised they have a script using tar.
It is old school. tar - tape archive
It was ok for smaller systems, but now many other tools are better.

We typically do not suggest backing up Ubuntu system as that is easy to reinstall. But you backup your files including /home, data, list of installed apps, perhaps some files in /etc where you manually edited settings and any server type apps in / (root) like database or web apps.

What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 

My rsync is not really a backup as it is just a copy. A copy may lose files that change when you want older version, or a deleted file.
But I rsync to multiple flash drives and copy most critical files to DVD. While ok for me as a home user, not what theFu would recommend as professional way to backup.

Thanks Fred.   I will check out the links and modify appropriately. 
Chris

---

### Post by chris53 on 2022-01-30
Just an FYI..   I did some looking in to my Tar issue "file changed as we read it".    

"[COLOR=#202124][FONT=Roboto]In this case, you are trying to archive into backup. ... tar command interprets that backup. tar is also one of input files, but is being changed [/FONT][/COLOR]**during archiving, so throwing the error. To fix the error, make sure that the output tar file does not belong to the file(s) being archived."**

---

