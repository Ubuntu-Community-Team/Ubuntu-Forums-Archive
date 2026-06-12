---
title: "Can't find my 2nd harddrive..."
date: 2005-11-02
forum: General Help
---

### Post by Master Magnus on 2005-11-02
Hello there, nice forum and a nice OS! Wow, I downloaded it yesterday and I really love it :p I've already started with some translation to swedish :)

But there's one thing, I can't find my second harddrive. I tried to access it through system/administration/disks but it wont open. I have the same problem with some other things in the topmenus. They are opening and it says "Opening" in the bottom of the screen, but then it dissappears and nothing more happens. 

I would appreciate an answer,
- Magnus

---

### Post by teaker1s on 2005-11-02
sounds like it's not mounted second harddrive until you mount it it won't appear

---

### Post by Master Magnus on 2005-11-02
Ok, what is mounting then? Sorry but I'm a newbie to this :)

---

### Post by mad_alfred on 2005-11-02
you have to mount the drive using the mount command from the console

go to /etc/fstab and have a look at it.

I'm assuming the drive you want to access is the one with windows installed so just have a look at what drives there are:

my layout is:

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1     /mnt/HD            ntfs     ro,user               0       0

so the windows drive must be "hdb1" because ut's formatted in ntfs.

now go to console and type 
sudo mkdir /mnt/HardDrive

then type 
sudo mount /dev/hd** /mnt/HardDrive

where ** stand for the ID of your hard drive .
If you don't find your drive in fstab you have a look in the /dev folder, you'll find a series of hda hda1 hda2 hdb1 etc... your drive is one of those.

if it's an ide slave then it's usually hdb where the number ( hdb1 hdb2... ) usually stands for the partition.

if it's a sata drive it's called hds hds1 hds2 etc...depending on how many partitions you've got.

:)

---

### Post by mad_alfred on 2005-11-02
sorry u forgot..at the end of the proces if everything went right the drive will be accessible at /mnt/HardDrive which will show as a folder

---

### Post by teaker1s on 2005-11-02
[http://ubuntuguide.org/](http://ubuntuguide.org/)

helped me there is a windows section if your mounting ntfs

---

### Post by Master Magnus on 2005-11-02
[QUOTE=mad_alfred]you have to mount the drive using the mount command from the console

go to /etc/fstab and have a look at it.

I'm assuming the drive you want to access is the one with windows installed so just have a look at what drives there are:

my layout is:

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1     /mnt/HD            ntfs     ro,user               0       0

so the windows drive must be "hdb1" because ut's formatted in ntfs.

now go to console and type 
sudo mkdir /mnt/HardDrive

then type 
sudo mount /dev/hd** /mnt/HardDrive

where ** stand for the ID of your hard drive .
If you don't find your drive in fstab you have a look in the /dev folder, you'll find a series of hda hda1 hda2 hdb1 etc... your drive is one of those.

if it's an ide slave then it's usually hdb where the number ( hdb1 hdb2... ) usually stands for the partition.

if it's a sata drive it's called hds hds1 hds2 etc...depending on how many partitions you've got.

:)[/QUOTE]
Thanks for that, but I don't have windows installed on it. I'm only running Ubuntu. I'm running it on master (40 gig) and got another installed as slave (200 gig). And I can't reach that. Do I still have to mount it even though windows isn't isntalled on it?

---

### Post by pickarooney on 2005-11-02
I also found when I first installed Ubuntu that even though my second HD was mounted (took me a while to find the /media thing), I had no write-access to it as a normal user, so I had to use **sudo chmod -R a+w /media/hdb1**

---

### Post by mad_alfred on 2005-11-02
yes, it should work.:D

---

### Post by mad_alfred on 2005-11-02
[QUOTE=pickarooney]I also found when I first installed Ubuntu that even though my second HD was mounted (took me a while to find the /media thing), I had no write-access to it as a normal user, so I had to use **sudo chmod -R a+w /media/hdb1**[/QUOTE]

