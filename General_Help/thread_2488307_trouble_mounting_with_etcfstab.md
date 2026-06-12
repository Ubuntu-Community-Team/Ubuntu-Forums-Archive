---
title: "trouble mounting with /etc/fstab"
date: 2023-06-30
forum: General Help
---

### Post by Old Jimma on 2023-06-30
My laptop allows me to use two m.2 ssd cards.

The first m.2 ssd cards is 1TB and has the 22.04 opperting system and my home files at /home/oldjimma.


I bought a 2nd m.2 ssd card, iinstalled the deviced in the 2nd m.2 ssd slot in my laptop, and rebooted.

Next I gparted to 
[LIST]
[*]give the device a name and label...  I used "WD1" for both, and
[*]to format the m.2 SSD: I used gparted to format it as ext4.
[*]
[/LIST]

It is a 1 TB m.2 SSD.

I wanted the device to be mounted at a special mount point on start up: /mnt/WD1

So, I:
[LIST]
[*]as super user, I created a directory named WD2 under the /mnt directory,
[*]then as super user, I changed the ownership of that directory: sudo chomod -R username:username /mnt/WD1 (where "username" is the account user name), and then
[*]I gave "username" read, write, and execute privelenges in that directory, and in every directory that may be created within it in the future: chmod -R 777 /mnt/WD1
[*]
[/LIST]

Lastly, I added the following line to my /etc/fstab file:
> 
##
## WD1
##
UUID=668901d74-5398-4d1b-ac51-ff5aee638afb /mnt/WD1 auto nosuid,nodev,nofail,x-gvfs-name=WD1,x-gvfs-icon=WD1,x-gvfs-symbolic-icon=WD1 0 0


In that line, I determined the  m.2/s UUID using the "information" right click on the device using gparted.

When I rebooted, the device seemed mounted.

HOWEVER, there was a directory at /media/username/WD1 also.

I dd not think too much about that, and wrote alot of stuff to what I thought was the mounted directory /mnt/WD1

However, it seems that it wrote to the /media/usernam/WD1 directory, also. 

What  I determined was that:
[LIST]
[*]althought I thought I was adding files to /mnt/WD1,
[*]I was really adding files to /media/username/WD1
[*]
[/LIST]

I added so many files that the data at /media/username/WD1 nearly overwrote the entire "home directory" device.

What did I do wrong, and how to do get that 2nd m.2 ssd properly named, and mounted so that when I add files to it, files are really added to that device and no other place?

Thanks,
Old Jimma from the Old Country

---

### Post by SeijiSensei on 2023-06-30
First, you should mount the device as root, which is what automatically happens if you mount an ext4 device via /etc/fstab.

I've done the same thing once as you did and wrote the files to the main filesystem tree and not to the mounted device. The quickest solution is to mount the new device temporarily at /mnt, then run rsync to transfer the contents of /media/username/WD1 like this:
```
cd /media/username/WD1; sudo rsync -av . /mnt/WD1/
```
The dot represents the contents of the current directory.

Your fstab entry seems much too complex. If you format the entire partition as ext4, you shouldn't need anything more than
```
UUID=668901d74-5398-4d1b-ac51-ff5aee638afb /mnt/WD1 ext4 defaults 0 0
```

---

### Post by MAFoElffen on 2023-06-30
if you omit the two gvfs options in your fstab options
```

UUID=668901d74-5398-4d1b-ac51-ff5aee638afb /mnt/WD1 auto nosuid,nodev,nofail,[COLOR=#ff0000]x-gvfs-name=WD1,x-gvfs-icon=WD1,x-gvfs-symbolic-icon=WD1[/COLOR] 0 0

```
Without those, the system will replaces those with more logical defaults pointing to your mount point.

Translation, you are pointing to a specific mount mount (other than /media), but then using GVfs options in your options sections. GVfs is a layer under your applications, a userspace virtual filesystem implementation for GIO... That gnome-gdisks uses to mount things to /media. I think that is where that confusion is occurring like that.

I notice you have "auto' as filesystem type. Which filesystem did you format this to?

---

### Post by oldfred on 2023-06-30
Post this in code tags to preserve format, just to see all devices. 
lsblk -f

---

### Post by Old Jimma on 2023-06-30
Hello, oldfred:

Here, ya go (as John Wayne used to say):

