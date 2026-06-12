---
title: "Help Changing Permissions, Please!"
date: 2016-08-02
forum: General Help
---

### Post by BlueAZ on 2016-08-02
Hi,   I have read a bunch of similar threads, but still need help.  I love using Ubuntu, but run into this Permission denial problem occasionally and it never seems like the same procedure works twice!
In prep for upgrading to 16.04 on my 64-bit desktop, I am copying many essential folders from Home to a 32 Gb USB stick.  (this is in addition to creating a Back-in-Time backup on a separate partition)   All was going well till suddenly all folders and files on the USB became locked.  I don't know why this happened.  I tried right-clicking on the USB, both in Nautilus and Media, and changing permissions in Properties.  But I just got an error message.
So I went into T> gksu nautilus, and tried again, repeatedly, in every way I could think of.  I keep getting the error message that I don't have permission to change permissions.  Why is this so hard?  I just want full access to all my stuff!  Is there a way to turn off this annoying default in Ubuntu, so I never have to deal with this again?
Thank you tech gurus!

---

### Post by QIII on 2016-08-02
Applying permissions changes indiscriminately with a broad brush is a bad idea.  This is not an "Ubuntu default".  It is part and parcel of the structure of *nix systems.  Wholesale changes made to your backup would wreak havoc if you then applied the files to your new system.

Even a single permission change to one file can render your system inoperable.  And there are files in your home folder that have special permissions.

Your description of what is going on is unclear.  Exactly what are you doing and what is happening when you get these permission errors?

---

### Post by BlueAZ on 2016-08-03
Gee, that's as helpful as ground glass gravy!  I was quite clear: I was trying to access the files I had already copied to a USB stick.  If you can't help, at least don't lecture!

---

### Post by QIII on 2016-08-03
You have only now described that the error occurred after copying when trying to access the files.  That is a significant point not made in your original post.  The question I asked was for clarification to make it easier to diagnose your issue.  If you would like your issue to be solved, answering diagnostic questions without sarcasm would help.

You might do well to be somewhat less snarky with the volunteers who might help you.  And if you take a warning as an undesirable "lecture" that is on you.

You might also do well to avoid instructing Staff members when and when not to answer.

---

### Post by papibe on 2016-08-04
Hi BlueAZ.

Is the partition the is receiving the Back-in-Time backup also on the USB?

Which operation gave you the error? Copying files from your home directory, or the Back-in-Time backup?

How did you copy the files from home? Did you use command line tools, like cp, rsync? Did you copy files using nautilus?

Could you describe 'locked'? Like
[LIST]
[*]are you able to see the list of file and directories, but can open the files?
[*]are not able to see what's in the USB at all?
[*]you can see and open what's there, but can't add or modify files?
[/LIST]
Could you run this command on the mount point of the USB?
```
ls -ld /path/to/mountpoint; ls -l /path/to/mountpoint
```
or
run this if the above is too complicated:
```
mount -l | awk '/dev\/sd/{printf "%s\0", $3}' | xargs -0 -n1 bash -c 'ls -ld "$1"; ls -l "$1"; echo' _
```

Thanks in advance.

---

### Post by BlueAZ on 2016-08-04
Thanks papibe, for taking an interest!  I had previously created a partition on the hard drive for my Back-in-Time backups, two years ago when I upgraded to 14.04.  I know at the time I had trouble getting permission to use this partition I'd created.  I believe that's when I learned to use gksu nautilus from the terminal.  I am copying some folders/files to the usb as an extra, removable backup.  I've learned to be careful with my data.
My problem is only with the usb stick.  I had copied a lot to it, then went in and deleted some duplicates, and tried to resume copying to it.  That's when it started showing everything as locked, with a grey lock symbol on each folder.  I know this means I won't be able to copy these back to the hard drive if needed.  I was copying through Nautilus, right-clicking the items and clicking 'copy to' and indicating the usb.  This worked till it locked up; now it won't let me copy more to it, and no, it's not full.  
So: I can see and open what's in the usb, but can't add or modify.  I have tried to change the permissions by right-clicking and using Properties, both in normal mode and using gksu nautilus.  I get an error message that tells me I can't change permissions, that it's 'read only.'  I really want to learn how to deal with this permission thing consistently, as it continues to cost me a lot of wasted time.
I'm not adept at the terminal.  I can use some simple commands and copy/paste to it.  I couldn't run the above command because I don't know how to input the exact path to the usb.  This confuses me.  In Windows, there is an address bar sort of thing that shows that.  No such in Ubuntu.  I'm supposed to just know, I guess, but I don't.  I was too afraid to try the second one.
Thank you again,   Blue

---

### Post by BlueAZ on 2016-08-04
Qlll, I'm sorry for being 'snarky'.  It's just frustrating to search & search for an answer and see so many threads where nothing is resolved.  Then to write what I thought was a detailed description of my problem only to have that dissected.  We certainly got off on the wrong foot!
I do want to be able to mark this thread 'SOLVED' so others can learn too.  I can see from searching that I'm not the only one bumping my head on this permissions thing repeatedly.  I could not find the solution here, nor at AskUbuntu, nor through the Google searches I did.  This is time-consuming, and it's keeping me from upgrading to 16.04 because I won't do that without an extra backup.
Thanks,   Blue

---

### Post by papibe on 2016-08-04
Thanks.

This command should get us info on all mounts and its permissions:
```
mount -l | awk '/dev\/sd/{print $3}' | xargs -n1 -I arg bash -c 'ls -ld "$1"; ls -l "$1"; echo' _ arg
```
Regards.

---

### Post by papibe on 2016-08-05
Thanks.

