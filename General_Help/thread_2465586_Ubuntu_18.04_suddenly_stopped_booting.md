---
title: "Ubuntu 18.04 suddenly stopped booting"
date: 2021-08-06
forum: General Help
---

### Post by olivia89 on 2021-08-06
Damsel in distress asks for help.  

 I **cannot finish writing my master thesis** because after a few years Lenovo G505 Type 20240 (**single-boot Ubuntu 18.04.5 LTS**) suddenly stopped booting. The screen is black with &#8222;Booting in insecure mode&#8221; and I cannot get to purple screen or desktop.

 SMART and MEMTEST showed that HDD and RAM are OK. Neither changing BIOS settings nor resetting CMOS by removing battery helped. Pressing Shift or Esc did not work. I have managed to boot in live mode from USB (Ubuntu 20.04.2.0 LTS) and **Boot-Repair was unsuccessful**. Boot-Repair wanted me to delete unused files because partition was full (well, it was not) and I did but there was no way to empty trash folder.
 
 Paste from Boot-Repair: [URL="https://paste.ubuntu.com/p/xJFfKBbyV6/"]https://paste.ubuntu.com/p/xJFfKBbyV6/
[/URL]
**12 photos**: [https://ibb.co/album/XjL0zm](https://ibb.co/album/XjL0zm)

 &#8222;sudo fsck dev/sda2&#8221; results in &#8222;CLEAN, 267742/61022208 files, 229224017/244059136 blocks&#8221;

 
 Live mode enables me to copy important files (e.g. Zotero) and in the worst case scenario I can move to another computer or try to format Lenovo and reinstall Ubuntu or other OS, but I would prefer to finish writing on this laptop.

 
 I would really appreciate your help.  

 I wish you all good health!

 Olivia

---

### Post by tea for one on 2021-08-06
Just a couple of observations from your screenshots:-

Dev/sda2 - 94% used - I imagine that this has exceeded the threshold written into the boot-repair software.

Powered on 2 years, 1 month and 8 days - I've never kept a laptop powered on for anything like this. Possible battery damage as a guess?

Have you backed up all your data so that your thesis is safe?

---

### Post by olivia89 on 2021-08-06
> **tea for one said:**
> Just a couple of observations from your screenshots:-

Dev/sda2 - 94% used - I imagine that this has exceeded the threshold written into the boot-repair software.

Powered on 2 years, 1 month and 8 days - I've never kept a laptop powered on for anything like this. Possible battery damage as a guess?

Have you backed up all your data so that your thesis is safe?


1. If 6% is too low for Boot-Repair to work, what percentage should it be? It is a 1000 GB HDD. I have deleted some files but it went to trash folder. I cannot empty trash folder in USB live mode. Besides, there are some important files in trash folder so I would like to empty only part of trash folder.

2. I turn off my laptop every day and it works without battery. Could it be charger damage?

3. Thank you for asking. Currently I am not able to clone the entire HDD because I do not have another HDD with 1 TB or more. But I have copied LibreOffice Writer files and Zotero storage.

---

### Post by tea for one on 2021-08-06
One of your screenshots states [COLOR="#0000FF"]Booting in insecure mode[/COLOR]
Is that something special with Lenovo laptops?

I also noticed your have Secure Boot Enabled.

Perhaps, turn off secure boot in your UEFI set-up and see if the laptop boots?

---

### Post by olivia89 on 2021-08-06
> **tea for one said:**
> One of your screenshots states [COLOR=#0000FF]Booting in insecure mode[/COLOR]
Is that something special with Lenovo laptops?

I also noticed your have Secure Boot Enabled.

Perhaps, turn off secure boot in your UEFI set-up and see if the laptop boots?

[COLOR=#0000FF]Booting in insecure mode [/COLOR]was there from the beginning. I remeber having problems installing Linux on this laptop a few years ago.
As I wrote, changing BIOS settings did not help.

---

### Post by mikewhatever on 2021-08-06
It looks like nothing is wrong other then the amount of free space on /dev/sda2. Now, 6% is over 50GB in your case, but 5% is reserved by default, so in reallity, only 1% is usable. There seems to be no need for any boot repair action.

You can free some space with that 20.04 USB by setting the reserved blocks percentage to a lower value, say 1%:
> sudo tune2fs -m 1 /dev/sda2

Hopefully, it will be enough for the system to boot, and then you can delete unneeded files, and ampty the bin. 

It is a good idea to keep at least 10-15% of free space.

---

### Post by tea for one on 2021-08-06
> **olivia89 said:**
>  I have deleted some files but it went to trash folder. I cannot empty trash folder in USB live mode. Besides, there are some important files in trash folder so I would like to empty only part of trash folder.

You can access Trash folder in a [COLOR="#0000FF"]live[/COLOR] session.

Navigate to the hidden folder:- olivia89 (or username) > .local > share > Trash > files

---

### Post by mikewhatever on 2021-08-06
> **tea for one said:**
> You can access Trash folder in a [COLOR="#0000FF"]live[/COLOR] session.

Navigate to the hidden folder:- olivia89 (or username) > .local > share > Trash > files

Yep, but ownership would probably be a problem. When in live session, you don't own any of the files in Trash, so you'll need to become root first, which is not particularly user friendly.

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> It looks like nothing is wrong other then  the amount of free space on /dev/sda2. Now, 6% is over 50GB in your  case, but 5% is reserved by default, so in reallity, only 1% is usable.  There seems to be no need for any boot repair action.

You can free some space with that 20.04 USB by setting the reserved blocks percentage to a lower value, say 1%:


Hopefully, it will be enough for the system to boot, and then you can delete unneeded files, and ampty the bin. 

It is a good idea to keep at least 10-15% of free space.

First, I executed "sudo tune2fs -m 1 /dev/sda2" but it still did not boot.
Second, I tried Repair-Boot again. Unfortunately, an error occurred during the repair again.

[https://paste.ubuntu.com/p/hXm9fxKrDP/](https://paste.ubuntu.com/p/hXm9fxKrDP/)

Disappointed to see a black screen "Booting in insecure mode" again, I started to write this post on another computer, and after a longer moment, it went to purple screen and finally I see my desktop now. It took a while. **What should I do now? I am afraid to reboot or turn it off!** What should I do in the future when experiencing such problem? Ultimately, it is hard to tell what helped. 

Should I delete at least 150 out of 1000 GB?
Should I execute "sudo tune2fs -m 5 /dev/sda2" in order to set the reserved blocks percentage to default 5%?

---

### Post by mikewhatever on 2021-08-06
Since it is up, try to delete or backup as many large file as possible. It should work, once more then 10% of the filesystem is free.

5% is a number from old days, when HDDs were small. I doubt it makes sence to reserve 50GB of a 1TB HDD these days, but if you want to set it back to 5%, you know the way. It shouldn't matter if at lease 10-15% or more is free.

The system might work slowly because of high fragmentation - the fuller the filesystem, the higher the fragmentation. If you need to keep lots of files, get an external storage device for regular backups.

---

### Post by tea for one on 2021-08-06
> **olivia89 said:**
> Disappointed to see a black screen "Booting in insecure mode" again, I started to write this post on another computer, and after a longer moment, it went to purple screen and finally I see my desktop now. It took a while. **What should I do now? I am afraid to reboot or turn it off!** What should I do in the future when experiencing such problem? Ultimately, it is hard to tell what helped. 

Do you see the Grub menu when you boot?
If not, I would allow Grub to display so that you can access previous kernels and recovery options.

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> Since it is up, try to delete or backup as many large file as possible. It should work, once more then 10% of the filesystem is free.

5% is a number from old days, when HDDs were small. I doubt it makes sence to reserve 50GB of a 1TB HDD these days, but if you want to set it back to 5%, you know the way. It shouldn't matter is at lease 10-15% or more is free.

The system might work slowly because of high fragmentation - the fuller the filesystem, the higher the fragmentation. If you need to keep lots of files, get an external storage device for regular backups.

It is going to be a problem now. Remember when I deleted files in live mode because Boot-Repair asked me to? Well, 90% of my HDD were movies stored in Home/Videos. I deleted Home/Videos folder in live mode. Now:

1) Despite the fact I deleted it, HDD is still nearly full.

2) Home/Videos folder fell under the trash icon. When I try to open it, it shows "[I]Unable to find requested file. Please check the spelling and try again".

[/I]3) I cannot even find these movies by their titles in system search. 

In sum, **at the same time, movies take up disk space on the HDD and they are gone**.

---

### Post by mikewhatever on 2021-08-06
You can try to check the size of Trash and ownership, just to make sure:
> du -hs .local/share/Trash

ls -l .local/share/Trash

I suspect the latter is off, and if that is the case, we can fix that.

PS: The boot-info output show there are a few old kernels that can be removed to free disk space:
> 
sudo apt-get purge linux-image-4.15.0-29-generic linux-headers-4.15.0-29-generic\
linux-image-4.15.0-147-generic linux-headers-4.15.0-147-generic
sudo apt-get --purge autoremove
sudo apt-get clean


---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> You can try to check the size of Trash and ownership, just to make sure:
I suspect the latter is off, and if that is the case, we can fix that.

```

du -hs .local/share/Trash

**17G        .local/share/Trash**

```


```

ls -l .local/share/Trash

[B]in sum 372 
drwx------2 lenovo lenovo 16384 aug 3 13:19 expunged
drwx------168 lenovo lenovo 155648 aug 3 23:47 files
drwx------2 lenovo lenovo 200704 aug 3 23:47 info[/B]

```

---

### Post by mikewhatever on 2021-08-06
So, the ownership is ok, and it doesn't look like a lot. Could it be that the Live USB created another Trash in /?

> ls -a /

---

### Post by mIk3_08 on 2021-08-06
Every system needs allocation space from a local disk. Your disk now is nearly full
This might be the cause of the system failure to boot to your desktop.
This command will erase all the files that are located inside your 
trash bin.
to empty the trash bin; run this command to empty your trash bin.
```
rm -rf ~/.local/share/Trash/*
```
This can be solve the issue you are facing right now.

---

### Post by mikewhatever on 2021-08-06
> **mIk3_08 said:**
> Every system needs allocation space from a local disk. Your disk now is nearly full
This might be the cause of the system failure to boot to your desktop.
This command will erase all the files that are located inside your 
trash bin.
to empty the trash bin; run this command to empty your trash bin.
```
rm -rf ~/.local/share/Trash/*
```
This can be solve the issue you are facing right now.

The OP previously stated this thermo-nuclear kind of bomming as undesirerable. There is also no need to force remove anything in this case.
I thik it is a bad advice.

---

### Post by mIk3_08 on 2021-08-06
> **olivia89 said:**
> ```

du -hs .local/share/Trash

**17G        .local/share/Trash**

```


You have a lot files inside your trash bin. **17G** that's huge enough for the trash bin.
Maybe this is the time to perform cleaning in your trash bin. so that can have 
free space in your local disk. To perform an empty command,
run this command in your terminal.

```
rm -rf ~/.local/share/Trash/*
```

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> So, the ownership is ok, and it doesn't look like a lot. Could it be that the Live USB created another Trash in /?


Please see the attachment.

---

### Post by mikewhatever on 2021-08-06
Yeap, there is /.Trash-0. So, let's see the same outputs:

> 
ls -l /.Trash-0
du -hs /.Trash-0


You'll probably need to change ownership:

```
sudo chown -R lenovo:lenovo /.Trash-0
```

Any way you can copy it somewhere other then the HDD, and then delete, ...at least some? ...I mean, are there any external storage devices in the house?

---

### Post by mIk3_08 on 2021-08-06
> **mikewhatever said:**
> The OP previously stated this thermo-nuclear kind of bomming as undesirerable. There is also no need to force remove anything in this case.
I thik it is a bad advice.
The disk is nearly full and if why should not empty the bin when all the files inside bin is already a trash? 
are you keeping garbage in your home for compost pit purposes, when the system is nearly dying? 
Why keeping something when we already have the cloud for safe keeping?

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> Yeap, there is /.Trash-0. So, let's see the same outputs:

[HTML]ls: cannot open directory (...) : permission denied

du: invalid option -- /
du: invalid option -- .
du: invalid option -- T
du: invalid option -- r
du: invalid option -- -
"du --help" for info

[/HTML]  

> **mIk3_08 said:**
> You have a lot files inside your trash bin. **17G** that's huge enough for the trash bin.
Maybe this is the time to perform cleaning in your trash bin. so that can have 
free space in your local disk. To perform an empty command,
run this command in your terminal.
```
rm -rf ~/.local/share/Trash/*
```
 
There are files in my trash bin that are needed for master thesis.
**I am ready to sacrifice all of my movies (hundreds of GB).**
And then I can move those files needed for mater thesis from trash to normal folder.

> **mikewhatever said:**
> Any way you can copy it somewhere other then the HDD, and then delete,  ...at least some? ...I mean, are there any external storage devices in  the house?

Excuse me, but I do not understand. What would I copy? I am ready to delete all of my movies in Home/Videos (a.k.a. .Trash-0 created by Live USB). I just would like to keep files from normal trash folder.

---

### Post by mikewhatever on 2021-08-06
Right, you can access the /.Trash-0 folder after changing its ownership. 

> sudo chown -R lenovo:lenovo /.Trash-0

---

### Post by mIk3_08 on 2021-08-06
> **olivia89 said:**
> 
 
There are files in my trash bin that are needed for master thesis.
**I am ready to sacrifice all of my movies (hundreds of GB).**
And then I can move those files needed for mater thesis from trash to normal folder.
Excuse me, but I do not understand. What would I copy? I am ready to delete all of my movies in Home/Videos (a.k.a. .Trash-0 created by Live USB). I just would like to keep files from normal trash folder.

You normally put important files in your trash bin? Why would you do that? That is a suicide! If you have important files specially thesis Files my advise is to put it in the cloud.
It is for safety purposes. We have lot free space that are available for free in the cloud. Why not using that? In this case; you can't perform empty command you should follow mikewhatever advise.
Good Luck!

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> Right, you can access the /.Trash-0 folder after changing ownership.

VIDEOS in Home still does not open.

```
sudo chown -R lenovo:lenovo /.Trash-0

ls -l /.Trash-0

[B]in sum 8
drwx------ 6 lenovo lenovo 4096 aug 03:48 files
drwx------ 2 lenovo lenovo 4096 aug 03:48 info[/B]


du -hs /.Trash-0
[B]
819G /.Trash-0[/B]


```

---

### Post by mikewhatever on 2021-08-06
There you go, 819GB is more like what I would expect from a movie folder.

Check the ownership of ~/Videos in home with <ls -ld ~/Videos>. You may need to reset it back to lenove with the following:
> sudo chown -R /home/lenovo/Videos

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> There you go, 819GB is more like what I would expect from a movie folder.

Check the ownership of ~/Videos in home with <ls -ld ~/Videos>. You may need to reset it back to lenove with the following:

```

sudo chown -R lenovo:lenovo /home/lenovo/Videoes

ls -ld ~Videos
[B]
drwxr-xr-x 2 lenovo lenovo 4096 jul 27 2019 /home/lenovo/Videos[/B]

```

VIDEOS in Home still does not open.

---

### Post by mikewhatever on 2021-08-06
Is is "Videos" or "VIDEOS", because these aren't the same. It is the former by default, I don't know where all caps come from.
Also, have you been able to free some space?

---

### Post by yancek on 2021-08-06
Keeping "important" file is the Trash bin?  Why would you do that?  If you have important files, you need to put them on an external hard drive or flash drive.

Moving files to the Trash bin is not the same as deleting them.  Moving files to the Trash bin is no different than moving them to any other folder such as Documents, Downloads, or Pictures folders. It will NOT free any space on the drive.

I don't see any point in using boot repair.  The problem with booting is that your drive is too full.  As pointed out earlier, drive filesystems generally need 5% of the drive for the filesystem.  This is a general amount.  I've seen drives with 3% free that booted and drives with 8% free that did not boot.  The general percentage of 5% is needed wheter you have a 50GB drive or a 4TB drive.

When a drive is full or nearly full, the first place to look to delete files is the /var/log directory.  You can have log files in the mulit GB size so take a look there if you can boot the installed Ubuntu.   Otherwise, if you are using a flash drive, mount the root partition of the installed Ubuntu from the usb and navigate to the /var/log folder and check the size of the files..

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> Is is "Videos" or "VIDEOS", because these aren't the same. It is the former by default, I don't know where all caps come from.
Also, have you been able to free some space?

I followed your commands and executed them. I was not been able to free any space because:
- I do not want to empty trash folder on my desktop,
- I can neither restore Videos folder with my movies in Home Folder, nor empty trash folder created by USB live mode. 

In my Home Folder I have these folders:
- snap
- Zotero
- 7 custom icons with logos in my language (Pulpit, Dokumenty, Pobrane, Muzyka, Obrazy, Publiczny, Szablony and **Wideo is missing**)
- 8 normal icons in English (Desktop, Documents, Downloads, Music, Pictures, Public, Templates, Videos)

On the left bar you can see that **Wideo fell under the trash icon**.

---

### Post by tea for one on 2021-08-06
> **mikewhatever said:**
> Yep, but ownership would probably be a problem. When in live session, you don't own any of the files in Trash, so you'll need to become root first, which is not particularly user friendly.

During a live session, you can copy a file from Trash and save it to a USB stick.

Then you can return the file to its original location after booting into your user directory i.e. /home/username.

Root privileges are not required because, I think, that the original owner is the same as the new owner (i.e. ownership has not changed on the journey in and out of Trash)

I suppose it depends on who is accessing the Trash and to where the file is being returned.

---

### Post by olivia89 on 2021-08-06
> **yancek said:**
> Keeping "important" file is the Trash bin?  Why would you do that?  If you have important files, you need to put them on an external hard drive or flash drive.

Moving files to the Trash bin is not the same as deleting them.  Moving files to the Trash bin is no different than moving them to any other folder such as Documents, Downloads, or Pictures folders. It will NOT free any space on the drive.

I don't see any point in using boot repair.  The problem with booting is that your drive is too full.  As pointed out earlier, drive filesystems generally need 5% of the drive for the filesystem.  This is a general amount.  I've seen drives with 3% free that booted and drives with 8% free that did not boot.  The general percentage of 5% is needed wheter you have a 50GB drive or a 4TB drive.

When a drive is full or nearly full, the first place to look to delete files is the /var/log directory.  You can have log files in the mulit GB size so take a look there if you can boot the installed Ubuntu.   Otherwise, if you are using a flash drive, mount the root partition of the installed Ubuntu from the usb and navigate to the /var/log folder and check the size of the files..

I did not turn my laptop off since I happily managed to boot it. 
There are 9 folders and 65 files (21 MB) in my var/log folder. There is 51,0 out of 928,9 GB of free space.


> **tea for one said:**
> During a live session, you can copy a file from Trash and save it to a USB stick.

Then you can return the file to its original location after booting into your user directory i.e. /home/username.

Root privileges are not required because, I think, that the original  owner is the same as the new owner (i.e. ownership has not changed on  the journey in and out of Trash)

I suppose it depends on who is accessing the Trash and to where the file is being returned.

Do I need to copy files from .Trash-0 created by USB live to a USB stick in order to delete them?
This is 819 GB of movies I decided to sacrifice and I do not have any drive with such space.

---

### Post by tea for one on 2021-08-06
> **olivia89 said:**
> 
Do I need to copy files from .Trash-0 created by USB live to a USB stick in order to delete them?

In post no. 3, you said [highlight]I cannot empty trash folder in USB live mode. Besides, there are some important files in trash folder so I would like to empty only part of trash folder.[/highlight]

Only you can decide what is important to save.

I was only offering advice concerning the access to Trash via a live session.

---

### Post by olivia89 on 2021-08-06
> **tea for one said:**
> In post no. 3, you said [highlight]I cannot empty trash folder in USB live mode. Besides, there are some important files in trash folder so I would like to empty only part of trash folder.[/highlight]

Only you can decide what is important to save.

I was only offering advice concerning the access to Trash via a live session.

Excuse my fatigue because I did not sleep and let me summarize.

You helped me with booting my laptop (I did not turn it off since then).  

 The problem is that earlier in live mode (USB) Boot-Repair asked me to free some space and I deleted Wideo folder from HOME. This Wideo folder contained all of my movies (819 GB). Now (not in live mode) I cannot access the Wideo folder, my movies are NOT in trash folder on my desktop and this 819 GB was NOT freed (I have only 51,0 out of 982,9 GB of free space).  I cannot empty trash folder on my desktop because there are important files that I am going to transfer to e.g. HOME/Downloads. I would like to empty this invisible trash folder created by live mode with my movies and to make Wideo folder in HOME accessible again. Could you please advise me on what should I do?

---

### Post by mikewhatever on 2021-08-06
So..., you've said before that "VIDEOS in Home still does not open." I am not sure where it is, and if it is all caps or not. Assuming it is /home/lenovo/Videos, we'll need to investigate.
The /.Trash-0 folder should be accessible after changing ownership. Since you want to delete it, just click and hit shift-del on the keyboard.
Alternatively, you can use the following command:
> sudo rm -r /.Trash-0

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> So..., you've said before that "VIDEOS in Home still does not open." I am not sure where it is, and if it is all caps or not. Assuming it is /home/lenovo/Videos, we'll need to investigate.
The /.Trash-0 folder should be accessible after changing ownership. Since you want to delete it, just click and hit shift-del on the keyboard.
Alternatively, you can use the following command:

Videos folder was not visible in home/lenovo as an icon. It was displayed on the left bar below the trash icon (it should be displayed below Pictures icon and over the trash icon). On the left bar you normally have: Recent,Home,Desktop,Documents, Downloads, Music, Pictures, and Trash. 

I executed "sudo rm -r /.Trash-0" and now I have 929,9 out of 982,9 GB. Luckily, my desktop trash was not emptied by that.

1. How can I restore Videos folder and icon?

2. Software Updater says "The software of this computer is up to date. However, Ubuntu 20.10 is now available (you have 18.04)". Should I do it? Is there any risk I can lose thesis files from Desktop?

---

### Post by mIk3_08 on 2021-08-06
Be careful removing Trash-0 Files. Trash-0 contains 819G Files. maybe your thesis is there.
When removing this Trash-0 their is no turning back. Thesis documents is very important.
When you can't retrieve this thesis document you will be going back to zero. "0"
This is no Good enough. Just want to say be careful when you decide. Yes its hard; But you 
have to retrieve first your Thesis Document before you decide to remove the Trash-0 Files. :-(
A lot in this community that is willing to help but maybe they haven't encountered this problem yet
But others already do know this. Maybe you just have to wait for other to reply for this.
Good Luck!

---

### Post by tea for one on 2021-08-06
> **olivia89 said:**
> 2. Software Updater says "The software of this computer is up to date. However, Ubuntu 20.10 is now available (you have 18.04)". Should I do it? Is there any risk I can lose thesis files from Desktop?

No, please do **_not_** do that, you will have a disaster on your hands based on the contents of this thread.
There is no direct path from 18.04 to 20.10

When you have sorted out back-ups of your thesis, personal data  and/or movies, then consider installing 20.04 LTS.

Edit: I do not mean an in-situ upgrade, I would recommend  a clean, fresh installation of 20.04 and then restore your back-up.

---

### Post by olivia89 on 2021-08-06
Thank you mikewhatever, tea for one, mIk3_08 and yancek. You have been of great help to me! I wish you all a happy weekend!

---

### Post by mikewhatever on 2021-08-06
> **olivia89 said:**
> Videos folder was not visible in home/lenovo as an icon. It was displayed on the left bar below the trash icon (it should be displayed below Pictures icon and over the trash icon). On the left bar you normally have: Recent,Home,Desktop,Documents, Downloads, Music, Pictures, and Trash. 

I executed "sudo rm -r /.Trash-0" and now I have 929,9 out of 982,9 GB. Luckily, my desktop trash was not emptied by that.

1. How can I restore Videos folder and icon?

2. Software Updater says "The software of this computer is up to date. However, Ubuntu 20.10 is now available (you have 18.04)". Should I do it? Is there any risk I can lose thesis files from Desktop?

1. Right, I can see that in the picture you've posted. Thanks for the explanation. Not sure what is wrong with it, but those left pannel links/bookmarks have a config file ".config/gtk-3.0/bookmarks". Check its content with 
> cat .config/gtk-3.0/bookmarks

2. No, 20.10 is no longer supported. You can upgrade to 20.04 after all the issues are sorted out.

---

### Post by olivia89 on 2021-08-06
> **mikewhatever said:**
> 1. Right, I can see that in the picture you've posted. Thanks for the explanation. Not sure what is wrong with it, but those left pannel links/bookmarks have a config file ".config/gtk-3.0/bookmarks". Check its content with 


2. No, 20.10 is no longer supported. You can upgrade to 20.04 after all the issues are sortedout.


Just rebooted it. It takes 50 seconds to boot to the purple screen and 1 min 45 seconds to see the desktop.
CPU and GPU 60-65 Celsius, HDD 39 Celsius.

---