```

NAME FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
loop0
     squash 4.0                                                    0   100% /snap/bare/5
loop1
     squash 4.0                                                    0   100% /snap/core20/1822
loop2
     squash 4.0                                                    0   100% /snap/core20/1950
loop3
     squash 4.0                                                    0   100% /snap/core22/766
loop4
     squash 4.0                                                    0   100% /snap/gnome-3-38-2004/119
loop5
     squash 4.0                                                    0   100% /snap/gnome-3-38-2004/140
loop6
     squash 4.0                                                    0   100% /snap/gnome-42-2204/111
loop7
     squash 4.0                                                    0   100% /snap/gtk-common-themes/1535
loop8
     squash 4.0                                                    0   100% /snap/snap-store/638
loop9
     squash 4.0                                                    0   100% /snap/snap-store/959
loop10
     squash 4.0                                                    0   100% /snap/snapd/18357
loop11
     squash 4.0                                                    0   100% /snap/snapd/19457
loop12
     squash 4.0                                                    0   100% /snap/snapd-desktop-integration/49
loop13
     squash 4.0                                                    0   100% /snap/snapd-desktop-integration/83
nvme0n1
&#9474;                                                                           
&#9492;&#9472;nvme0n1p1
     ext4   1.0   WD1   28b9e12b-1468-4556-9835-e0695bd6b6c8  869.2G     0% /mnt/WD1
nvme1n1
&#9474;                                                                           
&#9500;&#9472;nvme1n1p1
&#9474;    vfat   FAT32       30D6-88F4                             504.9M     1% /boot/efi
&#9492;&#9472;nvme1n1p2
     ext4   1.0         e84771bf-abad-4503-9591-6cdd5fdd7b8a  355.1G    56% /

```

---

### Post by Old Jimma on 2023-06-30
thanks for your thought and suggestion,,Seiji Sensi.

I thought it would be important for yuo to know that I tried it, and now my computer will not boot: it offers "emergency mode."

Good grief. The last time I did this  I had to install the operating system again, and then load all of my program and then restore lost files from back up.

I wondered if you might have any further suggestions.

Tanks,
OJ

---

### Post by Old Jimma on 2023-06-30
Well, folks. Thank for your replies. Seem like I ran into a locomotive on this one: followed some advice, and cannot reboot.

If you would be so kind, please sketch a procedure for mounting my second m.2

I'll give it a shot. However, it takes several hours to install the system, and restore, all programs, settings, and data.

It is unlikely that i'll respond to you today because of that.

Thank you,
Old Jimma

---

### Post by oldfred on 2023-06-30
If you have good backups, including list of installed apps, /home and anything else you need, you should be able to reinstall in about an hour.

Did you try to boot recovery mode to get terminal to edit corrupt file(s)?

Or did you try Boot-Repair first?
And post the report it creates?

And then if it takes more than an hour or two to repair, then reinstall?

---

### Post by MAFoElffen on 2023-07-01
Do this... You have two options.

Option #1 you can use if you can get to a Grub2 Menu > Adavnced Options > Select a kernel with recovery > Select enable networking > Select Root Prompt...

Edit the /etc/fstab file
```

nano /etc/fstab

```

Option #2. Boot from LiveUSB installer image. From terminal session
```

mount /dev/nvme1n1p2 /mnt
sudo nano /mnt/etc/fstab

```

After either of those options, then make the repair...

Change the mount line for your added drive to something like this:
```

LABEL=WD1 /mnt/WD1 ext4 auto,nofail,noatime,rw,user    0   0

```
In those options, using 'nofail' will tell it to continue the boot, even if that drive is not there or if there is a (timing) problem. Using that option has to come after option 'auto'. 

Optional whether you use UUID=, LABEL=, PARTLABEL=, or /dev/disk/by-id (or the /dev/disk/by- variants)... I advise not to use /dev/sdXY, nor /dev/nvmeXnY, as those can change during a boot... But what i mentioned doesn't. Since you took the time to make a LABEL, that is very easy to use. But can be a (user caused) problem if you name two partitions with the same Label name...

---

### Post by SeijiSensei on 2023-07-01
It looks like the UUID you gave us originally does not match the actual partition. From your posting above,

> &#9492;&#9472;nvme0n1p1
     ext4   1.0   WD1   **28b9e12b-1468-4556-9835-e0695bd6b6c8**  869.2G     0% /mnt/WD1


You would need that UUID in /etc/fstab, not the one you gave us earlier, or you can use "LABEL=WD1" instead.

I find the easiest solution in cases like this is to boot from a installation disk then open a terminal. You can then mount the system partition to /mnt or somewhere else and make any necessary changes.

---

### Post by Old Jimma on 2023-07-01
First off all: apologies. INoybody knows how to make errors that are worse than mine. 

The catastrophe that occurred yesterday on my computer was most certainly entirely my fault somehow. 

I appreciate everyone's help, especially  SeijiSensei's. 



So, I'm back at it today... starting from scratch after a complete reinstall.

Here is my game plan for installing and mounting the second m.2 drive:

1. create a mount point, /mnt/WDBlack
2. change ownership of /mnt/WDBlack, giving "username" ownership: **sudo chown -R username /mnt/WDBlack**
3. change the privileges of "username" for /mnt/WDBlack: **chmod -R 777 /mnt/WDBlack**
4. add this line to /etc/fstab: **UUID=uuidnumbergoeshere /mnt/WDBlack ext4 defaults,nofail,discard,noatime 0 2**

