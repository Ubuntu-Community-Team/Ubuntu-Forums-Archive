---
title: "How to change permissions on locked Mac files"
date: 2012-12-01
forum: General Help
---

### Post by Gazucha on 2012-12-01
Hola people,   I used to use Macs, although gave up after various Hardware failures, however there are still a lot of personal files on an external back-up Time Machine, as well as the actual Hard Drive from one of the dead Macbooks, which I would like to Format and sell (we lost a LOT of money with Mac).                                                                          I would like to know the commands to change ownership and read/write permissions.    I imagine it is some kind of chmod and chown commands?                                                                                                                                            I can currently access and read 'most' of the files.                                                                                                                                                      One last thing, the name of one of the Partitions has a space in it. What happens there?   Any help would be great.                                                                                                                                                 Thanks in advance.

---

### Post by dino99 on 2012-12-01
as i know (dont have/had MAC) it use the linux commands:

be root: sudo / sudo -i / ...
set the user (you) to be admin: check the users & groups settings, user need to be added to admin group and sudo group

and now, the rough way: if you dont care about the data (nothing to backup), then formatting the hdd(s) or some partition(s) is the easiest way. I dont know the special tools on  MAC to do multiple erases at once (writing 0 several times over all the support to make recovery impossible)  . But if you have an ubuntu installed, then you can use nwipe for example (from an usb stick or other).

---

### Post by Gazucha on 2012-12-01
I think I must be a bit thick.  You lost me already.  I know how to enter root. i.e. sudo -i   "set the user (you) to be admin: check the users & groups settings, user need to be added to admin group and sudo group"   ???????????????????????????????????????????????????????????????????????  I'm lost.

---

### Post by coffeecat on 2012-12-01
The Time Machine backup will be formatted with the journalled version of HFS+ which you can access read-only from Ubuntu, which is why you won't be able to change ownership and permissions while the files are still on that drive. (There is a way of force-mounting it read-write from Ubuntu, but not something I would advise, at least until you've backed it up.) Added to which the owner will probably be UID=501 for your Mac files, whereas the UID of the Ubuntu account you are working from is probably 1000. Which is why you see a padlock on some of the files/folders, depending on what the specific permissions are.

If you have access to a Mac machine, you can change the permissions of the padlocked files from the MacOS finder. If not, one way round this is to use a file manager in Ubuntu with root privileges to copy to another drive or partition. If you are copying to a ext3/4 filesystem you would then need to run recursive "sudo chown" and "sudo chmod" on everything you've copied to get ownership and permissions right. But a neat way of side-stepping the ownership/permissions issue is to copy to a Windows filesystem, either NTFS or FAT32, NTFS to be preferred. By doing this you lose the ownership and permissions from the HFS+ filesystem and inherit ownership/permissions from the mount options. Plug in an external HD formatted NTFS, for example, and it will be mounted for you. After copying everything to the NTFS filesystem, you can then copy it all to wherever you want without any special manipulation.

So - my preferred option:

[list][*]Plug the time machine drive in, let it be automounted, and then close the Nautilus window that has just opened.
[*]Run this to open a root Nautilus:
```
gksudo nautilus
```
Navigate to where your HFS+ filesystem is mounted, somewhere in /media. To make it slightly easier, you could run:
```
gksudo nautilus /media
```
[*]Plug in a NTFS-formatted drive, let it be automounted and leave the new nautilus window open.
[*]Drag and drop your folders and files from the HFS+ filesystem to the NTFS one. You now have all your stuff on the NTFS fileystem and available whenever you want.
[/list]

If you use this NTFS/FAT32 trick, you don't need to worry about any spaces in any filename or folder name, because you'll be using drag and drop in the GUI.

Caveats: Both NTFS and FAT32 don't allow some characters in filenames and may error with some files. FAT32 has a maximum 4GB for filesize.

---

### Post by Gazucha on 2012-12-02
Hi Coffecat,  tried what you said via Nautilus and NTFS but unfortunately Permission is still denied.  Perhaps I need to try and find a friendly soul with a Mac that isn't broken? :)

---

### Post by coffeecat on 2012-12-02
Where is permission denied? When you try to access files on the Time Machine backup or when you try to write to the NTFS filesystem? More details and we might be able to figure this out.

---

### Post by Gazucha on 2012-12-02
WTF is it with UF that ALL of my posts now come out in one bulk? As if written by a child? Hello again,  &quot;Permission Denied&quot; after I drag the item into NTFS.   Although even after opening via 'gksudo nautilus', the folder for the Mac drive appears with a padlock.  I can access most files by right clicking and selecting &quot;open as administrator&quot;  One last thing, after entering 'gksudo nautilus /media' it just hangs on,'Initializing nautilus-image-converter extension' ?  Hope that helps.