i just always access as root... it's a lot faster, i hate having problems with permissions!! :P..but this is just me...

---

### Post by Master Magnus on 2005-11-02
Sorry, but how can I access the console? I have the swedish version so I don't know what the name is... :oops:

---

### Post by teaker1s on 2005-11-02
run as a different user  in aplications system tools and run  'gnome-terminal'
is the command to start console 
or in system tools you will see a computer monitor icon with black screen and >_ on the icon screen

---

### Post by Master Magnus on 2005-11-02
Thanks for all help :)

---

### Post by Master Magnus on 2005-11-02
Or the other problem, I can't run some things like "Discs" and a few more... What shall I do?

---

### Post by pickarooney on 2005-11-02
[QUOTE=Master Magnus]Or the other problem, I can't run some things like "Discs" and a few more... What shall I do?[/QUOTE]

Can you clarify that last bit? You can't access disc-drives or something else?

---

### Post by Master Magnus on 2005-11-02
What I meant was that when I'm clicking at System-Admin-Discs it wont start. It's just saying "opening" at the bottom but no more.

---

### Post by Master Magnus on 2005-11-03
I can't even get my 2nd drive... I will provide you with some screenshots here:

[www.mgsworld.org/ubuntu](www.mgsworld.org/ubuntu)

1. I'm checking the fstab-file, but the drive wont show up.
2. In the dev-folder, it's showing up.
3. Starting the terminal and writes what you told me.
4. Pressing enter and that prompt comes up.
5. Writing in the password (nothing shows up. Normal?
6. I'm writing the second line you told me to write.
7. Pressed enter.
8. Checking the mnt-folder, nothing there.

Why can't I just get it to work? :(

---

### Post by pickarooney on 2005-11-03
Type **ls -alF /mnt/HardDrive**.
What's on the second HD and what filesystem is it using? (e.g. Windows with NTFS).
You seem to have done everything correctly, with the possible exception of the mount command, you might need to specify the filesystem (although normally it would complain just after you typed it in).

It's very strange that when you look with Nautilus the directory /mnt is empty, as you've just created a directory (HardDrive) on it... unless you're actually looking at another directory called mnt? (try clicking on Upp until you can go no further and then open the mnt directory again.

---

### Post by Master Magnus on 2005-11-03
It's the right folder, I'm sure of it.

I got some files on it, but it is partitioned (200 = 180+20). No Windows, just files in NTFS. Can is be somethiing woth the partitions? Thanks for your help.

*When I typed _Is -alF /mnt/HardDrive_ this came up:
_ls: /mnt/HardDrive: Filen eller katalogen finns inte _
which means:
(ls: /mnt/HardDrive: File or directory does not exist)

---

### Post by pickarooney on 2005-11-03
And **sudo ls -alF /mnt/HardDrive** gives the same message?
I'm new to Ubuntu so I don't know what the story is with reading from and writing to NTFS drives. It may require installing something to enable you to read the filesystem, but someone else will have to help you if that's the case, I'm afraid.

You can read [this](http://ubuntuforums.org/showthread.php?t=82224) thread and [this](http://ubuntuforums.org/showthread.php?t=24989) one and perhaps [this](http://www.debian-administration.org/articles/247) one. Just don't get discouraged, I'm pretty certain you'll have
a) mounted a readable NTFS partition and
b) understood the basics of mount/fstab
by the end of the day :)

---

### Post by Master Magnus on 2005-11-03
Thanks for your help. I will test the sudo if and read the topics now :)

---

### Post by Master Magnus on 2005-11-03
***Sorry, double-posted because it didn't load :) ***

---

