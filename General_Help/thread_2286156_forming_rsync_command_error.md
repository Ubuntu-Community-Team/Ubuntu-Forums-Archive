---
title: "forming rsync command error"
date: 2015-07-10
forum: General Help
---

### Post by Drenriza on 2015-07-10
Currently i am trying to make a rsync command to take a backup of my local files and place them on a remote system.

But rsync only executes the mkdir command and build the directory tree from include.cfg, but it doesn't transfer the actual files from the directories in include.cfg file.

```
rsync -e ssh -a --compress --rsync-path="mkdir /new/remote/backup/directory && rsync" --delete --files-from=/path/include.cfg --exclude-from=/path/exclude.cfg / remoteBackupServer:/path/created/by/mkdir
```

Anyone who can see where i have done wrong and point me in the right direction?

Thanks on advance

---

### Post by TheFu on 2015-07-10
Do the **mkdir -p** on a separate command.
BTW, rsync defaults to ssh now. Don't need to specify it. I think compression is used for remote rsync too (not local).

The generic for of rsync is
rsync {options} {source} {target}

When I have problems with a command, I simplify and test until something works, then add back in 1 part at time.

BTW - rsync is great for mirrors, but really not so great for backups because it doesn't retain file permissions as part of the versioning. There are other reasons too.  You probably want **rdiff-backup** instead. [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)  rdiff-backup has an rsync-like command structure.

For both commands, it is generally best to either include or exclude file-patterns.  Don't do both.

---

### Post by papibe on 2015-07-10
Hi Drenriza.

A few thoughts:

Use mkdir with the -p option as TheFu suggests.

When you use --files-from, the -r option (which is included in -a) it is forced off. You need to add it explicitly if 'include.cfg' contains directory names.

The file 'include.cfg' should contain names relative to the source directory. For instance, if you want to back up /home, you should have a line that says 'home/' not '/home/'.

If you post the content of 'include.cfg'  and 'exclude.cfg', we may offer more suggestions.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Drenriza on 2015-07-13
Thanks for the reply @papibe

Thanks for the reply @TheFu

> BTW - rsync is great for mirrors, but really not so great for backups because it doesn't retain file permissions
-p
-o
-g
-t
Preserve the permissions, owner, group and times. Soo i am not a hundred percent sure what you mean with it dosent retain file permission, can you elaborate your answer a little more?

Thanks on advance
Kind regards.

---

### Post by Drenriza on 2015-07-13
From the feedback i got (thanks guys) i have edited the command to

```
rsync -v -e ssh -a --recursive --compress --delete --rsync-path="mkdir /new/remote/folder.full.dir && rsync" --files-from=/include.cfg --exclude-from=/exclude.cfg / remoteServer:/new/backup/folder/made/by/mkdir
```

And edited the include.cfg & exclude.cfg with no leading /

Which from first glans (still transferring) now works as intended for creating a full backup

**Added**
For creating the incremental backup i run
```
 rsync -v -e ssh -a --recursive --compress --rsync-path="mkdir /new/remote/folder.inc.dir && rsync" --link-dest=/previous/full/backup/folder.full.dir --files-from=/include.cfg --exclude-from=/exclude.cfg / remoteServer:/new/backup/folder/made/by/mkdir
```

---

### Post by TheFu on 2015-07-13
> **Drenriza said:**
> 
Preserve the permissions, owner, group and times. Soo i am not a hundred percent sure what you mean with it dosent retain file permission, can you elaborate your answer a little more?

See you got it working - GREAT!

Backups need to be versioned.  Having 1 mirror is NOT a backup.  Having daily backups over the last 30-120 days and capturing all the changes to the data and the permissions (owner, group, ACLs) in that time is important.  There are backup tools available that can hold 30 days of daily backups for 10%-20% more storage than the full copy. That is all.

BTW, we all start out using rsync for "backups" - usually move to an rsync-based script that uses hardlinks for versioning, then see that permission changes are lost, and finally move onto a backup tool designed specifically for backups. I did.

---

### Post by Drenriza on 2015-07-15
Thanks for the reply @TheFu

