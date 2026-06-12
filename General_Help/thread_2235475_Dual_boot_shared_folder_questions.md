---
title: "Dual boot shared folder questions"
date: 2014-07-21
forum: General Help
---

### Post by pages on 2014-07-21
Hi all , 

I've been researching the best solution for my current setup and seem to be running into issues
Currently Dual booting win7/ubuntu (via [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) install ) 

Ideally I'd like a shared folder with RW permissions so i can access the files on either Linux or windows. Here's the different approaches I've tried 


[LIST]
[*]I downloaded ext2fsd to view folders and files.
[/LIST]
[INDENT]However when i go into the home folder (on windows via ext2fsd) I'm told the folder was unmounted for protection[/INDENT]
[INDENT=3]From the graphical desktop, click on: 
[/INDENT]
[INDENT=3] "Access Your Private Data" 
[/INDENT]
[INDENT=3]
[/INDENT]
[INDENT=3]or 
[/INDENT]
[INDENT=3]
[/INDENT]
[INDENT=3]From the command line, run: 
[/INDENT]
[INDENT=3] ecryptfs-mount-private  
[/INDENT]
[INDENT]When I boot back into Ubuntu these files don't exist but even running ecryptfs-mount-private via terminal doesn't stop the behaviour on windows.[/INDENT]




[LIST]
[*] I was following this [guide]("http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/") on how to harmonize Ubuntu and Windows
[/LIST]
[INDENT]When following the guide I got to this point 
```
[FONT=monospace]sudo mkdir /media/storage
[/FONT][FONT=monospace]sudo blkid[/FONT]
```
However in the output i couldn't find storage 
Tried using Gparted to create a partition NTFS which it did , but still when running blkid it wouldn't show up.[/INDENT]




[LIST]
[*]Next I went back to ext2fsd type approach since I could at least browse the folders in that.
[/LIST]
[INDENT]Created a /storage folder with 777. 
I moved my movies/photos in there and could at least view them from windows but If i tried to edit any files I would get write protected errors.

sudo setfacl -d -m other:rw /storage/
This seemed to me at least logically what I wanted since i wanted every file within this folder to be read/writeable by anyone ( windows user ) 
But still getting issues [/INDENT]



[LIST]
[*]Looked up similar [programs]("http://www.paragon-drivers.com/extfs-windows/") which boast the ability to force write on ext4 but no joy
[/LIST]

Any help in regards to what I'm trying to do would be helpful since a lot of the information online is about Samba shares which isn't relevant to me 
Just in case people are wondering , While I am happy that i can run movies/files I'd still like to be able to alter files while also having the ability to run .exe downloaded via the Ubuntu OS

---

### Post by Mark Phelps on 2014-07-21
Sorry, but continuing to use Wubi is a serious mistake.  It has been abandoned with the release of Windows 8.

---

### Post by pages on 2014-07-21
> **Mark Phelps said:**
> Sorry, but continuing to use Wubi is a serious mistake.  It has been abandoned with the release of Windows 8.

Actually turns out I used [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) to install Ubuntu , just said wubi by mistake/previous always using wubi to install.
I'll edit the original post to remove that . Hopefully it's not the same case with Linux live being outdated ?

---

### Post by Impavidus on 2014-07-21
Easiest is using a shared ntfs partition. [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) You don't have to install anything, as ntfs-3g is installed by default nowadays. It's very easy. I edited fstab manually & correctly 10 minutes after I installed Ubuntu for the first time.

---

### Post by oldfred on 2014-07-21
Back in 2006 one of the first things I did was create a shared FAT32 partition, I then in 2009 converted to NTFS as FAT32 has many limits.
I still have my NTFS shared data partition as I have not totally reorganized, but do not use XP anymore. In my NTFS partition are my Firefox & Thunderbird profiles so all my installs share the same bookmarks and email.

Create NTFS partition with gparted. Then mount it in fstab so it always is mounted on reboots.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

        
 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

           
 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

    
Then you can link your folders in you shared partition into your /home. 
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by pages on 2014-07-21
Cheers for the replies guys. 


Although I can't believe how much hard work i made of something so easy.

In the end I just created a new partition using Windows disk management
Mounted that on ubuntu and can share files (going to edit fstab to make it mount on boot now )
Can read/write/execute any files i need too. 

Sorry for wasting everyone's time

---

### Post by oldfred on 2014-07-21
Best never to use Windows to create partitions. It will convert to dynamic partitions if you have the 4 primary partition limit and are not using extended partition. And there is no official or easy undo of dynamic partitions.

Glad you got it working.
With NTFS you set default ownership and permissions with mount in fstab.
It will show root but you have full use.

---

### Post by Mark Phelps on 2014-07-21
> Sorry for wasting everyone's time 

You're NOT wasting our time -- we're here to help.  The fact you learned something useful from this situation makes it worthwhile on its own.

---