This command should get us info on all mounts and its permissions:
```
mount -l | awk '/dev\/sd/{print $3}' | xargs -n1 -I arg bash -c 'ls -ld "$1"; ls -l "$1"; echo' _ arg
```
Regards.

---

### Post by BlueAZ on 2016-08-05
OK, here is the full output:
```
blue@blue-IC780M-A:~$ mount -l | awk '/dev\/sd/{print $3}' | xargs -n1 -I arg bash -c 'ls -ld "$1"; ls -l "$1"; echo' _ arg
drwxr-xr-x 24 root root 4096 Jul 14 13:08 /
total 100
drwxr-xr-x   2 root root  4096 Apr 14 16:13 bin
drwxr-xr-x   3 root root  4096 Jul 14 13:14 boot
drwxrwxr-x   2 root root  4096 Feb 21  2015 cdrom
drwxr-xr-x  16 root root  4320 Aug  5 12:19 dev
drwxr-xr-x 144 root root 12288 Aug  5 12:19 etc
drwxr-xr-x   3 root root  4096 Feb 21  2015 home
lrwxrwxrwx   1 root root    33 Jul 14 13:08 initrd.img -> boot/initrd.img-3.13.0-92-generic
lrwxrwxrwx   1 root root    33 Jun 28 16:02 initrd.img.old -> boot/initrd.img-3.13.0-91-generic
drwxr-xr-x  25 root root  4096 May 26 11:00 lib
drwxr-xr-x   2 root root  4096 May 26 11:00 lib32
drwxr-xr-x   2 root root  4096 May 26 11:00 lib64
drwx------   2 root root 16384 Feb 21  2015 lost+found
drwxr-xr-x   3 root root  4096 Feb 25  2015 media
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt
drwxr-xr-x   2 root root  4096 Apr 16  2014 opt
dr-xr-xr-x 207 root root     0 Aug  5 04:58 proc
drwx------   9 root root  4096 Jul  4  2015 root
drwxr-xr-x  24 root root   760 Aug  5 11:59 run
drwxr-xr-x   2 root root 12288 Aug  1 11:27 sbin
drwxr-xr-x   2 root root  4096 Apr 16  2014 srv
dr-xr-xr-x  13 root root     0 Aug  5 04:58 sys
drwxrwxrwt   6 root root  4096 Aug  5 12:17 tmp
drwxr-xr-x  11 root root  4096 Mar 19 12:58 usr
drwxr-xr-x  13 root root  4096 Apr 16  2014 var
lrwxrwxrwx   1 root root    30 Jul 14 13:08 vmlinuz -> boot/vmlinuz-3.13.0-92-generic
lrwxrwxrwx   1 root root    30 Jun 28 16:02 vmlinuz.old -> boot/vmlinuz-3.13.0-91-generic

drwx------ 15 blue blue 16384 Dec 31  1969 /media/blue/2016Backup
total 176
drwx------  2 blue blue 16384 Jul  2 16:41 AirBnB
drwx------  7 blue blue 16384 Aug  1 17:08 Assistance
drwx------  5 blue blue 16384 Aug  4 22:39 AudioBooks
drwx------  2 blue blue 16384 Feb 24  2015 BeeKeeping
drwx------  3 blue blue 16384 Aug  1 17:21 BkUp 4-16-14
drwx------ 26 blue blue 16384 Aug  4 22:23 Documents
drwx------ 15 blue blue 16384 Aug  1 19:05 Music
drwx------  3 blue blue 16384 Aug  4 22:25 My Archives
drwx------  3 blue blue 16384 Apr 23 12:51 My eBooks
drwx------  2 blue blue 16384 Oct 24  2015 Sunset maps
drwx------  3 blue blue 16384 Aug  1 17:37 U-one Bkups to 2-2014

blue@blue-IC780M-A:~$ 

```
I hope that's the correct way to post it.  I don't understand any of it.  The USB stick is mounted.
Thank you,   Blue

---

### Post by BlueAZ on 2016-08-05
Oh, now I see it:  the USB is /media/blue/2016Backup.  It would appear to me that I should be able to read, write and execute.  Why can't I?

---

### Post by papibe on 2016-08-05
> **BlueAZ said:**
> Oh, now I see it:  the USB is /media/blue/2016Backup.
Yes. Let's do some testing.

First, let's see the file system and mount options:
```
grep 2016Backup /proc/mounts
```
Then, let's create a file on the mount point:
```
touch /media/blue/2016Backup/testfile1
```
After that create one on one of the directories:
```
touch /media/blue/2016Backup/Documents/testfile2
```
Let's us how it goes.
Regards.

---

### Post by BlueAZ on 2016-08-15
OK, I muddled through this, so I'll tell you how, in the hope it will help someone else!
After trying another USB stick & having the same problem, I realized maybe I was trying to copy too much stuff at a time.  You know, folders within folders within folders...  So I ejected all media, shut down Ubuntu, went for a walk, scratched left ear, etc.  Then started again, but copying just a few folders at a time.  The USBs both magically began accepting more data and were no longer locked.  So I was able to create the external backup I wanted before upgrading to 16.04.
Actually I did a fresh install of 16.04 from a Live dvd, to the partition where 14.04 had been.  It went well, so I downloaded Back-in-Time, opened the separate partition where my Back-in-Time backups were stored.  Using Back-in-Time, I was able to restore all my personal data, files, photos, music, etc.  In the last phase of the restore, Back-in-Time properly set all permissions so I have access to everything.  I LOVE Back-in-Time!!!  For me, it works better than Deja-Dup.
So there you have it:  copying less at a time gave the desired result, and I'm a happy 16.04 user!

---