> usually move to an rsync-based script that uses hardlinks for versioning
The rsync command actually does hardlinks from the previous full backup to the new incremental backup, aslong as you give it the folder name of the full backup to hardlink from.

> then see that permission changes are lost
Do you mean if for example i make a full backup with a file named
test.txt with 755 permissions.

Then change the permissions (on the server backed up from) to 744 and make a incremental backup (while not changing the file content), than these permission changes wont be recorded as is, but as 755?

But a real good question i have here is than.

How do you verify the hardlinks from the incremental backup, back to their full backup??
I know i can look at the inode, for example with 
```
ls -i
```
but is their a easy way to link these back to the source?

> and finally move onto a backup tool designed specifically for backups. I did.
What backup tool do you currently use?

---

### Post by TheFu on 2015-07-15
You should verify the answers yourself.  Also - please test changing the owner, the group, and adding ACLs - that's 3 more tests. See what happens.

I use rdiff-backup, but there are lots of solutions that handle this correctly.  Heck - tar can.

---

### Post by Drenriza on 2015-07-15
When we are talking about preserving file attributes.

-a excludes -H -A and -X

But how does -H, -A and -X work, and can they be used in conjunction with -a?

**-H**
If you have a hardlink and you copy this with rsync, will rsync than just point to the same inode on the disk to where the hardlink originates from?
If we say its a pointer and not a file, than if the inode changes the hardlink will break. Also (guessing) you cannot than copy this backup to a different disk (disaster recovery) since the inode will not exist or contain different info for another file.