If you care to, let me know if there are changes you'd suggest.

Thank you!
Old Jimma

---

### Post by TheFu on 2023-07-01
> **Old Jimma said:**
> First off all: apologies. INoybody knows how to make errors that are worse than mine. 
 

I'd done a few doozies in my time too.  Once destroyed a $40k server to the point that even the hardware support people sent by the company were unable to fix it after a week of trying.  It wasn't my server and I hadn't been managing it.  Learned that nobody had managed it in the 2 prior years. 100% data loss on the system and the system never booted again.

I prefer to use LABEL= as the identifier for storage to be mounted. UUIDs aren't exactly human friendly and if you are attempting to type in a UUID, that's a mistake.  Best to find a way to copy/paste or store the UUID of interest into a file, then read that file into your editor when needed. vim makes that easy.

If you get into the habit of making a temporary back copy of any system file BEFORE you screw with it, then you can trivially get back to the prior version.
```
LABEL=WD1    /mnt/WDBlack    ext4     defaults 0 1
```
Also, never use 777 permissions. That's just lazy.  There is a time to use 4777 permissions, but end users seldom would need to do that. Admins should know when it is needed.

---

### Post by Dennis N on 2023-07-01
I wouldn't set 777 for permissions as it gives everyone the same permissions as the owner. chown retains the existing permissions for the three classes of users, and being the owner is all you need.

discard - you don't need this if fstrim is active on your machine.

---

### Post by MAFoElffen on 2023-07-01
+1 with TheFu...

I suggested using LABELS= for you also. they are easy to use, as long as you remember, as a User, to create unique Label names.

Everyone is human and can make mistakes. I am not immune, and have tried to learn from mine. After 34 years of IT, I have had some also. Some were just stupid mistakes while in a hurry, and trying to take shortcuts. Some were just accidents out-of-the-blue on customers machines. (Ouch!) 

Dang, if we were all perfect, that would make things real 'boring'. LOL

A lot of times, I like to use UUID or do 
```

lsblk -o name,label,size,fstype,type,mountpoint
# I'll look at that to adjust the grep filter below to what I want...
ls -la /dev/disk/by-id/ | grep 'sdb' | head -n 1

```
to get my unique disk identifiers. 

I'm getting old, and don't trust myself anymore to retype UUID's from one place to another. So instead, then I'll use something like this to help me
```

DISK=$(ls -la /dev/disk/by-id/ | awk '/sdb/ {print $9}' | head -n 1)
# Then I'll use adjust the following partition number of the following to point to what I want
echo -e "UUID=$(blkid -s UUID -o value ${DISK}-part3') /keystore     vfat  defaults,umask=0077  0 2" >> /etc/fstab

```
Or a variant thereof, so that I do not have to rely on my own typing skills to retype those... Some of my customers want them that way, so I have to do as they have their IT policies set to.

Honestly, in the long run, if you have them as "LABEL=", then if you replaced the drive and Labeled the new filesystem as what was there, you don't even need to update the fstab for the changed drive. It just finds it and see's it as the same. So much easier to use Labels.

I always try to remember to Label things so I can quickly and easily find things that I might have to look for later.

---

### Post by MAFoElffen on 2023-07-01
Also of note...

I've mentioned that for installs, I'll open an editor and create a plan for that in a recipe. I'll type all the commands that I'll use to do the install. I test the installers for QA... But for my other installs, they tend to be a bit more complex than just the basic installer's scripts. So I work around those.

I sometimes also create post-install scripts to use an installer's basic script for something, then extend the system to how I want it to be... Good for migrations.

Even if I don't make it into an install script (many times I do), I can still use 'that' recipe to cut and paste the commands into a graphical terminal session (ssh session or via stored on USB) to do it. These days, I like to create a plan I can see and recheck, to get to where I want to go... It makes things so much easier.

---

### Post by Morbius1 on 2023-07-01
Before we all get medieval about 777 permissions keep in mind the steps he did:

> 1. create a mount point, /mnt/WDBlack
2. change ownership of /mnt/WDBlack, giving "username" ownership: sudo chown -R username /mnt/WDBlack
3. change the privileges of "username" for /mnt/WDBlack: chmod -R 777 /mnt/WDBlack
4. add this line to /etc/fstab: UUID=uuidnumbergoeshere /mnt/WDBlack ext4 defaults,nofail,discard,noatime 0 2

He is setting ownership and permissions of the mount point before the partition is mounted. A mounted partition doesn't inherit the permissions of the mount point - it's the other way around.

If it's a newly formatted ext4 partition it will mount to that mount point with owner = root and permissions of 755 regardless of the permissions of the mount point prior to the mount.

---

### Post by TheFu on 2023-07-01
This is why showing facts using commands is so important.  It prevents missed actions.  
**ls -la /mnt/** would solve that, after the storage is mounted.

Less description of what you think. More facts of what actually is.

---

