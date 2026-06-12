---
title: "Understanding user and group permissions"
date: 2019-08-14
forum: General Help
---

### Post by 5circles on 2019-08-14
I know there is a lot of information online about user and group permissions, but I'm having a tough time deciphering the symptoms I've been seeing, and the apparent resolution.  I'd love to find some sort of comprehensive tutorial with explanations and best practices - and not just responses of "already answered".  This post is based on experiences with PhpStorm, both Windows and Ubuntu, with deployment on a dedicated Ubuntu box, or Ubuntu running on VirtualBox.  The most recent experience which stimulated the post is setting up Laravel.  I'll try to minimize any comments or questions related directly to PhpStorm or Laravel.  I'll clarify any differences between the two deployment servers - actually I don't think there are any.

I always deploy to a Ubuntu box, whether it's for testing/development, staging, or (eventually) actual deployment.  The username I want to use is mine - mikep.  I can't use www-data because Windows only allows a single set of credentials to be connected to a single network device.  (That's a stupid limitation IMO - claimed to be for security reasons - but I can't do anything about it, so I can either connect as mikep or www-data.

Files created on either server by uploading with PhpStorm, when connected as mikep (which is the only way I've connected to the dedicated box), are all owned by mikep with group mikep.

mikep is part of the www-data group, but I guess this is a Secondary group membership when the add to a new group is done with adduser user group.  Is this correct?

_**What is a Secondary group anyway (and is it the same as Supplemental group - both terms are used in help for programs that manipulate users)?**_

The problem I was having with Laravel is that permissions for the 'storage' directory and subdirectories was incorrect.  The result was that the first access to the Laravel directory gave an error about not being able to open the log file - "*The stream or file "/var/www/../../storage/logs/laravel.log" could not be opened: failed to open stream: Permission denied*" .  This actually means that the file could not be created.  

So what does it mean that "mikep" is a member of the "www-data" group that runs the webserver?  Not much, it appears.  I don't know if Laravel is checking for ownership, not just permissions.  But at this stage of experiments, something was preventing the file from being created.  

Here's what I tried:

1. Made www-data part of the mikep group with "sudo adduser www-data mikep"  .  I was then able to touch files in the storage and storage/logs folder, but Laravel still generated the same error.
2. ran "sudo chown -R :www-data /var/www/../../Laravel_1".  This allowed the Laravel page to be displayed without error, suggesting that permissions for files and directories in the hierarchy were incorrectly set earlier.  The problem with this - it seems to me - is that new files or directories created by PhpStorm and uploaded would still have ownership as "mikep:mikep" which is likely to cause problems.
3. ran "sudo chmod -R g+s /var/www/../../Laravel_1" per something I found online to set the setgid bit.  This appears to work as far as Laravel is concerned, and probably including new files, but it looks messy with owner:group for new files and also for the ls output after the  setgid bit.
4. Finally, which I think is the right approach  - "sudo usermod -g www-data mikep" to change the primary group for my user to www-data.  Logging out and back in didn't have the right effect, but restarting did the trick. Now files created by user mikep - whether on the machine or through a mapped drive - are mikep:www-data.

I think this last approach is the best because it only means making the change once, and having www-data group ownership makes sense.

Am I correct, or is there a better way?  And, as I wondered at the beginning, why does Primary group seem to be a mystery?  I've been using Ubuntu for a long time, and I've never really been exposed to explanations.

Thanks
Mike

---

### Post by TheFu on 2019-08-15
Fewer descriptions.   More facts, please.  Run commands, show output. Use code tags so it looks the same here as it does in a terminal.
When there are permission issues, we need the ls -al for the files and the directory where those files reside. For example:
```
blog44:/var/www/lpi.example.com$ ls -al
total 28
drwxr**ws**r-x  6 tf tf   4096 Jun 29 06:43 .
drwxr-xr-x 14 tf root 4096 Jun  6 12:24 ..
drwxrwsr-x  2 tf tf   4096 Oct 30  2017 2017-Fall
drwxrwsr-x  2 tf tf   4096 Jun 29 06:49 2017-Spring
drwxrwsr-x  2 tf tf   4096 Jan 19  2018 Books
drwxrwsr-x  2 tf tf   4096 Sep 26  2017 LPI-Certs-Summary
-rw-rw-r--  1 tf tf   1077 Jun 29 06:43 README.txt

```
This is a static website served by nginx.  My userid is 'tf' (thefu is too long). ;)  

**ps** shows nginx running ....
```
**www-data**  1522  1521  0 Aug03 ?        00:03:06 nginx: worker process
www-data  1523  1521  0 Aug03 ?        00:00:05 nginx: cache manager process

```
So the process is www-data owned.  For www-data to access the files above, the "other" permissions need to allow read for the files and the parent directory and all parent directories to /.

It is the setgroupid bit and it forces any newly created files inside a directory to retain the same group as the parent.  *chmod g+s {directory}* is how you set it. It doesn't work for files, just directories. Only the directory owner can control permissions.  If a directory as write and setgroupid and execute permissions, then any member of that group can create new files inside it.

A userid can be a member of hundreds of groups.  Only the primary group is special, sometimes called the "effective gid". Any other groups are all equal. I suppose they can all called secondary, if you like.  There are some processes which have limitations for the number of groups the process will notice, but those don't kick in until after 20 groups. The only one I know about having limitations is NFS. Bash doesn't and I've never heard of any shell having a limitation.  If you like, you can temporarily change the primary group using the **newgrp** command.  This is almost never needed, but it can be convenient if you add a new group to a userid and don't feel like logging out to get your session to recognize the newly added group. Only the shell/window where you run newgrp would see it.  For most people, it is just easier to logout and login again to keep confusion to a minimal.

BTW, MS-Windows doesn't have any limitation on the use of different accounts to connect to Ubuntu. People have been using putty for decades to connect from Windows to Unix systems, including Linux.  Any userid on the remote system that allows ssh, can be used for any ssh-based access. Same applies for CIFS/Samba and every other protocol I know.  I suspect the real limitation is with the software you are using, not the system on either side.  The way to get updates to a server are usually either rsync or using the VCS to get a read-only copy of everything.

/var/www/../../storage/logs/laravel.log is the same as /storage/logs/laravel.log. 
Which ever userid is running the process that is trying to write to that file (or create the file), needs to have permissions to write to it. To create a file inside any directory, the userid running the process must have write privileges on the directory or by the group membership.

 /var/www/../../Laravel_1 is the same as /Laravel_1.  If that isn't clear, please look up absolute vs relative directories.
[https://www.funtoo.org/Linux_Fundamentals,_Part_1](https://www.funtoo.org/Linux_Fundamentals,_Part_1) overs absolute and relative paths in lesson 1. BTW, Windows works exactly the same way.

Should any web files be writable by www-data?  From a security standpoint, I'd say most should not and only those specifically required to allow write access for a webserver should, but no 1 extra file.  The risk factors for the system would go into this answer.  I don't trust php webapps and don't allow them to be directly available over the internet.  For some uses, I have deployed php webapps, but they are only available outside the LAN through a VPN or ssh-tunnel connection.  That is my mitigation method. You should decide on yours.

Every process has a userid, effective groupid and groups.  Access to files and directories are based those things at runtime.  Your userid, when you enter commands in the shell/bash, inherits the userid and groups. That is what controls access to files and directories. In Unix, everything is either a process or a file.  A process is anything that shows up in the process table - ps, top, htop, whatever tool that looks at the process table.  EVERYTHING else is a file.  Access to everything else is controlled by the same Unix permissions model.

Hopefully, this will get you over the hump of understanding.

---