[B]-A
[/B]What does ACLs imply in Linux? In my world ACL is short for Access Control Lists, but i havent come across any.I did read some about what ACL in Linux is here [https://wiki.debian.org/Permissions](https://wiki.debian.org/Permissions) but it does not say alot about it**. **Like how they work or where they are stored.
**-X**
When we talk about extended attributes, are we than talking about for example the SGID, SUID and sticky bit?

Rsync also has a --backup and --backup-dir=/ option, which by its name is interesting but the man page has very little information about them.

---

### Post by papibe on 2015-07-15
> **Drenriza said:**
> But how does -H, -A and -X work, and can they be used in conjunction with -a?
Yes. If you have 'rsync -aH', you have the defaults of -a, but then you turn on hard links.
> **Drenriza said:**
> 
**-H** If you have a hardlink and you copy this with rsync, will rsync than just point to the same inode on the disk to where the hardlink originates from?
No. If 2 files are hard linked (same inode) on the source, they also will be on the destination, but not related to the source. For example:
```
$ mkdir tmp
$ echo "this is a file." > tmp/first_file.txt
$ ln tmp/first_file.txt tmp/other_file
$ ls tmp
first_file.txt  other_file

$ stat -c %i tmp/first_file.txt 
**[COLOR="#FF0000"]2230100[/COLOR]**
$ stat -c %i tmp/other_file 
**[COLOR="#FF0000"]2230100[/COLOR]**

$ rsync -avH tmp/ tmp2/
sending incremental file list
created directory tmp2
./
other_file
first_file.txt => other_file

sent 189 bytes  received 87 bytes  552.00 bytes/sec
total size is 32  speedup is 0.12

$ ls tmp2
first_file.txt  other_file

$ stat -c %i tmp2/first_file.txt 
**[COLOR="#0000CD"]2230102[/COLOR]**
$ stat -c %i tmp2/other_file 
**[COLOR="#0000CD"]2230102[/COLOR]**
```
> **Drenriza said:**
> **-A** and **-X**
Both extended attributes and ACL are extensions to a regular file system. Chances are you are not using any of them. By default rsync, and even regular cp, doesn't transmit them.

Does that help?
Regards.

---

### Post by Drenriza on 2015-07-16
Thanks for the reply @papibe it helps a lot.
I will try and make a slick script for checking that the incremental files transfered by rsync are real files and that files != transfered are linked files,
and than output the amount of space used by the incremental backup (files that don't point to the same inode number) and a % of linked files.

[B]User and groups
[/B]This is an interesting predicament. When rsync transfer files it does not preserve the owner:group for files and directories.

From what i can gather from the web a few criteria needs to be in place before rsync can actually do that.
[LIST]
[*]The user and group must exist on both source and destination system. 
[*]You must run the rsync command as root from source, or a user with root privileges. 
[*]You must initiate a (root) user on the destination system with root privileges. 
[/LIST]

But i cant seem to solve the issue, of actually preserving user:group. For test i initiate rsync on the source system as root,
on the destination i initiate a normal user that has been added to /etc/sudoers with ALL=(ALL:ALL) ALL (test purposes).

I also tried adding --super to my rsync command so it now looks like
```
rsync -v -e ssh -a --super --recursive --delete --compress --rsync-path="mkdir /new/remote/dir.full.dir && rsync" --files-from=/include.cfg --exclude-from=/etc/exclude.cfg / remoteHost:/new/remote/dir.full.dir
```
> -o, --owner
              This option causes rsync to set the owner of the destination file to be the same as the source file, [B]but only if the receiving rsync  is
              being  run  as the super-user[/B] (see also the --super and --fake-super options).  Without this option, the owner of new and/or transferred
              files are set to the invoking user on the receiving side.

              The preservation of ownership will associate matching names by default, but may fall back to using the ID number in  some  circumstances
              (see also the --numeric-ids option for a full discussion).

       -g, --group
              This  option  causes  rsync to set the group of the destination file to be the same as the source file.  [B]If the receiving program is not
              running as the super-user (or if --no-super was specified), only groups that the invoking user on the receiving side is a member of will
              be preserved[/B].  Without this option, the group is set to the default group of the invoking user on the receiving side.

But rsync still change the owner:group to the initiated destination user:group, instead of preserving the source user:group
> rsync: chown "/path/to/file/rsync/copy/to/remote/file.txt" failed: Operation not permitted (1)

Edit.
I have found what seem like good answers from various sites, but i don't quote know how to implement them (yet).
> You need a method to supply the password to sudo.  An askpass program is designed to ask for passwords when the normal mechanisms aren't available.  Setting up sudo to not require a password to run rsync as your userid is one option.
  
I normally configure** key based login with appropriate restrictions**  for cases like this.   If you configure a restricted key that an only  run rsync as root then this kind of thing gets easier to do.  **Another alternative is to use an rsycnd process to handle the remote requests.**  The configuration provides a variety of restrictions that can be applied.



I very much like the key based login method, but how does one enforce only limited privileges to a key based login?

 
Any feedback are most welcome.
Thanks on advance to all

---

### Post by papibe on 2015-07-16
The simplest, but not safest, way to preserve all attributes would be to use root as a remote user:
```
rsync -av source/ root@remote_server:/path/to/destination
```
However, this would open all kinds of security issues. In general, it is not recommended to allow remote connections to the root account.

The standard and easiest way to work this out is to:
[LIST]
[*]'tar' the source first
[*]rsync the resulting tar file instead, and
[*]in the remote server, untar as root (sudo tar xvf ....)
[/LIST]
'tar' saves the ownership, and permissions as metadata. So if you untar as root, it would assign them correctly. If you untar as a regular user, it would probaly keep permissions, but it would assign ownership to the user.

The down side of this method, is that you need the space for the whole tar file on the destination, before even transmitting it.

There's another option, but it is a little bit of a hack. You could run 'sudo rsync' instead of regular rsync:
```
--rsync-path="mkdir -p /new/remote/dir.full.dir && sudo rsync"
```
Then in the remote server, you could add a sudoers entry disabling the password requirement for the rsync command.

Hope it helps. Let us know if you have more questions.
Regards.

---

### Post by Drenriza on 2015-07-17
Thanks for the reply @papibe

Yes i also looked at doing the rsync "hack". But what would the difference be from using the "hack" vs using root?

rsync would have root privileges and be able to copy of any file on the system.

Using root will make you able to try bruteforce attempts on the user (because you know it exist). But with a ssh-keyfile setup and disable ssh password logins, you would get past that.

Its a head scratcher

---

### Post by Lars Noodén on 2015-07-17
> **Drenriza said:**
> Its a head scratcher

I tried describing how to use rsync with sudo here:

[https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo)

Step #4 requires paying attention to what ssh sends.  You could also lock sudo down on the client side too using somewhat similar methods.  Once sudo is locked down, you can further lock things down by specifying the exact parameters allowed in the public key on the server using *command=*

---

### Post by papibe on 2015-07-17
Great guide! Thanks Lars Noodén. :D

---

### Post by Lars Noodén on 2015-07-18
You're welcome.  If there is anything missing, unclear or wrong, I can fix it.  

Drenriza, does it match what you are trying to do with rsync?

---

### Post by Drenriza on 2015-07-18
Thanks for the reply @Papibe and @Lars Nooden

This section of the guide
> Step 4: Adjust **/etc/sudoers** so that the backup account has **enough  access to run rsync** but **only in the directories it is supposed to run**  in and without free-rein on the system.

How is this done? I dont see it in the guide unfurtiantly.

Thanks on advance
Kind regards

---

### Post by Lars Noodén on 2015-07-18
If you run rsync specifying the -v option for ssh when going about your task:  

```

rsync -e "ssh -t -v" --rsync-path='sudo rsync' source/ root@remote_server:/path/to/destination

```

That will give you debugging output and there you will see the rsync command with the exact options specified.  Then that can be fed into [sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) on the target machine for a non-privileged account.  

In the example in the wikibook, it was like this:

```

debug1: Sending command: sudo [color=blue]rsync --server --sender -e.iLs . /var/www[/color]

```

It is that part *rsync --server ...* that needs to go into sudoers for the non-privileged account.

---

### Post by Drenriza on 2015-07-18
**Thanks** for the reply @Lars Nooden

Think i understand now what you mean, i will try out your suggestion / guide and see if i can make it work as such :)

---

### Post by Drenriza on 2015-07-20
@Lars Nooden

I got a question about how to do the sudoers file and hope you or someone else can help me out with my understanding.

I executed the following command
```
rsync -v -e "ssh -t -v" -a --recursive --compress --rsync-path="mkdir /new/remote/backup/parent/date.dir && sudo rsync" --files-from=/include.cfg --exclude-from=/exclude.cfg / remoteServer:/new/remote/backup/parent/date.dir
```

And got the following debug output
> debug1: Sending command: mkdir /new/remote/backup/parent/date.dir && sudo rsync --server -vlogDtprRze.iLs . /new/remote/backup/parent/date.dir

Would i need to make separate statements for mkdir and sudoers, so mkdir can make the child folder in the parent folder, and rsync can access it?
I am also wondering how i should format it in sudoers.

Example
**rsync**
```
rsync --server -vlogDtprRze.iLs . /new/remote/backup/parent
```
And than through ssh send the command
```
&& sudo rsync --server -vlogDtprRze.iLs . /new/remote/backup/parent/date.dir
```

**mkdir**
```
rsync ALL=/bin/mkdir #Define parent folder to be able to make child folder??
```

Hot / Cold / Antarctica ? xD

---

### Post by Lars Noodén on 2015-07-20
Yes, I think you need separate entries in [sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) on the server for mkdir and rsync.  But for mkdir, it would be good to limit which directories can be created.  

```

rsync ALL=(ALL:ALL) /usr/bin/rsync --server -vlogDtprRze.iLs . /new/remote/backup/parent/date.dir
rsync ALL=(ALL:ALL) /bin/mkdir /new/remote/backup/parent/date.dir 
```

If the directory to be created is not "date.dir" literally but some pattern, then use [globbing](http://manpages.ubuntu.com/manpages/trusty/en/man7/glob.7.html) for that pattern, in both the line for rsync and the line for mkdir.

---

### Post by Drenriza on 2015-07-21
> **Lars Noodén said:**
> Yes, I think you need separate entries in [sudoers]("http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html") on the server for mkdir and rsync.  But for mkdir, it would be good to limit which directories can be created.  

```

rsync ALL=(ALL:ALL) /usr/bin/rsync --server -vlogDtprRze\.iLs \. /new/remote/backup/parent/date\.dir
rsync ALL=(ALL:ALL) /bin/mkdir /new/remote/backup/parent/date\.dir 
```

If the directory to be created is not "date.dir" literally but some pattern, then use [globbing]("http://manpages.ubuntu.com/manpages/trusty/en/man7/glob.7.html") for that pattern, in both the line for rsync and the line for mkdir.

Thanks for the reply @Lars Nooden its super helpful.

Actually i run the rsync command through a script where i set the new directory name as follows
```

weekOfMonth=$((($(date +%d)-1)/7+1))
DATE="$(date "+%Y-%m-%d-${weekOfMonth}-%T")"

```

```

rsync -v -e "ssh -t" -a --log-file=/path/log/${DATE}.rsync.log --recursive --compress --rsync-path="mkdir ${filePath02}/${DATE}.full.dir && sudo rsync" --files-from=/include.cfg --exclude-from=/exclude.cfg / ${BACKUPSERVER}:${filePath02}/${DATE}.full.dir

```

Can the date be achieved with globbing?

---

### Post by Lars Noodén on 2015-07-21
Kind of.  I am finding that sudo's globbing is not quite normal but this pattern below would allow you to make any directory, anywhere that ended in the date pattern you show above.

```

rsync      (ALL : ALL) /bin/mkdir /*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]

```

The /*/ part can be replaced by a real directory if you know that in advance.  

You'll want to test to be sure.

---

### Post by Drenriza on 2015-07-21
> **Lars Noodén said:**
> Kind of.  I am finding that sudo's globbing is not quite normal but this pattern below would allow you to make any directory, anywhere that ended in the date pattern you show above.

```

rsync      (ALL : ALL) /bin/mkdir /*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]

```

The /*/ part can be replaced by a real directory if you know that in advance.  

You'll want to test to be sure.

Thanks a bunch for the reply @Lars, its like a big life ring.

Would the style for mkdir also apply to rsync, for example

```

rsync ALL=(ALL:ALL) /usr/bin/rsync --server -vlogDtprRze\.iLs \. /*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]

```
Would rsync see this as mkdir does, as in
it can access any directory that equals the pattern?

---

### Post by Lars Noodén on 2015-07-21
> **Drenriza said:**
> it can access any directory that equals the pattern?

Yes, but question is if it is the right pattern. ;)  If it is all scripted then you can put a NOPASSWD: in front of it.  

One thing about testing sudo and sudoers is that you should leave open a root shell or edit session of sudoers while you experiment so that you don't lock yourself out.

---

### Post by Drenriza on 2015-07-22
> **Lars Noodén said:**
> Yes, but question is if it is the right pattern. ;)  If it is all scripted then you can put a NOPASSWD: in front of it.  

