---
title: "Peculiarities of the Linux file system that we should all be aware?!"
date: 2012-12-11
forum: General Help
---

### Post by Rebelli0us on 2012-12-11
I've been backing up disk#1 to disk#4 (both NTFS) using rsync. The OS is in disk#3. The rsync command line referred to the disks as  "/media/1_1/" and "/media/4_1/" based on their respective volume labels. Everything worked fine. 

I reformatted disk#4 to ext4 and ran rsync. By mistake I had the wrong destination because "/media/4_1/" no longer existed. rsync instead of saying "dir not found" it created the backup on the **wrong drive**, the OS drive #3 under a directory /media/4_1/

I deleted many gigabytes of the misdirected backup under /media/ and corrected the rsync command line. It now reads /media/sdd1/ but shouldn't have Linux told me that the destination partition no longer exists???

---

### Post by lykwydchykyn on 2012-12-11
In Linux, you mount partitions to directories on the filesystem.  The directories exist whether something is mounted to them or not.

This gives you really cool filesystem transparency across devices, disks, network shares, etc.  On the flipside, transparency means by definition that the system doesn't know or care if the directory actually has a filesystem mounted.

If you're doing something like this (my server does something similar) it's usually a good idea to detect if the partition is mounted first, by (for example) grepping the output of "mount".

Here's a snippet from my backup script if it helps (my backup device is mounted at /srv/data)

```

if [ -z `mount |grep /srv/data |cut -d ' ' -f 1` ]; then
    logger "Backup drive not mounted; exiting"
    exit 1
fi

```

---

### Post by Rebelli0us on 2012-12-11
> **lykwydchykyn said:**
> In Linux, you mount partitions to directories on the filesystem.  The directories exist whether something is mounted to them or not.

This gives you really cool filesystem transparency across devices, disks, network shares, etc.  On the flipside, transparency means by definition that the system doesn't know or care if the directory actually has a filesystem mounted.

If you're doing something like this (my server does something similar) it's usually a good idea to detect if the partition is mounted first, by (for example) grepping the output of "mount".

Here's a snippet from my backup script if it helps (my backup device is mounted at /srv/data)

```

if [ -z `mount |grep /srv/data |cut -d ' ' -f 1` ]; then
    logger "Backup drive not mounted; exiting"
    exit 1
fi

```


Thank you, I was really dumbfounded. The backup completed successfully, without errors, but I couldn't find it. The newly partitioned drive was still blank, and I had no idea where 90GB of stuff went!

---

### Post by TheFu on 2012-12-11
> **Rebelli0us said:**
> I've been backing up disk#1 to disk#4 (both NTFS) using rsync. The OS is in disk#3. The rsync command line referred to the disks as  "/media/1_1/" and "/media/4_1/" based on their respective volume labels. Everything worked fine. 

I reformatted disk#4 to ext4 and ran rsync. By mistake I had the wrong destination because "/media/4_1/" no longer existed. rsync instead of saying "dir not found" it created the backup on the **wrong drive**, the OS drive #3 under a directory /media/4_1/

I deleted many gigabytes of the misdirected backup under /media/ and corrected the rsync command line. It now reads /media/sdd1/ but shouldn't have Linux told me that the destination partition no longer exists???

No it shouldn't. **rsync assumes that you know what you are doing.**

---

### Post by Cheesemill on 2012-12-11
> **lykwydchykyn said:**
> In Linux, you mount partitions to directories on the filesystem.  The directories exist whether something is mounted to them or not.

This gives you really cool filesystem transparency across devices, disks, network shares, etc.  On the flipside, transparency means by definition that the system doesn't know or care if the directory actually has a filesystem mounted.

If you're doing something like this (my server does something similar) it's usually a good idea to detect if the partition is mounted first, by (for example) grepping the output of "mount".

Here's a snippet from my backup script if it helps (my backup device is mounted at /srv/data)