### Post by teaker1s on 2005-11-03
right click gnome panel and select add to panel and select disk mounter
for ntfs if your still stuck [http://ubuntuguide.org/](http://ubuntuguide.org/)
windows section there is mount ntfs-worked for me-what ever you do don't be tempted to have disk as write access-you want read only or you risk ntfs corruption

---

### Post by Master Magnus on 2005-11-03
When I added the mounter there came three buttons - 3,5" disk + Cd/dvd + cd-rw. The dvd could be mounted, but not the others. And the harddrive wouldn't even show up :(

---

### Post by teaker1s on 2005-11-03
e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4. To mount Windows partition

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

   5. To unmount Windows partition

sudo umount /media/windows/

note this method will create a windows folder on linux and you will see contents of windows

hda1 is ide o master if your ntfs harddrive is connected slave(drive controller2)or otherwise see below


drive name	drive controller	
/dev/hda	1	1
/dev/hdb	1	2
/dev/hdc	2	1
/dev/hdd	2	2

---

### Post by Master Magnus on 2005-11-03
It seems like it has something to do with the "sudo". When typing sudo at the beginning of a line it ownt happen anything. But when I'm not writing it an error comes up "only root can do it".

I'm started to get pretty bored of this... :(

---

### Post by teaker1s on 2005-11-03
okay easy way of checking this out is system-administration-users and groups
then select your login and select properties then user privileges make sure all tick boxes are selected and you should be able to sudo etc etc other than this I'm wondering if the iso you installed was damaged if various things don't work.

someone else maybe can advise on sudoers list more than I can as I'm ex windows & I prefer to try the gui route first-because I'm new at this too

;)

---

### Post by Master Magnus on 2005-11-03
Yes, it may be damaged. I orderred a few CD's 2 days ago and it looks like I need them :) I was gonna handle out to friends and so but I'm thinking of reinstall it with one of the new CD's I am going to get. Maybe I should try to reinstall it already, and see if I put some settings wrong i the install... :/

---

### Post by pickarooney on 2005-11-03
I doubt there's anything wrong with the CDs - that's usually what people convince themselves when they can't fix something (I used do it a lot :D)

It's normal that when you prefix a command with **sudo** that you don't get the error message, as the error message is effectively saying "type the same thing again, but prefix it with sudo"

Before downloading/ordering new CDs, try each of the steps teaker1s listed. If something doesn't make sense, don't ignore it, just ask for a more in-depth explanation, and always post up your results so people can try see what's going on. Something that might be meaningless to you could show an obvious problem to someone else.

As far as I can make out from your screenshots, you should replace **hda1** with **hdb1** in teaker1s' instructions.

Keep us posted with what happens and don't lose faith :)

---

### Post by Master Magnus on 2005-11-03
Finally! I reinstalled it and tested to mount it again. IT WORKS!!!

Thanks for all of ypur help :) I'm very greatful!

---

### Post by pickarooney on 2005-11-03
Glad it works, even if it's somewhat a pity nobody knows why exactly :D
Happy Ubuntuing.

---

### Post by teaker1s on 2005-11-03
i killed gnome and had to reinstall the gnome base as it started refusing to create users and various other issues and permission issues too 
I now have kde and gnome and all seems well except although I deleted a corrupted user I can't make a new account in that name-strange

---

### Post by Master Magnus on 2005-11-03
How do I change the permissions so I can edit the files without being logged in as root?

---

### Post by pickarooney on 2005-11-03
with the **chmod** command, like so

**sudo chmod a+rw filename**   (gives read and write access to everyone).
you can use **chmod +x** to give execute access or make everything from the root down read/write/executable with

**chmod -R 777 /mnt/Harddrive** *

* Be careful when changing permissions on a lot of files. If there may be files to which only root should have access anywhere beneath the path you specify, don't change them or your system may become unstable.

The man page gives the full list of options (type **man chmod**)

---

### Post by teaker1s on 2005-11-03
create launcher and comand 'gksudo nautilus' this will give in effect a file browser as root

Right click on files/folders -> Properties

Permissions Tab -> Read/Write/Execute (Checked the permissions for 
Owner/Group/Others) 

can change permissions in terminal but I can't remember the method

---

### Post by Master Magnus on 2005-11-03
Hm, it says after every file "File only readable" and when I'm running Nautilus as root and I'm trying to change that it way it says "cannot change permission because the disc is write-protected"