One thing about testing sudo and sudoers is that you should leave open a root shell or edit session of sudoers while you experiment so that you don't lock yourself out.

Thats a good question ;)

Thanks again for all the assistance @Lars Nooden

I will try and see if sudoers will accept a parent backup directory and than match any character (devices) to make a backup in.

```

rsync      (ALL : ALL) /bin/mkdir **/backup/***/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]

```
So i can end up with something like
(output from tree command - empty folders)
backup
&#9500;&#9472;&#9472; device1.dir
&#9474;        &#9500;&#9472;&#9472; backup1
&#9474;        &#9500;&#9472;&#9472; backup2
&#9474;        &#9492;&#9472;&#9472; backup3
&#9492;&#9472;&#9472; device2.dir
        &#9500;&#9472;&#9472; backup1
        &#9500;&#9472;&#9472; backup2
        &#9492;&#9472;&#9472; backup3

---

### Post by Lars Noodén on 2015-07-22
> **Drenriza said:**
> ```

backup
&#9500;&#9472;&#9472; device1.dir
&#9474;        &#9500;&#9472;&#9472; backup1
&#9474;        &#9500;&#9472;&#9472; backup2
&#9474;        &#9492;&#9472;&#9472; backup3
&#9492;&#9472;&#9472; device2.dir
        &#9500;&#9472;&#9472; backup1
        &#9500;&#9472;&#9472; backup2
        &#9492;&#9472;&#9472; backup3
```

