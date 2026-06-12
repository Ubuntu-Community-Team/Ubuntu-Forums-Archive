---
title: "Making a /home partition"
date: 2007-11-22
forum: General Help
---

### Post by OldGrey on 2007-11-22
Hi

I made myself a separate home partition using Psychocats instructions:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
All went well, I have the 2 partitions and I can access all my folders and files that live in home. However all my personal settings had gone: desktop; bookmarks, firefox add ons, email accounts, address books, etc etc. I am sure that is not right, but I cannot work out what I did wrong.

---

### Post by Happy_Man on 2007-11-22
That's quite interesting.... well, the best thing I can suggest is to start redoing all your settings. Sorry.

---

### Post by OldGrey on 2007-11-22
Thats want I am doing. The tedious bit reorganising all my music and photos.

---

### Post by tad1073 on 2008-02-04
i want to put /home on sdb1 and keep sda1 as root. I was looking at [this](http://www.psychocats.net/ubuntu/separatehome) tutorial and seeing how that I already have the partitions set up could I just copy my home folder to sdb1 and add ```
/dev/sdb1 /home ext3 nodev,nosuid 0 2 
```to fstab like this ```
 /dev/sdb1
/dev/sdb1 /home ext3 nodev,nosuid 0 2
/dev/sdb1 /mnt/sdb1 ext3 defaults 0 2
```

---

### Post by spec-chum on 2008-02-04
> **tad1073 said:**
> i want to put /home on sdb1 and keep sda1 as root. I was looking at [this](http://www.psychocats.net/ubuntu/separatehome) tutorial and seeing how that I already have the partitions set up could I just copy my home folder to sdb1 and add ```
/dev/sdb1 /home ext3 nodev,nosuid 0 2 
```to fstab like this ```
 /dev/sdb1
/dev/sdb1 /home ext3 nodev,nosuid 0 2
/dev/sdb1 /mnt/sdb1 ext3 defaults 0 2
```

That's sort of the scenario I've implemented.  I installed the OS without a separate /home partition and I've got two drives in this box so I thought I'd use the second one for /home.  I copied my /home over to the second disk and amended /etc/fstab to reflect the change.  This is the relevant bits from my /etc/fstab (/spare is a separate partition I created on the first disk when I used gparted to shrink the filesystem.  /home is on the second hard drive):
```

/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /spare          ext3    defaults        0       2
/dev/sdb1       /home   ext3    defaults        0       2

```

---

### Post by tad1073 on 2008-02-04
I am assuming that it worked for you? Will I have to change the thing that associate themselves with /home/thomas/file or folder like config files scripts etc...

---

### Post by spec-chum on 2008-02-04
> **tad1073 said:**
> I am assuming that it worked for you? Will I have to change the thing that associate themselves with /home/thomas/file or folder like config files scripts etc...

No you won't.  That's the beauty of it.  /home is still /home.  You've just changed where the operating system looks for /home by changing the /etc/fstab file.  It now looks for it on the second drive.
The entry in the fstab is saying "mount the partition found at /dev/sdb1 as /home"

---

### Post by tad1073 on 2008-02-04
to do that do i need to use the live cd or or can I just copy /home over put the enrty in fstab, restart then delete the old home

---

### Post by spec-chum on 2008-02-04
What I did first of all was copy my current /etc/fstab to /etc/fstab.bak so I could always revert if I broke something (very good idea).

Just to be on the safe side I also copied my folder from within the current /home to / as when you mount a different partition there you can't see the old one.

Then I copied /home to the second disk (I think I had it mounted as /disk2 at the time so I just copied /home to /disk2/home.

Then I made the change to /etc/fstab to change the line
```

/dev/sdb1       /disk2   ext3    defaults        0       2

```
to
```

/dev/sdb1       /home   ext3    defaults        0       2

```

Then I removed my folder from within the current /home and rebooted to test the new settings.

If it hadn't worked I'd've used the live CD to replace my changed /etc/fstab with the backup copy I'd made and moved my folder back into the old /home.

I notice in your proposed change
```

 /dev/sdb1
/dev/sdb1 /home ext3 nodev,nosuid 0 2
/dev/sdb1 /mnt/sdb1 ext3 defaults 0 2

```

you've got an extra line.  You only want the one line specifying where /dev/sdb1 will be mounted, so that should read
```

 /dev/sdb1
/dev/sdb1 /home ext3 nodev,nosuid 0 2

```

i.e. without the /mnt/sdb1 line.

---

### Post by tad1073 on 2008-02-04
It worked, sort of. the way I had my desktop set-up changed to the original ubuntu scheme I think my splash screen changed also, conky reverted back to the default layout etc...

Do you think you can help me st-up my printer also? I have all the drivers loaded for my particular priter, during start-up it cycles through it's set-up stage but I can't print anything. [Here](http://ubuntuforums.org/showthread.php?t=682259) is my thread about it.

---

### Post by tad1073 on 2008-02-04
I created the /Home folder on sdb1 then renamed /Home on sda1 to /old home, restarted and was not able to login so i started the live cd changed everything back to the way it was but was still unable to login. Got some kind of xsession error, attached is the file. HELP!!!

---

### Post by tad1073 on 2008-02-08
I figured it out. I had /home as /Home.

---

### Post by tad1073 on 2008-02-08
After I copy /home to sdb1 and make the grub entry what do I need to do to be able to delete /home from sda1  and still be able to login.

---

### Post by tad1073 on 2008-02-09
bump...

---

### Post by Nythain on 2008-02-09
ok, question/note to all of you "losing" your settings when you copy your home like that... are you making sure to copy .hidden files also. Most file managers and even ls dont show hidden files by default... wich means, if you dont turn that feature on before you copy, you could be missing important .rc files wich tend to be user setting/configuration files... you could also be missing important .hidden directories wich contain lots of data for programs... they will all get recreated teh next time you run the app, but you will have lost all of your "settings"

just a thought... as for the most recent topic, you dont want to make a grub entry, you want to make an fstab entry....
and as far as what else you need to do to log in... its all been pretty well covered in spec-chum's post...
basically i would mount the partition i wanted to use as new home... copy contents of /home over to it... copy /home to somewhere else within / (for back up purposes???) once you have everything copied and have made sure you have teh appropriate fstab settings, a simple reboot should do the trick

---

### Post by tad1073 on 2008-02-09
I never deleted the /home folder that I put in sdb1 and i just checked to make sure that all the files were there, including the hidden files and they are. The other problem is when i change the name of /home in sda1 i am unable to login.

i ment fstab not grub, my mistake.
> After I copy /home to sdb1 and make the grub entry what do I need to do to be able to delete /home from sda1 and still be able to login.

---

### Post by tad1073 on 2008-02-10
bump...

---

### Post by tad1073 on 2008-02-11
bump...

---

### Post by GerryGG on 2008-02-13
I am not sure if you already found a solution to your problem of not being able to log in after changing the name of your /home directory. I had the same problem. I copied my home directory onto the new dedicated partition, and then renamed the existing /home directory, thinking that that way I would still have it (under a different name) and the new partition would be mounted as my /home directory, as I had added the necessary edits to my /etc/fstab. And like you, I was not able to log in. I got a message, "Your home directory is listed as '/home/[username]' but it does not appear to exist....".

Then I realized that whenever you mount a partition, a share, or anything, the mount point must exist in advance. The /etc/fstab does not create the mount point; it simply mounts the device to whatever existing mount point is identified. So, I used my live Ubuntu CD to access my computer and created the necessary mount point. It took some searching to find the partition, and then I had to use sudo to create the mount point "sudo mkdir /media/disk/home". But, once I did, and rebooted it all worked. Hope this helps.

---

### Post by tad1073 on 2008-02-14
> **GerryGG said:**
> I am not sure if you already found a solution to your problem of not being able to log in after changing the name of your /home directory. I had the same problem. I copied my home directory onto the new dedicated partition, and then renamed the existing /home directory, thinking that that way I would still have it (under a different name) and the new partition would be mounted as my /home directory, as I had added the necessary edits to my /etc/fstab. And like you, I was not able to log in. I got a message, "Your home directory is listed as '/home/[username]' but it does not appear to exist....".

Then I realized that whenever you mount a partition, a share, or anything, the mount point must exist in advance. The /etc/fstab does not create the mount point; it simply mounts the device to whatever existing mount point is identified. So, I used my live Ubuntu CD to access my computer and created the necessary mount point. It took some searching to find the partition, and then I had to use sudo to create the mount point "sudo mkdir /media/disk/home". But, once I did, and rebooted it all worked. Hope this helps.

what is the mount point that I should attach to it? Being that the other /home partition is on a second drve, it will not be nessesary to boot the live cd right? sda1=drive0, sdb1=drive1 and sdc1=drive2

---

### Post by GerryGG on 2008-02-15
The mount point would be /home in the partiion in which your linux file system is installed. However, if you renamed /home to /homeold, then /home doesn't exist any longer. And, when your system reads your /etc/fstab file and tries to mount your new partition as /home, it looks for the /home mount point and can't find it (because you don't have it any longer; you only have a /homeold). So, you need to recreate the /home mount point just as you would create any directory.

I used my live CD, as it was the easiest way for me to access the partition where my linux system was installed, and recreate the /home mount point (directory). If your situation is like mine, and it appears that it may be, one way or the other, you need to create a /home mount point (basically an empty directory called home) in your linux file system - where your old /home used to be - so that when your /etc/fstab runs, your new /home partition will have a mount point to attach to.

---