```

if [ -z `mount |grep /srv/data |cut -d ' ' -f 1` ]; then
    logger "Backup drive not mounted; exiting"
    exit 1
fi

```
Instead of messing around with mount, cut and grep, take a look at the solution I use in this thread (read posts #9 and #11).

[http://ubuntuforums.org/showthread.php?t=2093121](http://ubuntuforums.org/showthread.php?t=2093121)

---

### Post by lykwydchykyn on 2012-12-12
> **Cheesemill said:**
> Instead of messing around with mount, cut and grep, take a look at the solution I use in this thread (read posts #9 and #11).

[http://ubuntuforums.org/showthread.php?t=2093121](http://ubuntuforums.org/showthread.php?t=2093121)

Very elegant.  I'll have to remember that one.

---

### Post by Rebelli0us on 2012-12-12
Honestly, all that is too arcane for %99 of users. 

Testing for the existence of some file is a workaround, I wouldn’t call it elegant because it cannot be handled by the script. If your script attempted to create a new unique file (with a random alphanumeric name) and if that fails then you’d stop the script with error message, that wouldn’t work either.

So I prefer the mount test. But, the mount command understands “/dev/sdd1” but not “/media/sdd1/” so how does your script correlate the two? You hard-code all the device mappings, and hope that they don’t change?

. . . 

ok, I’m testing the mount command in the command prompt.

mount |grep /dev/sdd1     works, but what does “cut” do?

. . .

rsync script should test both source & destination, yes?

. . .

“fi” = “end if”          in Windows-speak? How cute ;)

---

### Post by Rebelli0us on 2012-12-12
One more question. I'm trying to do the same with network shares. Nautilus refers to them as "smb://bla-bla/..." but when I type that path at the prompt there is no filename completion, so obviously the command interpreter doesn't understand that syntax??

---

### Post by SeijiSensei on 2012-12-12
If you want to use rsync, you need to mount the shares with smbfs as [described here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently"). The smb:// URL style works with clients like Nautilus or Dolphin, but rsync operates at the filesystem level.

---

### Post by TheFu on 2012-12-12
> **Rebelli0us said:**
> Honestly, all that is too arcane for %99 of users. 

Testing for the existence of some file is a workaround, I wouldn’t call it elegant because it cannot be handled by the script. If your script attempted to create a new unique file (with a random alphanumeric name) and if that fails then you’d stop the script with error message, that wouldn’t work either.

So I prefer the mount test. But, the mount command understands “/dev/sdd1” but not “/media/sdd1/” so how does your script correlate the two? You hard-code all the device mappings, and hope that they don’t change?


Actually, testing for that file **is** elegant and trivial in a script. The file would only be there if the partition was not mounted.  I check for a known file/directory under the mount in my backup script, but I'll probably change to the method of looking for a file that is only available when the mount has not happened.  A single 
```
if [ ! -f $file_file ] ; then
 echo "ERROR: backup file system NOT mounted!!!" 
 exit 1
fi
```
**IS** better.  BTW, Linux/UNIX scripting is what Microsoft copied with PowerShell.

Linux is not Windows, there is a very different philosophy.  We prefer smaller programs that do 1 thing well. Then we put smaller programs together to build millions of different solution needs.  For more on this different in philosophy [http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) .

Both methods have a place and are useful, but it is up to us to recognize which fits best for our situation.

---

### Post by JKyleOKC on 2012-12-12
> **Rebelli0us said:**
> Honestly, all that is too arcane for %99 of users. 

...snip...

the mount command understands “/dev/sdd1” but not “/media/sdd1/” so how does your script correlate the two? You hard-code all the device mappings, and hope that they don’t change?

. . . 

ok, I’m testing the mount command in the command prompt.

mount |grep /dev/sdd1     works, but what does “cut” do?

. . .

rsync script should test both source & destination, yes?

. . .

“fi” = “end if”          in Windows-speak? How cute ;)In the first place, scripting **itself** is too arcane for 99% of the users.

For your first question, the mount command **does** include the mount point in addition to the device name. The mount point is the third field of each line, assuming that the space character delimits fields.

The "cut" command extracts the specified field from its input line.

I don't know details of rsync, but most commands need both input and output defined either as input parameters or as defaults.

Finally, reversing the character string is the normal Unix/Linux/BSD way of indicating the end of a command's scope (actually it's in the command shell, bash; other shells might differ). For instance, "case ... esac" or as you noted "if ... fi" -- but "do" is an exception; it's "do ... done" and there could be others. I find it much easier to read, in comparison to the overloaded "end" of some other approaches.

---

### Post by lykwydchykyn on 2012-12-12
> **Rebelli0us said:**
> Honestly, all that is too arcane for %99 of users. 


I wasn't attempting to help 99% of users.  I was attempting to help you.  Is the solution too arcane for you?

---

### Post by Rebelli0us on 2012-12-12
Thank you. I’m gonna play with all this, though I’ve been taking the path of least resistance:

I’ve been using robocopy from inside a Windows VM. Surprisingly it works, and has error handling in case of missing partitions. It even copies transparently to ext4 partitions. Its log is more user-friendly and even includes deleted files, which rsynch apparently will not do. The only thing it can’t copy is security attributes i.e. Linux permissions. But using sudo once to set the ownership of the root directory takes care of that, because it seems all subdirectories inherit permissions from the base dir.

I’m not ready to mark this SOLVED. I consider this to be a defect in the Linux file system, and the workarounds (if any) are much too technical for the average user, it even makes my head spin. However I was pleasantly surprised with all this **FUSION** -- that I can use Windows utilities, on a Windows-free **and** NTFS-free system, and I’m very impressed to see little or no fragmentation after copying 90+GB of stuff including several VMs of 10-20 GB apiece.

---

### Post by Rebelli0us on 2012-12-12
> **lykwydchykyn said:**
> I wasn't attempting to help 99% of users.  I was attempting to help you.  Is the solution too arcane for you?

Thank you. Yes it is, but it's very educational for me and for anyone else that encounters this problem.  You've no idea what it's like to loose an entire backup and have no clue where it went.

---

### Post by sudodus on 2012-12-12
I use ***labels*** to identify partitions and mount them to subdirectories of /media or /mnt with corresponding names to avoid confusion.

---

### Post by Cheesemill on 2012-12-12
This really isn't a peculiarity or defect in the Linux filesystem, it's just a misunderstanding on your part about how things work.

When you use rsync it has no understanding of what mount points are or whether they are involved in the copy process or not. You simply specify a source directory and a destination directory and rsync does its thing, it's up to you to make sure that the source and destination arguments that you pass to rsync are pointing to the correct destination.

This stems from the Linux philosophy of '[Do one thing and do it well]("http://en.wikipedia.org/wiki/Unix_philosophy")'.

---

### Post by LewisTM on 2012-12-12
If you still want to use rsync but with a friendly UI and some dumbproofing, take a look at Luckybackup. One of its features is precisely to check for the existence of target mount points before executing a backup. 
From the Manual:
> [B]Keep your data safe
[/B]luckyBackup first checks whether the directories you've declared exist or if they are empty and warns you accordingly. 

You wouldn't want your 500GB music collection backup (that took half a day to create !!) vanish in a second if you forgot to mount the external drive that your source is in !! 
You also wouldn't want to execute an rsync command if your destination folder is in an external drive that you also forgot to mount.
Cheers!

---

### Post by cmcanulty on 2012-12-12
or use grsync and just browse to locations, makes mistakes a lot harder to do

---

### Post by Rebelli0us on 2012-12-12
> **LewisTM said:**
> If you still want to use rsync but with a friendly UI and some dumbproofing, take a look at Luckybackup. One of its features is precisely to check for the existence of target mount points before executing a backup. 
From the Manual:

Cheers!

Thank you, I **want** a command line and I want a Task Scheduler to wake up the machines at 3am and run it. But the cron thing is not working for me, and I’m not a beginner I assure you. That’s why I’m experimenting with Windows VMs, but VMs can’t see the hardware so they can’t wake up machines from S3.

---

### Post by Rebelli0us on 2012-12-12
> **Cheesemill said:**
> This really isn't a peculiarity or defect in the Linux filesystem, it's just a misunderstanding on your part about how things work.

When you use rsync it has no understanding of what mount points are or whether they are involved in the copy process or not. You simply specify a source directory and a destination directory and rsync does its thing, it's up to you to make sure that the source and destination arguments that you pass to rsync are pointing to the correct destination.

This stems from the Linux philosophy of '[Do one thing and do it well]("http://en.wikipedia.org/wiki/Unix_philosophy")'.

Microsoft now claims that Windows 8 is NOT defective even though there are only 3 people that can use it. But even Microsoft with all their corporate arrogance refrains from blaming the customer when things don’t work.

No argument from me on the Linux philosophy of modularity. I do understand what’s happened here -- missing OS pointers, handles, symbolic links, etc. The bash syntax seems familiar too -- loops, pipes, redirection, etc., a cross between DOS and Visual Basic, without variable declarations.  It’s just not practical having to learn yet another script language just to copy some files.:popcorn:

---

### Post by drmrgd on 2012-12-12
You seem to be mixing and matching a lot of things, as well as trying to do things that some commands are not capable of.  In the last example, cron is not intended to wake a computer up.  It is intended as a job scheduler, which will run a job on a computer when it's awake and active (the Windows job scheduler is the same way).  You might have a look at 'rtcwake' to wake you computer from sleep to run the cron backup script you've created.  Here's an example:

[http://www.howtogeek.com/121241/how-to-make-your-linux-pc-wake-from-sleep-automatically/](http://www.howtogeek.com/121241/how-to-make-your-linux-pc-wake-from-sleep-automatically/)

I wouldn't recommend you use Windows to do the backing up of your Linux system.  Use Linux Tools for Linux and Windows tools for Windows.  You can mix and match, but the results can sometimes be less than ideal.

---

### Post by JKyleOKC on 2012-12-12
> **Rebelli0us said:**
> No argument from me on the Linux philosophy of modularity. I do understand what&#8217;s happened here -- missing OS pointers, handles, symbolic links, etc. The bash syntax seems familiar too -- loops, pipes, redirection, etc., a cross between DOS and Visual Basic, without variable declarations.  It&#8217;s just not practical having to learn yet another script language just to copy some files.Ah, but bash **does** have variable declarations, both local and global, together with functions and subroutines. It's **not** just a script language, any more than COMMAND.COM or CMD.EXE are; it's the default command interpreter or shell just as those are.

If you don't care to know what you can do in the shell, that's fine -- but please don't dismiss it until you know what it really is. Everything you do in a Linux system gets processed through the shell in one way or another, even the programs you write in assembly language to access the system calls.

---

### Post by LewisTM on 2012-12-12
> **JKyleOKC said:**
> If you don't care to know what you can do in the shell, that's fine -- but please don't dismiss it until you know what it really is. Everything you do in a Linux system gets processed through the shell in one way or another, even the programs you write in assembly language to access the system calls.
For the sake of clarity, I don't think that's true.
First of all, dash, not bash, is the default system shell interpreter.
/bin/sh is a symlink to /bin/dash
Bash is the default shell for users. To make bash interpret a shell script, you have to add #!/bin/bash to the first line.
The system programs do **not** use the shell unless specified. Just try to make a launcher in Xubuntu with shell-specific syntax like
```
true && thunar
```
and see how it goes. It won't do anything because Xfce doesn't interpret the &&. The same command in a bash terminal will launch thunar.

Sorry for the digression, just think it's an interesting topic and it could be educational for some.

---

### Post by JKyleOKC on 2012-12-12
Thanks for the correction! I should have said everything goes through **a** shell although it's not always the same one. My intended point was that the shell processing is always there to help translate human-friendly command language into machine-friendly form.

EDIT: I may well have over-stated things; it's been quite a few years since I ventured to write my own o/s on a TRS-80 Model 4! However it's true that a very significant number of "system programs" are actually bash (or other shell) scripts!

---

### Post by drdos2006 on 2012-12-12
This did not work for me with 10.04 Desktop.
I opened new file on drive /media/sdb1 then sudo umount /media/sdb1 to test.

if [ $(mount | grep -c /media/sdb1) == 1 ] does not work	
nor does this
if [ -f /media/sdb1/unmounted ]


However HermanAB's script does.

if [ -z `mount |grep /media/sdb1 |cut -d ' ' -f 1` ]

Thanks HermanAB.

regards

---

### Post by Cheesemill on 2012-12-12
> **drdos2006 said:**
> This did not work for me with 10.04 Desktop.
I opened new file on drive /media/sdb1 then sudo umount /media/sdb1 to test.

if [ $(mount | grep -c /media/sdb1) == 1 ] does not work    
nor does this
if [ -f /media/sdb1/unmounted ]


However HermanAB's script does.

if [ -z `mount |grep /media/sdb1 |cut -d ' ' -f 1` ]

Thanks HermanAB.

regards

For my method to work you need to create a file called unmounted in the empty mount point, see posts #9 and #11 [here]("http://ubuntuforums.org/showthread.php?t=2093121") for a description of how and why this works.

Also how was your sdb1 mounted in the first place? If it was automounted by the system (which I am assuming as it was mounted in /media) instead of manually  then there is a chance the /media/sdb1 directory was deleted when you unmounted.

---

### Post by drdos2006 on 2012-12-12
The drive /media/sdb1 is mounted through fstab. It is mounted at boot time.

I generated a new file named "unmounted" and saved it on the root directory of /media/sdb1.

I unmounted the /media/sdb1 drive and used my bash backup file ( command "bash backup.sh" from a terminal ) using the different commands to test for the "unmounted" file.

HermanAB's command in the script worked for me but not the other two commands.

regards

---

### Post by Cheesemill on 2012-12-12
> **drdos2006 said:**
> I generated a new file named "unmounted" and saved it on the root directory of /media/sdb1.
Did you create the file when sdb was unmounted?

I've been using this technique in my server backup scripts for the last 15 years.

---

### Post by drdos2006 on 2012-12-12
No, I was unable to save the file when /media/sdb1 is unmounted ( as one would expect ).

regards

[edit]
I also unmounted the drive and used "sudo gedit /media/sdb1/unmounted" from a terminal to save the file.
Using HermanAB's script, the log file user.log is updated as well.

[/edit]

---

### Post by Cheesemill on 2012-12-12
It works fine here:
```
root@arch:~# cat mount_test.sh 
[COLOR=RoyalBlue]if [ -f /mnt/test/unmounted ]
then
  echo "Drive is unmounted"
else
  echo "Drive is mounted"
fi[/COLOR]
root@arch:~# mkdir /mnt/test
root@arch:~# touch /mnt/test/unmounted
root@arch:~# mount /dev/sdb2 /mnt/test
root@arch:~# ./mount_test.sh 
Drive is mounted
root@arch:~# umount /dev/sdb2
root@arch:~# ./mount_test.sh 
Drive is unmounted
root@arch:~# 
```

---

### Post by Rebelli0us on 2012-12-17
Using the path in my OP:

```
/ $ cat /media/4_1/nonexistent.rtf
cat: /media/4_1/nonexistent.rtf: No such file or directory

/ $ ls  /media/4_1/
ls: cannot access /media/4_1/: No such file or directory


```

bash responds correctly, so why doesn't rsync know that the path is invalid?

---

### Post by TheFu on 2012-12-17
> **Rebelli0us said:**
> Using the path in my OP:

```
/ $ cat /media/4_1/nonexistent.rtf
cat: /media/4_1/nonexistent.rtf: No such file or directory

/ $ ls  /media/4_1/
ls: cannot access /media/4_1/: No such file or directory


```bash responds correctly, so why doesn't rsync know that the path is invalid?

**Bash** is checking something else.  **cat** is checking something different too.  **Rsync** only needs to know if the file should be mirrored/copied or not. If it doesn't exist, it will create the path. If you ask for a recursive copy using the -r option, then it will create directories above as necessary.  THAT is a feature, not a bug.

If you don't want** rsync** to perform the behavior it is designed to perform, then check to see if  /media/4_1/nonexistent.rtf exists or not before you decide to call or not call rsync.

Just because something doesn't work the way you think it should, doesn't mean it isn't working correctly or as-intended.

I think I've mentioned this previously, but I was hit with a similar issue for my backups using a different backup tool.   The HDD wasn't mounted, so that other tool dutifully backed up as much of the files as could fit on my / partition.  I keep / fairly small only 10G or so, which meant it was filled quickly.  The missing /backup area was created on the root (/) partition, then all the subdirs necessary were created. I had to verify that the /backup partition which was almost 1TB was mounted and available to prevent the same issue happening again.  I also had to umount that storage and clean up the 8GB of crap on the root partition manually.  What came through my mind when this all happened and I figured out the issue was "of course, that's how it should work."  If it hadn't worked that way THEN there would be a bug, IMHO.

---

### Post by Rebelli0us on 2012-12-21
> **TheFu said:**
> **Bash** is checking something else.  **cat** is checking something different too.  **Rsync** only needs to know if the file should be mirrored/copied or not. If it doesn't exist, it will create the path. If you ask for a recursive copy using the -r option, then it will create directories above as necessary.  THAT is a feature, not a bug.

If you don't want** rsync** to perform the behavior it is designed to perform, then check to see if  /media/4_1/nonexistent.rtf exists or not before you decide to call or not call rsync.

Just because something doesn't work the way you think it should, doesn't mean it isn't working correctly or as-intended.

I think I've mentioned this previously, but I was hit with a similar issue for my backups using a different backup tool.   The HDD wasn't mounted, so that other tool dutifully backed up as much of the files as could fit on my / partition.  I keep / fairly small only 10G or so, which meant it was filled quickly.  The missing /backup area was created on the root (/) partition, then all the subdirs necessary were created. I had to verify that the /backup partition which was almost 1TB was mounted and available to prevent the same issue happening again.  I also had to umount that storage and clean up the 8GB of crap on the root partition manually.  What came through my mind when this all happened and I figured out the issue was "of course, that's how it should work."  If it hadn't worked that way THEN there would be a bug, IMHO.

Thank you. Here's rsync summary of my backup. It's supposed to be a mirror, but it gives the impression that not all files were copied! Do you know what happened here?

```
2012/12/21 11:47:00 [2699] Number of files: 151467
2012/12/21 11:47:00 [2699] Number of files transferred: 141387
2012/12/21 11:47:00 [2699] Total file size: 107.20G bytes
2012/12/21 11:47:00 [2699] Total transferred file size: 107.20G bytes
2012/12/21 11:47:00 [2699] Literal data: 107.20G bytes
2012/12/21 11:47:00 [2699] Matched data: 0 bytes
2012/12/21 11:47:00 [2699] File list size: 2.92M
2012/12/21 11:47:00 [2699] File list generation time: 0.001 seconds
2012/12/21 11:47:00 [2699] File list transfer time: 0.000 seconds
2012/12/21 11:47:00 [2699] Total bytes sent: 107.22G
2012/12/21 11:47:00 [2699] Total bytes received: 2.73M
2012/12/21 11:47:00 [2699] sent 107.22G bytes  received 2.73M bytes  68.23M bytes/sec
2012/12/21 11:47:00 [2699] total size is 107.20G  speedup is 1.00
2012/12/21 11:47:00 [2699] sent 107220284403 bytes  received 2726685 bytes  total size 107198314475
```

---

### Post by TheFu on 2012-12-21
Might I suggest turning up the verbose setting so you can see the details?
I also like the --stats and --progress switches.

The **rsync** man page is really very good.
$ man rsync

---

### Post by lykwydchykyn on 2012-12-21
Make sure when you're logging this that you're capturing stderr; if there's a file access problem (due to permissions, e.g.) then it's going to be send to stderr.  By default only stdout is sent to a pipe/redirect, so if your script is redirecting output to the logs you'll want to redirect stderr to stdout.

See this for more detail: [http://www.tldp.org/LDP/abs/html/io-redirection.html](http://www.tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by Rebelli0us on 2012-12-21
> **lykwydchykyn said:**
> Make sure when you're logging this that you're capturing stderr; if there's a file access problem (due to permissions, e.g.) then it's going to be send to stderr.  By default only stdout is sent to a pipe/redirect, so if your script is redirecting output to the logs you'll want to redirect stderr to stdout.

See this for more detail: [http://www.tldp.org/LDP/abs/html/io-redirection.html](http://www.tldp.org/LDP/abs/html/io-redirection.html)

Thank you. I'm not redirecting, you specify the logfile in the command line and everything goes there:

rsync -a --delete --log-file=.....

The output does not list deleted files, unfortunately. Yeah, the linux permissions thing is a nightmare, if stuff doesn't get backup up due to that, we'll have to go back to NTFS.

---

### Post by sudodus on 2012-12-21
I'm happy with ***Unison***, that uses rsync to do the job. I use it to backup my data partition with pictures, video clips etc. You run Unison with sudo. There is a cli version and a GUI version. I suggest you start using the GUI version.

Unison will help you make sure that the backup or (actually the synchronization) is complete. And you can manually reverse the process for individual files or folders or ignore the differences, until you know which version to keep.

But sometimes I run rsync, when I don't want to 'sync' but to keep files, that were deleted after backing them up.

I use ```
sudo rsync -avn 
``` or ```
sudo rsync -Havn
``` if I know there are hard-linked big files (and remove the n after checking with a dry run).

If you are not happy with Unison, you have the option to make complete images of drives or partitions with ***Clonezilla***. With several such images for backup, you are very well prepared for disk crashes.

---