If the hierarchy is arranged like that, then it might be possible to do away with the suspect asterisk. 

```

rsync      (ALL : ALL) /bin/mkdir /backup/device[0-9].dir/backup[0-9]/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]

```

---

### Post by Drenriza on 2015-07-23
> **Lars Noodén said:**
> If the hierarchy is arranged like that, then it might be possible to do away with the suspect asterisk. 

```

rsync      (ALL : ALL) /bin/mkdir /backup/device[0-9].dir/backup[0-9]/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]

```

Thanks for your reply @Lars Noden

I will test out your suggestions with sudo :)

At the moment i am testing rsync with the root user, for simplicity until i have tested with the updated sudoers file.

**Log confusion question**
In my rsync command i have the flag --log-file=/file to where rsync logs all its changes.

That with 
```
cat file.log |awk '{print $4}' |sort |uniq
```
sump up to

> 
cd..t......
<f+++++++++
<f.st......
<f..t......


What i don't understand is that rsync hardlinks from my previous backup to the second one, if a file has not changed to save disk space and bandwidth.
But it does not state anything like this in the log file.

But on the first run (full backup) rsync transfear 2.5GB and on the incremental it transfer 28MB.
By checking two files, one from the full and incremental backup with

```
stat -c %i [filename]
```

I can see that the inode number is the same, so the hardlink has happened. But why cant i see this in the logfile??

