---
title: "Can't write to Kingston USB flash memory"
date: 2006-11-03
forum: General Help
---

### Post by hueoblue on 2006-11-03
Hello,

Just upgraded to edgy and can't seem to write anything to my flash memory stick.
I've tried to chmod the /media/KINGSTON directory, tried to change /etc/ftab, reformatted to fat32, and it remains read-only. I don't know what else to do.

Any help would be greatly appreciated.

---

### Post by Jussi Kukkonen on 2006-11-03
what is the error message?
How is the stick mounted (see /etc/mtab)?

---

### Post by hueoblue on 2006-11-03
The error message is:

"Error while copying to "/media/KINGSTON"
You do not have permission to write to this folder."

In /etc/mtab :

/dev/sda1 /media/KINGSTON vfat rw 0 0

---

### Post by dannyboy79 on 2006-11-03
> **hueoblue said:**
> The error message is:

"Error while copying to "/media/KINGSTON"
You do not have permission to write to this folder."

In /etc/mtab :

/dev/sda1 /media/KINGSTON vfat rw 0 0


what does ls -l /media/KINGSTON return? have you tried to chmod the directory? sudo chmod 700 would give the user read write execute, I think. and read for the group, and read for everyone. I could be wrong on what number to use, but  I think you want to chmod the folder, maybe even change the owner?

All I did was use the search function of this forum and found this answer, change your fstab to match this:
/dev/sdb1       /media/Lacie    ntfs    rw,auto,user,umask=007,gid=46   0       0
but obviously make it match your settings, mount point, hard drive and partition number, and I think that the first user ad first group created in ubuntu is 1000, so it would be gid=1000. this is what I have for my external usb hard drive that is fat32, 
/dev/hdb1       /home/daniel/fat32      vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000  0       0
and I have /home/daniel/fat32 folder owned by me, and these permissions: drwxrwxrwx 9 daniel daniel 32768 1969-12-31 18:00 fat32

---

### Post by chedabob on 2006-11-03
Could you post your fstab?

---

### Post by hueoblue on 2006-11-03
ls -l /media/KINGSTON returns:

"-rwxr-xr-x 1 root root 265209 2006-11-03"

The chmod doesn't work, unfortunately, and I've tried chowner as well, but it tells me that I'm not allowed, even when I sudo.

---

### Post by hueoblue on 2006-11-03
/etc/fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=63d7af10-81e8-44d9-9370-119a4fa61b5e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0dfa6762-905c-4776-ae75-37df66798e6b none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1	/media/KINGSTON auto    defaults	0	0


---

### Post by dannyboy79 on 2006-11-03
have you tried to change you fstab as I have suggested? i believe having tha auto for your filesystem option may be confusing ubuntu and making it read only since you are't defining a filesytem. Maybe, I am merely speculating. Also, i don't know if you read my entire post, but this issue has been solved by changing your fstab to match this:
/dev/sdb1 /media/Lacie ntfs rw,auto,user,umask=007,gid=46 0 0
but obviously make it match your settings, mount point, hard drive and partition number, and I think that the first user ad first group created in ubuntu is 1000, so it would be gid=1000. this is what I have for my external usb hard drive that is fat32, 
/dev/hdb1 /home/daniel/fat32 vfat rw,uid=1000,gid=1000,iocharset=utf8,umask=0000 0 0
and I have /home/daniel/fat32 folder owned by me, and these permissions: drwxrwxrwx 9 daniel daniel 32768 1969-12-31 18:00 fat32

---

### Post by hueoblue on 2006-11-03
Thank-you!
It seems to be working fine now.

---

### Post by dannyboy79 on 2006-11-03
> **hueoblue said:**
> Thank-you!
It seems to be working fine now.

HOORAY!!!!! Chalk another helped person up for dannyboy79! iam glad it is working for you now, just in case others read this thread, can you please post exactly what you did to solve this, if it was using what I had posted, then please state that for future users.

---

### Post by hueoblue on 2006-11-03
Alright, so a review of the solution.

I wasn't able to write anything to my flash disk from the desktop.

So, I reformatted the flash stick using fdisk, changed the file format to (b) FAT32. (This wouldn't be necessary if it is already formatted as a FAT file format. I've read elsewhere that NTFS will cause problems, in which case it may be necessary to format.)

Then edited the /etc/fstab file with a line that looked like this:
```
/dev/sda1  /media/KINGSTON vfat  rw,uid=1000,gid=1000,iocharset=utf8 0 0
```