---

### Post by teaker1s on 2005-11-03
which disk are we talking about your windows ntfs?

---

### Post by Master Magnus on 2005-11-03
Yeah, both of the ntfs-partitions (hdb1 and hdb5).

---

### Post by teaker1s on 2005-11-03
the settings I gave you allow only read access-this is because linux write access on ntfs is at best dodgy as hell and the general opinion is don't do it-I also believe that ubuntu kernel has NTFS write disabled as there is a great risk of it corupting all your data.

NTFS is still a new ability your best bet would be to copy files you want to your linux hard disk and change the permissions from there on:KS

---

### Post by Master Magnus on 2005-11-03
So copy all of the files to my linux drive and then reformat hdb1 and hdb5, and then move them back?

---

### Post by teaker1s on 2005-11-03
if your going the linux way then possibly the best way, but before you do see what other people say as I'm new to this too ;)

---

### Post by Master Magnus on 2005-11-03
Well, the other people that I've talked to are telling me that this is great so I think I will :) Thanks for your help, I'm amazed over your knowledge even though your new to it :o

---

### Post by teaker1s on 2005-11-03
the truth is I used to build and still maintain pc's with ms windows, I've only been using ubuntu linux for a month but the community and the wilki are amazing.
I would guess that at first you feel that linux is alien-I did but as I understood that the   
desktop is for every day tasks and the konsole is for under the bonnet tweaks it slowly becomes easier.
I make a point of reading posts on the forum if I think I may encounter the problem and learn on the way.
I'd encourage not let setbacks get you down as most are easy to fix and if it does blow up on you you can always reinstall damaged packages
(not like windows where it gets past a certain point it's screwed and it's reinstall time)
Oh and yes before you ask I've broken ubuntu already and with some help fixed it;)

---

### Post by Master Magnus on 2005-11-04
Well, now I have copied them to a folder on my home-partition (hda1). But how can I change the file-system on the write-protected disk hdb1 and hdb5 from ntfs to ext3? If I'm trying to delete a file it just says that it can't because it's writing-protected :(

---

### Post by pickarooney on 2005-11-04
Just format the windows disks with disc manager, i.e. wipe them and reformat them as ext3.
If you had Windows installed on your PC you could simply have converted the filesystem from NTFS to FAT32, which is read/writable by Linux. (useless info now, but in case there's a next time).

---

### Post by Master Magnus on 2005-11-04
Do I have to go through the terminal or something, because the button that says format is unavailable...

EDIT: I had to inactivate it :)

---

### Post by Master Magnus on 2005-11-04
Ok, now I've got this problem:

I have done as you said with the mounting, moved all files from hdb1 and hdb5 to hda1, reformatted hdb in ext3 and moved the files back. Now I've restarted the computer and it can't find the second drive again. How shall I do?

---

### Post by scarabaeus on 2005-11-04
i have a similar problem and cant find anything on the net or the forum. maybe you guys can help:

i'm having 2 harddrives. allthough i can perfectly mount them trough aministration -> disks and use them, the next time i log on, they are gone again...

(2 partitions, one FAT the other swt3)

do i have to go and edit my fstab?

cheers 

PS: nice forum. i hope to contribute as soon as i got rid of my neeby-status...

---

### Post by teaker1s on 2005-11-04
Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

   
e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

   6. Save the edited file (sample)
   7. Read How to remount /etc/fstab without rebooting?

Q: How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
     Local mount folder: /media/windows

   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

   6. Save the edited file

---

### Post by scarabaeus on 2005-11-04
thx for you help teaker1s. things work just fine now...:) 

there was some kind of misunderstanding i guess. i was using horay and had problems with the mounting (noob). then when i installed breezy and saw this disks-tool i assumed it would modify my fstab. after all, ppl normally don't want to mount a harddrive only once. anyways, i was wrong, so:

the disks-tool does NOT change fstab.

one more thing learned...

cheers

---

### Post by jessecollins on 2006-12-16
Thanks, I got this working now.  :D

---