---

### Post by Lars Noodén on 2015-07-23
Is that even with -v, -vv or -vvv for rsync?  I haven't tried --info or --debug but maybe they would help, particularly the latter.  The option --debug seems to support reporting about hardlinks.  See 'rsync --info=help' or 'rsync --debug=help' for the details.  

BTW, awk can read directly from a file and sort has a built-in unique function.

```

[s]cat file.log |awk '{print $4}' |sort |uniq[/s]
awk '{print $4}' file.log | sort -u

```

---

### Post by Drenriza on 2015-07-28
> **Lars Noodén said:**
> Is that even with -v, -vv or -vvv for rsync?  I haven't tried --info or --debug but maybe they would help, particularly the latter.  The option --debug seems to support reporting about hardlinks.  See 'rsync --info=help' or 'rsync --debug=help' for the details.  

BTW, awk can read directly from a file and sort has a built-in unique function.

```

[s]cat file.log |awk '{print $4}' |sort |uniq[/s]
awk '{print $4}' file.log | sort -u

```

Thanks for the reply @Lars Nooden

I haven't had time to check the --debug or --info yet unfurtiantly, but i will get their :)

I have though tried to edit my sudoers file, without luck for a successful parse by visudo -c

**Attempt #1**
```

# backup user that can gain super-user privileges  <<< This is line 21
abackup ALL=(ALL:ALL) /bin/mkdir /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9].[f,i]*
abackup ALL=(ALL:ALL) /usr/bin/rsync --server -vlogDtprRze\.iLs \. /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9].[f,i]*

```