I still have to mount the drive manually from the command-line, but the problem is solved.

Thanks again, dannyboy.

---

### Post by givré on 2006-11-03
To solve any removable device problem, just remove line about them in /etc/fstab.
fstab is for static device, it don't play really nice with removable device, which can be configure & mount automaticly when plug.

---

### Post by hueoblue on 2006-11-03
> **givré said:**
> To solve any removable device problem, just remove line about them in /etc/fstab.
fstab is for static device, it don't play really nice with removable device, which can be configure & mount automaticly when plug.

That was one of the things I tried initially and it didn't solve my problem of being unable to write to the card.

---

### Post by givré on 2006-11-03
> **hueoblue said:**
> That was one of the things I tried initially and it didn't solve my problem of being unable to write to the card.
So your device is probably formated in ntfs.
pmount is configure to mount fat32 with read/write access by default.

---

### Post by dannyboy79 on 2006-11-06
> **givré said:**
> So your device is probably formated in ntfs.
pmount is configure to mount fat32 with read/write access by default.

well, if you had been helping him all along you would have seen that it was fat32, and it was automounting it owned by root and only readable, the only solution was to add an entry to fstab to get it writable, if you have another solution, please post it here.

---

### Post by givré on 2006-11-06
> **dannyboy79 said:**
> well, if you had been helping him all along you would have seen that it was fat32, and it was automounting it owned by root and only readable, the only solution was to add an entry to fstab to get it writable, if you have another solution, please post it here.
Well,the thing is that it is simply *impossible*. If you don't set it in /etc/fstab, pmount will use the *only* (no alternative...) option of pmount for vfat which is : nosuid,nodev,user,quiet,shortname=mixed,async,atime,noexec,uid=1000,gid=1000,umask=077,iocharset=utf8
So obviously there is only two option :
- There is something wrong with it's device.
- He set it in /etc/fstab.

People should not use /etc/fstab for removable device for at least one reason, the device name is set arbitrarily, and for exemple, if you have two usb device, one in ntfs and one in fat32, if you set the ntfs one with /etc/fstab, it's quite sure that the fat32 will be mount with the same device name, and it will fail (wronf fs).

So the rule is : Don't set removable device in your /etc/fstab if you don't have good reason to do so.

---

### Post by dannyboy79 on 2006-11-06
> **givré said:**
> So the rule is : Don't set removable device in your /etc/fstab if you don't have good reason to do so.

I am glad you finally see the light! After trying many different things to get there usb drives to be writeable, the last solution that we came up with is to make an entry in fstab, which then allows these people to write to the drive. i am glad you finally understand. If you have another solution it is advisable to inform us instead of call us stupid as you did in the other thread just like this one.

---

### Post by givré on 2006-11-06
Sorry dude, but looking at the first post and the following, i'm not sure that it did happens like you said.
> I've tried to chmod the /media/KINGSTON directory, tried to change /etc/ftab, reformatted to fat32, and it remains read-only.
Means for me, that he set up badly his USB device in fstab, and since pmount use fstab entry when there is one, automount fail.
Of course correcting fstab make it working but this is not the solution.
For the reasons i stated before, people should not use fstab for removable device if they don't have good reason to do so, and when i speak about good reason, i speak about setting special ownership, special option...
But for a general use, you should avoid that practice. On top, if it works with a line in fstab, it will works without it. And the second option is for sure the better.
If you don't know what you are talking about, just don't speak. I didn't call you stupid, i found just stupid that you stated wrong something that his important to know, and which is good practice.
Thanks.

---

### Post by dannyboy79 on 2006-11-06
> **givré said:**
> People should not use /etc/fstab for removable device for at least one reason, the device name is set arbitrarily, and for exemple, if you have two usb device, one in ntfs and one in fat32, if you set the ntfs one with /etc/fstab, it's quite sure that the fat32 will be mount with the same device name, and it will fail (wronf fs).

Sorry to point out that your reason is not a reason at all because that can be solved by using udev to create device nodes using vendor id's, check it out here: [http://www.ubuntuforums.org/showthread.php?t=168221&highlight=%2Fetc%2Fudev%2Frules.d](http://www.ubuntuforums.org/showthread.php?t=168221&highlight=%2Fetc%2Fudev%2Frules.d)

I will point out that there are issues with udev and Edgy, Edgy uninstalls udev and even after they reinstall it it appears to still not want to work.