---

### Post by coffeecat on 2012-12-02
> **Gazucha said:**
> ALL of my posts now come out in one bulk? As if written by a child? Hello again,  &quot;Permission Denied&quot;

It's nothing to do with the forum, but probably something to do with your browser settings. I really wish I knew. People bring this up occasionally in Forum Feedback & Help and then never bother to post again when members suggest things to try. All I can say is that the forum has **never** replaced " with &quot for me, or put fragments of html code in my posts. Have a look at your javascript settings, or no script if you have it installed. 

> **Gazucha said:**
> One last thing, after entering 'gksudo nautilus /media' it just hangs on,'Initializing nautilus-image-converter extension' ?  Hope that helps.

Which version of Ubuntu are you running? nautilus-image-converter is for gnome2 based desktops - it doesn't work with gnome3 and it looks as though it is interfering with opening nautilus. Ubuntu version 11.10 and later are based on gnome3.

---

### Post by Gazucha on 2012-12-02
No prob's I'll check the browser settings...   There is a spare hard drive and install DVD's of earlier Ubuntu's. I'm on 12.04.  Give me some time and I'll set-up a disk with 11.04 or 11.10 and try again.  Thanks for your input.

---

### Post by coffeecat on 2012-12-02
> **Gazucha said:**
> Give me some time and I'll set-up a disk with 11.04 or 11.10 and try again. 

Before you do that, or alternatively...

> **Gazucha said:**
> I'm on 12.04.

It's just possible that nautilus-image-converter being a gnome2 applet is the cause of your nautilus problems in 12.04. Try uninstalling it, and then try my suggestions again for copying HFS+ -> NTFS.

By the way, 11.04 uses gnome2 libraries, 11.10 uses gnome3 libraries.

OT hint - if you want the gnome3 equivalent of nautilus-image-converter in 12.04, you need the package nautilus-image-manipulator.

---

### Post by Gazucha on 2012-12-04
Hi Coffeecat,  Progress...   well, I have been occupied trying out your suggestions and actually managed to extract almost all the files from the Macbook HD. So thanks a million for that. Who was the smart cookie who worked out using an NTFS drive?   Unfortunately the Time Machine is not playing by the same rules so unless you have another idea, it looks as though I shall have to find a Mac somewhere.   It could be that I am entering the command wrong. Do I leave the gap between Time and Machine? or use \ or what?

---

### Post by coffeecat on 2012-12-04
With my suggestions you shouldn't have to use the terminal at all and not worry about spaces in filenames. But for the record, "Time Machine" would be "Time\ Machine" in the terminal (ignoring the quotes).

I'm still puzzled that with a gksu nautilus file browser you are not able to access some of your own files. Can you clarify one thing? You are only looking in the /Users folder, aren't you? (Equivalent to /home in Ubuntu.) I can understand if you can't get to some files in the system folders, but in /Users/yourusername you *should* be able to access everything and that's the only place your files should be.

---

### Post by Gazucha on 2012-12-04
Surely I had to use terminal in order to gain access to the files no? In 11.04, I typed 'gksudo nautilus /media' which displayed various icons in full colour, then accessed 'Gazucha' on the old HD via the 'Users' folder. These files were not visible or accessible before. I thought the nautilus command had sorted this. As for the Time Machine, I tried exactly the same command, however when opening 'Users', only the Gazucha folder is in colour and the 'shared' is grey and seemingly empty. Likewise upon opening 'Gazucha', perhaps 10% of all the files and folders are in colour and accessible. The rest are grey and reading 0 bytes. I can also only copy occasional photo's, (no film's nor documents) from Time Machine perhaps 1% of all the stuff contained within.

---

### Post by coffeecat on 2012-12-04
gksudo nautilus will show you every file that is there. But I've just realised, there may be something about Time Machine backups. They are incremental and the file structure may be different from what you would see in a HD taken out from a Mac. I'm more than a bit hazy on the details of Time Machine - I've never bothered with it with my Mac.

---

### Post by coffeecat on 2012-12-05
Sorry not to add more at the time of the last post. I was caught up in some priority forum admin work. Anyway, wikipedia has a brief description of how the folder structure might be on your Time Machine drive:

[http://en.wikipedia.org/wiki/Apple_Time_Machine#How_it_works](http://en.wikipedia.org/wiki/Apple_Time_Machine#How_it_works)

I can't think offhand what the grey folders/files are - perhaps a screenshot would help - but are you having to navigate into each folder named with date and time and thence into the Users folder to find all your files?

---

