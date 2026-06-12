---
title: "Stuck in Busybox because sda6 can't mount"
date: 2021-10-13
forum: General Help
---

### Post by theshin21 on 2021-10-13
See image for the error:

[https://imgur.com/a/xDaTKox](https://imgur.com/a/xDaTKox)

I don't know what to do :(

---

### Post by Dennis N on 2021-10-13
> **theshin21 said:**
> I don't know what to do :(
Is this a new install, or have you been using this OS previously? 
If it's a new install, you might have used **/root** instead of **/** when specifying a mount point. You also might have confused '**usr**' for your user name. Just my guesses without knowing more about your choices.

---

### Post by rsteinmetz70112 on 2021-10-13
Looks to me like an error in the /etc/fstab file preventing /dev/sda6 from mounting on boot. 
Can you cut and past the contents of that file into a reply - Please use code tags 
You may need to boot from a live session to get to it.

---

### Post by theshin21 on 2021-10-13
I've been using this OS previously, I was trying to get my /usr (sda6) partition to become read/write instead of just a read-only so I could store Steam games on it. I went into the Disk Manager App whatever it's called, went into that partition's properties and enabled some setting which after rebooting brought me to this screen with no way for me to get to the OS itself.
Sorry that I never actually described what I was doing, I was kinda panicking and looking for answers and in the meantime I thought I could quickly post something on this forum and then went back to trying to see how to undo what I did.

---

### Post by theshin21 on 2021-10-13
> **rsteinmetz70112 said:**
> Can you cut and past the contents of that file into a reply - Please use code tags 
You may need to boot from a live session to get to it.

I can't boot into Ubuntu, that's the whole problem. And if there's a way to get the files from this Terminal itself then I am very much not aware how I could achieve that.

---

### Post by TheFu on 2021-10-13
> **theshin21 said:**
> I can't boot into Ubuntu, that's the whole problem. And if there's a way to get the files from this Terminal itself then I am very much not aware how I could achieve that.

He is suggesting that you use a USB Flash drive with the Ubuntu/Xubuntu/Lubuntu installer on it.  At the boot screen, you'll be able to choose "Try Ubuntu" ... and be in a reasonable Ubuntu/Xubuntu/Lubuntu "live" environment which can be used to troubleshoot AND correct issues with the HDD/SSD installed version.

In short, use a flash drive Ubuntu installer, boot off it. Choose "Try Ubuntu" from the menu.  Then you'll want to run fsck and smartctl on the storage with the issues.  If the HDD failed, SMART will show lots of errors - or will fail to work.

Also, don't forget to check power and data cable connections. Over time, vibration can loosen those and I've seen SATA cables go bad over years of use (which makes no sense to me).

Using a Try Ubuntu environment to fix things is a very common technique.

---

### Post by ActionParsnip on 2021-10-13
Boot to live USB / CD desktop then run an fsck on all internal partitions to check that they are consistent

---

### Post by theshin21 on 2021-10-13
[SIZE=2]This option right here is the one that ruined it all (The one next to the mouse pointer):
[http://imgur.com/a/Wc5yLHt](http://imgur.com/a/Wc5yLHt)

Unchecking that and rebooting simply defaults it back to being enabled. Also I don't quite understand what I am supposed to do with the "fsck" since all it does in the Terminal is simply respond with "fsck from util-linux 2.34".[/SIZE]

---

### Post by TheFu on 2021-10-13
fsck isn't a GUI program.  You are expected to provide the file location for the file system as an argument to it.

"how to use fsck" search?  found this: [https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)
In your case, I'd guess - and it is just a guess, that the file system is on /dev/sda6. So the command would be 
```
sudo fsck /dev/sda6
```

gnome-disks might have a way to point-n-click, but it will be buried in multiple menu layers. Too hard to explain here. Sorry.

More information ... 
Almost all Linux commands have what is called a "manpage". This is short for Manual Pages. These are specifically setup help files organized with a summary at the top and more details the farther down we read.
```

NAME
       fsck - check and repair a Linux filesystem

SYNOPSIS
       fsck  [-lsAVRTMNP]  [-r [fd]] [-C [fd]] [-t fstype] [filesystem...] [--]
       [fs-specific-options]

DESCRIPTION
       fsck is used to check and optionally repair one or more  Linux  filesys&#8208;
       tems.   filesys  can  be  a  device name (e.g.  /dev/hdc1, /dev/sdb2), a
       mount point (e.g.  /, /usr, /home), or an filesystem label or UUID spec&#8208;
       ifier  (e.g.   UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd or LABEL=root).
       Normally, the fsck program will try to handle filesystems  on  different
       physical  disk  drives  in  parallel  to reduce the total amount of time
       needed to check all of them.
...
```
It goes on and on with details about errors, options, what each means, and other commands or/and manpages for more related information.

---

### Post by theshin21 on 2021-10-13
This doesn't seem very helpful with anything, putting "fsck /dev/sda6" or any equivalent of that command from the website you have provided me simply returns with

fcsk from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sda6: clean 200452/16007168 files, 2921954/64009216 blocks

And nothing else. And the recovery mode doesn't seem to be working either, instead simply dumping me into the same BusyBox Terminal.

---

### Post by TheFu on 2021-10-13
> **theshin21 said:**
> This doesn't seem very helpful with anything, putting "fsck /dev/sda6" or any equivalent of that command from the website you have provided me simply returns with

fcsk from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sda6: clean 200452/16007168 files, 2921954/64009216 blocks

And nothing else. And the recovery mode doesn't seem to be working either, instead simply dumping me into the same BusyBox Terminal.

That says the file system is clean. That's good news. Did you run it on all the other file systems?  Did you run smartctl (request a test, wait, request a report) on all the storage devices?

---

### Post by DuckHook on 2021-10-13
Please appreciate that when you bork an install by changing the permissions on the entire partition containing the OS, the damage done is not trivial. Therefore, the solution will not be trivial either.

Stated plainly, you cannot expect to solve your problem by blindly following a set of instructions as if following a recipe. You must do additional learning to arrive at a basic understanding of what these instructions are meant to achieve. The learning curve is unavoidable and is necessitated by the actions that caused the breakage.

When you run a LiveUSB session, it is possible that /dev/sda6 gets mapped to a different partition than your problematic one. After all you clearly have at least 6 partitions and possibly more. Since the naming of partitions is mapped during the boot process, a LiveUSB will often map different physical partitions to different device names. Therefore, you first have to make sure that /dev/sda6 is, in fact, your problem parition.

Frankly, I doubt that the problem is a corrupted filesystem—which fsck is designed to repair. Based on your own description of the problem, it is far more likely that you have irreparably damaged your OS structure by changing critical components from read only to read-write. One must not go changing foundational file structures without a complete understanding of what one is doing.

I can only suggest the following:

[list=1]
[*]Make sure that you are, in fact, checking the proper partition with fsck.
[*]If the file system is not corrupted, then, using the LiveUSB, you can try navigating to the /usr directory that you messed with and try changing the permissions back to read-only.
[*]Don't hold your breath. It's a vast directory and some files may require settings that are *not* read only. These would have been set properly at time of install and it was your mass change of everything within it that caused the problem.
[*]The problem with making blind wholesale changes to critical system directories/files is that it's a one way process and repairing it is like trying to unscramble an egg. 
[/list]
I suspect that you will end up having to reinstall. If this is what you are ultimately forced to do, then make sure you first back up all of your most important data, and also make sure this data is restorable.

Sorry to be so pessimistic, but assuming you are a relative newbie (based on what you did to the /usr directory), you will likely spend far more time and frustration trying to recover than on a fresh install.

And next time, do not change anything to get Steam running. I run Steam and it requires no monkeying around with file permissions to work properly.

---

### Post by TheFu on 2021-10-13
> **theshin21 said:**
> I've been using this OS previously, I was trying to get my /usr (sda6) partition to become read/write instead of just a read-only so I could store Steam games on it. I went into the Disk Manager App whatever it's called, went into that partition's properties and enabled some setting which after rebooting brought me to this screen with no way for me to get to the OS itself.
Sorry that I never actually described what I was doing, I was kinda panicking and looking for answers and in the meantime I thought I could quickly post something on this forum and then went back to trying to see how to undo what I did.

Ouch.  Permissions for different parts of the OS are set that way for very good reason.  Screwing around with them leads to problems when you don't really understand how permissions work and how the OS primarily uses them for the first line of security. Many programs demand specific owner, group and permissions to work AND those program will refuse to work if those things are not correct.

If the permissions were screw arounded, either restore from the system-backup made before doing that or do a fresh install. If there are any data or/and settings you'd like to keep, back those up first - the Try Ubuntu environment and a flash drive (or cloudy storage) can be used for data.  Don't expect permissions or the owner and groups to be retained in those backups.

You've learned a valuable lesson.  Sorry this knowledge came the hard way.  Many of us have learned it in a similar way.

---

### Post by rsteinmetz70112 on 2021-10-13
When you dump into busybox, simply type "help"
That will give you a list of commands you can use. Sorry, I don't remember what they are.  But if you google busy box you can get a list but it also depends on how busybox was originally compiled.

"cat" should be one of them. Try:
```
$ cat /etc/fstab
```

Mount should also be there. If you run mount:
```
$sudo  mount 
```
It should list all of the currently mounted partitions,
You could try to manually mount /usr with 
```
$sudo  mount /usr
```
But since that device seems to be clean I still suspect the fstab file is broken. At least that will give you an error message that might help figure it out.
More explicitly you could try:
```
$ sudo mount -t ext4 /dev/sda6 /usr
```

---

### Post by grahammechanical on 2021-10-13
Years ago I got dumped at a Busybox prompt. Re-installing saves time and a person's sanity. There are commands we can run at the Busybox prompt. You need a university degree in Busybox to understand the power of Busybox.

> **[B]mount**[/B]
 mount [flags] DEVICE NODE [-o OPT,OPT]

 Mount a filesystem. Filesystem autodetection requires /proc.

 Options:

         -a              Mount all filesystems in fstab
        -f              Dry run
        -i              Don't run mount helper
        -r              Read-only mount
        -w              Read-write mount (default)
        -t FSTYPE       Filesystem type
        -O OPT          Mount only filesystems with option OPT (-a only)
-o OPT:
        loop            Ignored (loop devices are autodetected)
        [a]sync         Writes are [a]synchronous
        [no]atime       Disable/enable updates to inode access times
        [no]diratime    Disable/enable atime updates to directories
        [no]relatime    Disable/enable atime updates relative to modification time
        [no]dev         (Dis)allow use of special device files
        [no]exec        (Dis)allow use of executable files
        [no]suid        (Dis)allow set-user-id-root programs
        [r]shared       Convert [recursively] to a shared subtree
        [r]slave        Convert [recursively] to a slave subtree
        [r]private      Convert [recursively] to a private subtree
        [un]bindable    Make mount point [un]able to be bind mounted
        bind            Bind a directory to an additional location
        move            Relocate an existing mount point
        remount         Remount a mounted filesystem, changing its flags
        ro/rw           Read-only/read-write mount There are EVEN MORE flags that are specific to each filesystem You'll have to see the written documentation for those filesystems


[https://busybox.net/downloads/BusyBox.html](https://busybox.net/downloads/BusyBox.html)

Regards

---