---

### Post by givré on 2006-11-06
> **dannyboy79 said:**
> Sorry to point out that your reason is not a reason at all because that can be solved by using udev to create device nodes using vendor id's, check it out here: [http://www.ubuntuforums.org/showthread.php?t=168221&highlight=%2Fetc%2Fudev%2Frules.d](http://www.ubuntuforums.org/showthread.php?t=168221&highlight=%2Fetc%2Fudev%2Frules.d)

udev rules is not a solution, when there is better solutions.
I'm not sure it's something good for newbie to make an udev rules for every removable device they will use.
They could us how unuser friendly is linux, when this is the contrary.
When there is g-v-m, hal, pmount, and gnome-mount which will replace pmount in feisty, why making such things.

---

### Post by dannyboy79 on 2006-11-06
> **givré said:**
> udev rules is not a solution, when there is better solutions.
I'm not sure it's something good for newbie to make an udev rules for every removable device they will use.
They could us how unuser friendly is linux, when this is the contrary.
When there is g-v-m, hal, pmount, and gnome-mount which will replace pmount in feisty, why making such things.

you keep going on and on about how my solutions are bad but yet you have posted 4 threads since without one solution explained and how to get it to work???? They have told you over and over that they removed the fstab entry and it wouldn't allow them to write to the drive!!!!!!! If you're going to say 1 method isn't correct than provide another solution and how to do it instead of just saying, oh, you should use g-v-m, hal, gnome-mount etc etc. Newbies don't know what do with sentences like that. You would do everyone a huge favor if you're going to critisize methods to provide a different method that WORKS and explain how to do it. Then to make matters worse for you to have the audacity to lie and say you didn't call me stupid is just plain wrong, I'll quote you from the other thread,

> **givré said:**
> Please, don't be stupid. Thanks.

So don't tell me you didn't call me stupid!!!

---

### Post by givré on 2006-11-06
> **dannyboy79 said:**
> you keep going on and on about how my solutions are bad but yet you have posted 4 threads since without one solution explained and how to get it to work???? They have told you over and over that they removed the fstab entry and it wouldn't allow them to write to the drive!!!!!!!
Sorry, but that's not true. That's  why i wanted to point them to the good solution.
> **dannyboy79 said:**
>  If you're going to say 1 method isn't correct than provide another solution and how to do it
That's not my solution, just the official solution.
> **dannyboy79 said:**
> instead of just saying, oh, you should use g-v-m, hal, gnome-mount etc etc. Newbies don't know what do with sentences like that. 
But they don't have to know. Everything is automatic.
> **dannyboy79 said:**
> You would do everyone a huge favor if you're going to critisize methods
You're methods worked, but could break other stuff, that's why i wanted to point the good method.
> **dannyboy79 said:**
> Then to make matters worse for you to have the audacity to lie and say you didn't call me stupid is just plain wrong, I'll quote you from the other thread,
I didn't say that you are stupid, just said that your reaction was stupid.
But that was over reaction, and i apologies for that.

---

### Post by dannyboy79 on 2006-11-06
> **givré said:**
> I didn't say that you are stupid, just said that your reaction was stupid.
But that was over reaction, and i apologies for that.

I can't believe that you are gonna still sit there and lie about it. I have quoted what you said and yet you still say you didn't call me stupid. How can you just flat out lie???? You stated this exactly, 

> **givré said:**
> Please, Don't be stupid. Thanks

and yet you keep saying you didn't say it. Why don't you just stop lieing and say you're sorry for calling me stupid and not try to switch it around and state the you were calling my reaction stupid which wasn't in the thread you called me stupid at all. There were 5 words in the thread you called me stupid in and nothing about you calling my reaction stupid, you flat out called me stupid. I don't accept your apology since you're not apologizing for what you said, you're apologizing for something you're lieing about which isn't the same thing!

---

### Post by givré on 2006-11-06
`Don't be stupid` didn't want to mean that you are stupid, but that you acted as (at least that was what i wanted to say). But like i said before, that was over reacting , and i apologies for telling you `don't be stupid`. 
And because what i did was bad, and was not a good exemple, i censured my post, and i apologized for what i said on the following post.

---

### Post by givré on 2006-11-06
And i then called for a discussion about that, what we did in that thread, and that was an interesting discussion, isn't it ?

---

### Post by weed-n-linux on 2008-01-13
seems to be an old thread but i have the same problem and nether of those suggestions worked :(

---