My first asterix for line 22 & 23 (**/backup/device/*/**) is for selecting my device-location that all has different names.
My second asterix on line 22 & 23 (**[0-9][0-9].[f,i]***) is for making a file extension that ends on full.dir or inc.dir after the date and time. unfortunately the attempt to create the file extension creates a parse error.

When i check my sudoers file with visudo it says
> 
visudo: >>> /etc/sudoers: syntax error near line 21 <<<
visudo: >>> /etc/sudoers: syntax error near line 22 <<<


**Attempt #2 (dumming it down)**
```

# backup user that can gain super-user privileges  <<< This is line 21
abackup  ALL=(ALL:ALL) /bin/mkdir  /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9].*
abackup  ALL=(ALL:ALL) /usr/bin/rsync --server -vlogDtprRze\.iLs \.  /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9].*

```

> visudo: >>> /etc/sudoers: syntax error near line 22 <<<
parse error in /etc/sudoers near line 22

So i guess their is something in the line
> /usr/bin/rsync --server -vlogDtprRze\.iLs \.
that it dosent like. The difference i can see between above and the debug output from the guide ([https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo))
is that in my rsync command it adds \. versus just . from the guide. I dont know if this make the difference, since im not sure what \. or . means in this syntax.

All feedback are greatly appreciated.
Thanks on advance.

Edit
> 
Note that the following          characters must be escaped with a '\' if they are used in command          arguments: 

[LIST]
[*],
[*]:
[*]=
[*]\
[/LIST]
 

---

### Post by Lars Noodén on 2015-07-28
It was my mistake, the dots are taken literally by sudo in sudoers and do not need to be escaped.  In fact sudo won't accept escaped dots. I thought I corrected my post above but I missed one and have now corrected it.

---

### Post by Drenriza on 2015-07-28
> **Lars Noodén said:**
> It was my mistake, the dots are taken literally by sudo in sudoers and do not need to be escaped.  In fact sudo won't accept escaped dots. I thought I corrected my post above but I missed one and have now corrected it.

Thanks @Lars Nooden

This solved the error from the sudoers file.
Here later i will check my new user over rsync :)

---

### Post by Drenriza on 2015-07-29
So i tried the script yesterday with the new backup user in sudoers file.

And get this error

> 
debug1: Sending command: sudo mkdir /backup/device/device-location/2015-07-29-5-11:44:56.inc.dir && sudo rsync --server -vlogDtprRze.iLs --log-format=%i --link-dest /backup/device/device-name/ . /backup/device/device-name/2015-07-29-5-11:44:56.inc.dir
[B]sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: 3 incorrect password attempts[/B]
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype [email]eow@openssh.com[/email] reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
Transferred: sent 3760, received 2016 bytes, in 0.5 seconds
Bytes per second: sent 7589.9, received 4069.5
debug1: Exit status 1


My sudoers file is as follows (parses with 0 errors with visudo -c)
```

# Backup user that can gain super-user privileges
abackup ALL=(ALL:ALL) /bin/mkdir /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9].*
abackup ALL=(ALL:ALL) /usr/bin/rsync --server -vlogDtprRze.iLs --log-format=%i --link-dest /backup/device/*/ . /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9].*

```

From what i can see it seems that the user authenticates just fine.
> 
debug1: Authentication succeeded (publickey).
Authenticated to remote.system ([xxx.xxx.xxx.xxx]:22).
debug1: channel 0: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8


I have tried to Google a solution but without luck to a secure solution.

Thanks on advance.
Kind regards.

---

### Post by Lars Noodén on 2015-07-29
sudo is asking for a password.  Ultimately that is turned off for scripting, which is why it is important to have the tightest pattern possible:

```

abackup ALL=(ALL:ALL) **NOPASSWD:** /bin/mkdir /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9].*
abackup ALL=(ALL:ALL) **NOPASSWD:** /usr/bin/rsync 

```

---

### Post by Drenriza on 2015-07-30
> **Lars Noodén said:**
> sudo is asking for a password.  Ultimately that is turned off for scripting, which is why it is important to have the tightest pattern possible:

```

abackup ALL=(ALL:ALL) **NOPASSWD:** /bin/mkdir /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9].*
abackup ALL=(ALL:ALL) **NOPASSWD:** /usr/bin/rsync 

```

Thanks @Lars Nooden
Makes perfect sense now when i see it with your text.

---

### Post by Lars Noodén on 2015-07-30
When the mkdir configuration in sudoers is working, try tightening down rsync.  Based on the output form an earlier post above, it should end up something like this:

```

abackup ALL=(ALL:ALL) /usr/bin/rsync --server -vlogDtprRze.iLs --log-format=%i --link-dest /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9] . /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]

```

But be sure not to end the sudoers pattern with a star, that would undo any restrictions since a star could stand for anything including ../../../../etc/shadow

---

### Post by Drenriza on 2015-07-30
> **Lars Noodén said:**
> When the mkdir configuration in sudoers is working, try tightening down rsync.  Based on the output form an earlier post above, it should end up something like this:

```

abackup ALL=(ALL:ALL) /usr/bin/rsync --server -vlogDtprRze.iLs --log-format=%i --link-dest /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9] . /backup/device/*/[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]-[0-9]-[0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]

```

But be sure not to end the sudoers pattern with a star, that would undo any restrictions since a star could stand for anything including ../../../../etc/shadow

Thanks @Lars Nooden

Thinking im almost their where i want to be in regards to rsync and a simple backup script
for full and incremental backups.

Its been a true learning experience and want to thank all for posting and taking time to helping me out.
In the end i will try and type out a guide and the problems i ran into and how i got around them.

Hopefully it can help someone.

---

