---
title: "[SOLVED] DVD Rom permission denied."
date: 2007-12-25
forum: General Help
---

### Post by grahambo2005 on 2007-12-25
Hey Guys

I am a total newbie to linux, I am having a problem with my DVD-ROM.
When I put in a DVD that I wish to copy/use I get a message on the screen saying permission denied to cdrom0.

I have looked for solutions to this but can only really find other people with the same problem or similar problem.

Ive tried to the whole chmod thing but that didnt work as the device is a DVD-ROM and is read only. I do not know how to access the drive in the terminal or through gnome. I really need access to it. Any help anyone has would be greatly appriciated. If you ask me for logs outputs etc please state clearly what I need to do in order to get that info

Cheers

Graham

---

### Post by TidusBlade on 2007-12-25
Dont know much here, but I can help you do it through the terminal is possible...
So firstly; go into the cdrom by typing "cd /media/cdrom0/". IF it dosent work, then I wouldnt know what to do then. "cd" means change directory.
Then, type "ls -a" which lists the directory contents, and the -a to also show hidden files.
And then whatever file you want try "sudo cp file.ext /home/username/" where sudo stand for su (super user AKA root) do, cp is copy and in file.ext, that would be the file or folder you wanna copy and /home/username/ is where you want it copied to ;)

---

### Post by eggdeng on 2007-12-25
Take a look in System -> Administration -> Users and Groups  -> Groups Tab. Find the cdrom group, click Properties and make sure your user is a member. If not, add the user.

---

### Post by grahambo2005 on 2008-01-06
Hey Guys

I tried both of these but neither has worked. :( Oh well. I'll have to trawl on. I have been able to access the drive as su but thats kind of a pain ya know?

:(

---

### Post by rubicon on 2008-01-06
Have you tried to re-insert this DVD?

If problem stays, please post your /etc/fstab (just copy the output of 'cat /etc/fstab' and paste here).

---

### Post by pimpaulogy on 2008-01-07
I am getting the same error.

When I try to browse to the directory (cd /media/cdrom0/) I get a permission denied.

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=20c11533-5c82-4b89-ab8a-6cf5b43d26c6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2EE874FDE874C51D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=b9c9d409-a0fe-4412-b11f-35bedef6ae93 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Thanks for the help.

---

### Post by rubicon on 2008-01-07
fstab seems OK to me.

What shows ```
ls -Al /media/
```? (that's small L in ls -Al)

---

### Post by pimpaulogy on 2008-01-07
total 46
lrwxrwxrwx  1 root       root           6 2007-12-07 01:43 cdrom -> cdrom0
dr--r--r--  3 4294967295 4294967295    88 2007-09-09 21:47 cdrom0
drwx------ 15 paul       root       16384 1969-12-31 16:00 disk
-rw-r--r--  1 root       root         100 2008-01-07 10:49 .hal-mtab
-rw-------  1 root       root           0 2008-01-07 10:49 .hal-mtab-lock
drwxrwx---  1 root       plugdev    24576 2007-12-04 08:50 sda1

---

### Post by rubicon on 2008-01-07
> **pimpaulogy said:**
> total 46
lrwxrwxrwx  1 root       root           6 2007-12-07 01:43 cdrom -> cdrom0
dr--r--r--  3 4294967295 4294967295    88 2007-09-09 21:47 cdrom0
drwx------ 15 paul       root       16384 1969-12-31 16:00 disk
-rw-r--r--  1 root       root         100 2008-01-07 10:49 .hal-mtab
-rw-------  1 root       root           0 2008-01-07 10:49 .hal-mtab-lock
drwxrwx---  1 root       plugdev    24576 2007-12-04 08:50 sda1
Whatif: ```
sudo chmod 777 /media/cdrom0
```?

---

### Post by pimpaulogy on 2008-01-07
Tried that once before, but will do again.

Here is the result:
```
chmod: changing permissions of `/media/cdrom0': Read-only file system
```

Then I do a cd /media/cdrom0
and I get this:
```
bash: cd: /media/cdrom0: Permission denied
```

Anymore thoughts?

---

### Post by rubicon on 2008-01-07
Hmm. OK, how about this one:```
sudo chmod +x /media/cdrom0
```?

---

### Post by pimpaulogy on 2008-01-07
Same result.

---

### Post by doug1212 on 2008-01-07
I had similar problems with my sata dvd rom drives, on my machine files /dev/sg0 are being set with incorrect permissions, it shoud be root:cdrom but is being set root:root. if the file permissions were altered manually on next boot they would revert.
I was instructed to edit /etc/rc.local to add:
```
chown root:cdrom /dev/sg0
```
before "exit 0"

Worth a try,
Doug.

---

### Post by rubicon on 2008-01-07
What "ls -Al /media" shows?

I'm not sure if it will help, but eject your cd, then```
sudo rmdir /media/cdrom0
sudo mkdir /media/cdrom0
```
This will recreate directory for mounting. (But be careful)

Insert cd. If you will experience the same, then the reason is probably in 'mount'.
Can you read anything from cdrom as root? 
```

sudo cd /media/cdrom0
sudo ls -Al
# tail <some text file>

```

If you can, check:```
groups <your-username>
``` if you are in "cdrom" group?

---

### Post by pimpaulogy on 2008-01-07
I am going to try adding the code to the rc.local file and see what happens.

A little more info is this seems to only happen with DVDs.  If I insert a CD, browse and access permissions are just fine.  I only get denied when it's this DVD (only one I have to test with) that was created by a person with video they shot with a video camera so their isn't any copyright protection on it.  Additionally, I can play the DVD with VLC, but I can't do anything else (rip).

---

### Post by pimpaulogy on 2008-01-07
Well, still doesn't work.

I didn't try deleting the folder because I don't think that will make a difference, but I could be wrong.  If you firmly believe that can help, let me know and I will try it.

I tested the same DVD on a different machine using XP and I could browse the disk just fine so I have to believe it's not related to the DVD.

I guess this happened when I switched to Gutsy because I used to use DVD with this same system with Feisty, but this is the first time using the DVD player since then, I think.

---

### Post by pimpaulogy on 2008-01-09
Does anybody else have anymore ideas on how to resolve this?

---

### Post by markusfarkus on 2008-01-09
Have you tried creating a new directory and manually mounting the cdrom to that directory?  I remember I had a problem with that once and needed a quick fix so I simply mounted it to a new directory I made and everything worked fine.  This obviously wouldn't be a permanent solution (though you could make it one by editing fstab), but it will get you up and running now. 

So you would do something like:
mkdir -p /media/test
mount -t iso9960 /dev/hda /media/test

(you can look at your fstab file to see exactly what /dev your cdrom is)

That should get you up and running.

---

### Post by pimpaulogy on 2008-01-09
Thank you, and to the others and their suggestions.

With all of your help, I got it to work, and it was a combination of everybody.

This is what finally did it for me:

I edited the fstab file and removed the "udf" from the cdrom0 line.  I remember reading that somewhere that because it was mounting as udf (I don't even know what that means), that it would cause this issue.

So, all in all, my fstab entry (/etc/fstab) looks like this:

```
/dev/scd0	/media/cdrom0	iso9660 user,noauto,exec 0	0
```

and not this:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I am still a newbie to all of this so some may look at this and go Duh!, but searching this forum, a couple other people had the same issue, but never listed how they resolved it.  Hopefully this helps the others too.

Thanks again.

---

