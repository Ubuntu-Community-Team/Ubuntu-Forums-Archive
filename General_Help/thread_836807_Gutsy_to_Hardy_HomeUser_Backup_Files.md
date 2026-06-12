---
title: "Gutsy to Hardy Home/User Backup Files"
date: 2008-06-21
forum: General Help
---

### Post by rustyz on 2008-06-21
i have installed Hardy, after inserting my Home/User backup data files CD... music/docs/photos/ect...

the files have been locked, tried many a fix with no luck...

does anyone have a way to get all of my files on a new fresh instalation of Hardy, from my Gusty, without the Data CD process, and without having them stil locked as a only user?

does the USB flash drive work, or another way?

this is also a problem with the new distros of Fedora, and Opensuse

one more question, could this be a computer hardware issue, or a bios setting issue?

do not see how, just reaching for anything...

thanks

---

### Post by cariboo on 2008-06-21
Can you not access the cd using gksu nautilus?

Jim

---

### Post by tact on 2008-06-21
What exactly have you tried?  

How did you back up the files?  Just copy/burn them to the CD?  Or are they archived in some way?

If you just copied the files and its a permission issue stopping you copying them back then try this...
Copy all the files using sudo to somewhere on your HDD.  If you want to do this using a GUI then press ALT-F2 and type "gksudo nautilus"

This will have you in nautilus with superuser privs so be careful not to do anything silly.

Navigate to the CD folders you want back on your HDD.  Select them, copy@paste to somewhere on hour HDD.  Choose an empty new folder just to ease confusion and make life easy later - copy/paste all files/folders there temporarily.   Then after the paste is done right click on the temporary folder and change permissions to what you want, change owner to you, change group to you, and check the box to apply to all contained files and subfolders.

Get out of super-nautilus now.  You don't want any heartaches huh?  :)

Then organise the files how you want.

In more detail using commandline in terminal:
```
mkdir ~/working
```Puts a new folder called "working" in your home directory.  (i.e. /home/your-username/working)

```
sudo cp /media/cdrom/* ~/working
```Assumes you want to copy the entire CD to the working folder on your HDD

```
sudo chown -hR your-username ~/working
```Change ownership of all files/folders recursively in "working" to you.    Change "your-username" to whatever your username is.

```
sudo chgrp -hR your-username ~/working
```Change group of all files/folders recursively in "working" to you.    Change "your-username" to whatever your username is.

```
sudo chmod 0755 -R ~/working
```make all files/folders in ~/working read/write to you, read only to all others.

Now you can go use Places>Home Folder and see the "working" folder.  You can then move files where you want them.

---

### Post by rustyz on 2008-06-22
tact> How did you back up the files? Just copy/burn them to the CDcopy as data/burn

installing hardy again, and will try as root under gksudo nautilus first...

i've tried so many things, i think that was one of the first ones...

also tried chown commands as myfiles, changing user groups, and permisions, read write files and more!

will get back with results...

i see there are 195 updates after new install, maybe one is a fix...

---

### Post by rustyz on 2008-06-22
ran cd under gksudo nautilus... Locked!

error while moving files...
permissions denied!

i tried edit users and groups/advanced...

my name(user) all grayed out...

and all the rest...

home/user

shell- /bin/bash

main group

user ID

i will try from the command line as tact mentioned...

i also did something like this as myfiles instead of "working"

here we go!

---

### Post by issih on 2008-06-22
Odd problem....One thought, you could try formatting a flash drive as ext2 using gparted, that way it ought to preserve user permissions. If you then create the same user names on the hardy install, it might work out nicely, not 100% sure though

---

### Post by rustyz on 2008-06-22
user@user-desktop:~$ mkdir ~/working
mkdir: cannot create directory `/home/user/working': File exists
user@user-desktop:~$ sudo cp /media/cdrom/* ~/working
cp: cannot stat `/media/cdrom/*': No such file or directory
user@user-desktop:~$ 

tact, thats as far as it would let me go...

---

### Post by tact on 2008-06-24
> **rustyz said:**
> user@user-desktop:~$ mkdir ~/working
mkdir: cannot create directory `/home/user/working': File exists
user@user-desktop:~$ sudo cp /media/cdrom/* ~/working
cp: cannot stat `/media/cdrom/*': No such file or directory
user@user-desktop:~$ 

tact, thats as far as it would let me go...

Ok...  sometimes when a CD is inserted it is not mounted on /media/cdrom.   When you insert the CD does ubuntu automatically open up a folder to display the files?  Look at the top in the location bar and see whats there... it may be  "/media/your-cd-label" instead of /media/cdrom

By way of example.  When I insert the latest Fedora CD in my drive it is mounted on 
/media/Fedora-9-Live-i686 instead of /media/cdrom  (pic attached)


once you know where the CD is mounted then the replace this command
```
sudo cp /media/cdrom/* ~/working
```with:
```
sudo cp /media/your-cd-label/* ~/working 
```

---

### Post by rustyz on 2008-06-24
tact, will give it a try later...

i'm confused by what it should be changed to...

> sudo cp /media/your-cd-label/* ~/working

what exactly is your-cd lable?

---

### Post by rustyz on 2008-06-24
well, i managed to mess up that install...

odd thing, as i go to direct install, not run live...

"this time, i ran it live, and i see the example file is locked!"

installing it now, and will get you the info you asked for tact...

when a cd data disk was in the other insallations, it read the disk no proplem, just as mentioned, they were locked...

---

### Post by tact on 2008-06-25
> **rustyz said:**
> tact, will give it a try later...

i'm confused by what it should be changed to...

what exactly is your-cd lable?

Ahhh sorry that is confusing.  What I was indicating in the previous posts is that sometimes when a CD is inserted and mounted for use by the system is is mounted on /media/cdrom

Sometimes its not mounted on /media/cdrom.  To find out where a particulat CD is mounted:
- assuming your system is up and running
- insert the CD and wait
- soon an icon representing the CD will appear on the desktop (correct?  This happens for you?)
- also a window will open up displaying the files and folders on the CD. (this happens for you?)

Assuming all that happens...  look at the "Location bar" of the window that opens up.  It may say "/media/cdrom0" or it may say something else like "/media/something-else".

Replace the "something-else" in the command below with what actually is displayed in the location bar of the window that popped up after inserting the CD

```
sudo cp /media/something-else/* ~/working
```

---

### Post by rustyz on 2008-06-25
> look at the "Location bar" yes system is installed, the icon shows, and it opens in file browser, with no location bar... 

now what?

could this be a partition thing, i insta;; "guided use entire disk...

see other post of mine for more info...

[http://ubuntuforums.org/showthread.php?t=839728](http://ubuntuforums.org/showthread.php?t=839728)

---

### Post by tact on 2008-06-25
> **rustyz said:**
> yes system is installed, the icon shows, and it opens in file browser, with no location bar... 

now what?

could this be a partition thing, i insta;; "guided use entire disk...

see other post of mine for more info...

[http://ubuntuforums.org/showthread.php?t=839728](http://ubuntuforums.org/showthread.php?t=839728)

When you are looking at the window showing whats on the CD - click "View" and check the box for location bar.

---

### Post by tact on 2008-06-25
Can you put the CD in the drive, let the file window open up and then grab a screenshot of it?   Applications>Accessories>Take a screenshot.

While the CD is in the drive and the file window is open - open up a terminal and run this
```
sudo ls -l /media
```

... cut and paste the result into a reply.

Thanks

---

### Post by rustyz on 2008-06-25
location bar says... "/media/cdrom0"

terminal...

lrwxrwxrwx 1 root  999    6 2008-06-24 16:06 cdrom -> cdrom0
dr-xr-xr-x 4 root root 2048 2008-04-28 12:31 cdrom0


heres what we have...

[IMG]http://img111.imageshack.us/img111/8757/screenshotcdrom0filebrofe5.png[/IMG]

thanks for taking the time out to help tact...

rz

---

### Post by tact on 2008-06-26
Ok so in that case here are the steps

- slot the cd into the drive
- wait til its mounted and the file window opens
- confirm its mounted on /media/cdrom0
- open a terminal

This assumes you want to copy the entire CD to the working folder on your HDD - At the command prompt type these commands:[FONT=monospace]
[/FONT]```
sudo cp /media/cdrom0/* ~/working
```Copies all the files on the CD to the directory /home/patrick/working (assumes you are logged in as user "patrick")

```
sudo chown -hR patrick ~/working
```Change ownership of all files/folders recursively in /home/patrick/working to the user "patrick". 
(Assumes "patrick" is your username - change it if not so).

     ```
sudo chgrp -hR patrick ~/working
```Change group of all files/folders recursively in /home/working to user "patrick".
(Assumes "patrick" is your username - change it if not so).
          [FONT=monospace]
[/FONT]```
sudo chmod 0755 -R ~/working
```make all files/folders in ~/working read/write to you, read only to all others.

Now you can go use Places>Home Folder and see the "working" folder.  You will have full ownership and access and can then move files where you want them to be.

---

### Post by rustyz on 2008-06-26
/working' is not a directory
/working': No such file or directory


is what comes up!

rrrrr!

my home/user example files are locked also...

tact, i had a dvd/player/writer in addition to a cd/player/writer that i took out to use on another machine, could that be a problem...

i have not tried Hardy on another PC as of yet...

this is really starting to bug me...

we wont be defeated tho...

thanks

p

---

### Post by tact on 2008-06-26
> **rustyz said:**
> /working' is not a directory
/working': No such file or directory


is what comes up!

rrrrr!

my home/user example files are locked also...

tact, i had a dvd/player/writer in addition to a cd/player/writer that i took out to use on another machine, could that be a problem...

i have not tried Hardy on another PC as of yet...

this is really starting to bug me...

we wont be defeated tho...

thanks

p

Ok, thought the working directory was already created (you didn't forget to type the ~ in commands like "cp /media/cdrom0/* ~/working" did you?) 

So lets create the directory first and then follow the same steps.  Here are the steps

- slot the cd into the drive
- wait til its mounted and the file window opens
- confirm its mounted on /media/cdrom0
- open a terminal

This assumes you want to copy the entire CD to the working folder on your HDD - At the command prompt type these commands:

```
sudo mkdir ~/working
```
Creates a directory in your home folder called "working" that we will use as a temporary folder.

[FONT=monospace] [/FONT]```
sudo cp /media/cdrom0/* ~/working
```Copies all the files on the CD to the directory /home/patrick/working (assumes you are logged in as user "patrick")

```
sudo chown -hR patrick ~/working
```Change ownership of all files/folders recursively in /home/patrick/working to the user "patrick". 
(Assumes "patrick" is your username - change it if not so).

 ```
sudo chgrp -hR patrick ~/working
```Change group of all files/folders recursively in /home/working to user "patrick".
(Assumes "patrick" is your username - change it if not so).
          [FONT=monospace]
[/FONT]```
sudo chmod 0755 -R ~/working
```make all files/folders in ~/working read/write to you, read only to all others.

Now you can go use Places>Home Folder and see the "working" folder. You will have full ownership and access and can then move files where you want them to be.

---

### Post by rustyz on 2008-06-26
tact, will try this tomorow, bed time for me here...

question, is this a permanent solution, or whenever i put a data disk in drive, do i have to go through this again?

thanks again buddy

p

---

### Post by rustyz on 2008-06-27
tact, it worked on the first try...

i made the working home file

then, i put in another CD Data disk, when i draged the file into the working file... 

it was locked again...

---

### Post by tact on 2008-06-30
> **rustyz said:**
> tact, it worked on the first try...

i made the working home file

then, i put in another CD Data disk, when i draged the file into the working file... 

it was locked again...

Hey there...  so you managed to copy all the files from the first CD?  Thats good.

You would need to repeat the process for every CD individually.  Pay special attention to where the CD is mounted.  It may not be mounted on /media/cdrom0 every time.  

So I have added the steps to pay special attention to and they are in bold below....
=======
This assumes you want to copy the entire CD to the working folder on your HDD - At the command prompt type these commands:

```
sudo mkdir ~/working
```Creates a directory in your home folder called "working" that we will use as a temporary folder.

**When the CD is inserted and a folder opens check where the CD is mounted by looking at the location bar (its circled in the attached image).   If its not "/media/cdrom0" then substitute whatever is there wherever you see "/media/cdrom0" in the rest of the instructions.**

```
sudo cp /media/cdrom0/* ~/working
```Copies all the files on the CD to the directory /home/patrick/working (assumes you are logged in as user "patrick")

```
sudo chown -hR patrick ~/working
```Change ownership of all files/folders recursively in /home/patrick/working to the user "patrick". 
(Assumes "patrick" is your username - change it if not so).

 ```
sudo chgrp -hR patrick ~/working
```Change group of all files/folders recursively in /home/working to user "patrick".
(Assumes "patrick" is your username - change it if not so).
          [FONT=monospace]
[/FONT]```
sudo chmod 0755 -R ~/working
```make all files/folders in ~/working read/write to you, read only to all others.

Now you can go use Places>Home Folder and see the "working" folder. You will have full ownership and access and can then move files where you want them to be.

---

### Post by rustyz on 2008-06-30
tact, this will be my last try on this...

i have found that by dividing and archiving up my gutsy personal files into(for me) four tar.gz, burning that onto CD...

when i put back on hardy hard drive, the tar file shows a lock, but i can move them, and delete them wherever i like, without any mods!

how bout that! lol

just have to pay attention to the size of files, and  CD disk space..

way easier them the chown stuff!

thanks for all your time and help!

p

---

### Post by tact on 2008-07-01
Well I think that the problem you had is because you changed username since archiving the files and thus an ownership problem.

I find that when I archive things, copy them, whatever, to any media (CD, external drive, etc)...  I can go so far as to totally format and reinstall my system and copy back -  no problems with ownership of the files etc.   (So long as I use the same username).  :)

In fact I have even installed totally different systems with different flavours of linux or solaris...  and then copied back my home folders with no problems at all.

Not sure what twist you might have unintentionally introduced that gave you all the permissions problems  :)

Glad its all sorted.    

There are truly simple ways to archive and restore stuff under linux.  If you are patient you will ride the learning curve and discover some amazing stuff you can do.

---

### Post by rustyz on 2008-07-01
well, i have always just one user name...

passwords, always change them, and that souldn't be a problem...

and never changed, or fooled with permissions until the new version of Hardly Heron!

i'm on my journey tact, and will check out solaris also...

thanks so much for your time

---

### Post by tact on 2008-07-01
when you did the archiving, or copying, did you use "sudo"?  That would make all the archives/files take ownership as "root" I guess. 

Insert the CD again and find out where its mounted... (example it may be /media/cdrom0)

Then do this...
```
sudo ls -l /media/cdrom0
```

You will get output with several lines such as the one below....
```
-rw-r--r--  1 neilm neilm     7168 2007-12-16 14:48 netstat-ln-smb.after
```
This tells you all the permissions and the owner of the file.

Translated into english the above line says this:  "The file "netstat-ln-smb.after" is owned by "neilm" and is in the group "neilm".  It is a file (as opposed to a directory) and the owner (neilm) has read/write permission, the group "neilm" has read only access, and all others have only read access"

When you do a "ls -l"  or "sudo ls -l" on the location where your CD is mounted (e.g. maybe /media/cdrom0)....  if you see anything other than your username where you see "neilm neilm" then the process that created the archive or copied the files is what changed the ownership.
i.e. if you had "root root" instead of "neilm neilm" or "patrick patrick" then its likely that when you made the copy/archive you did so as "sudo" (root).

Some programs like rsync (or grsync) can be run as root (use sudo) to ensure that all files are processed no matter who is the owner...  and there are switches you can set so that the original ownership, permissions, and group, are preserved.   

If you do not set those switches appropriately and run as root (sudo) then all the files processed end up taking root as owner.

---

### Post by rustyz on 2008-07-02
ran what you asked,and this is what we have...

dr-xr-xr-x 1 root root  4096 2007-08-08 14:16 Desktops
patrick@patrick-desktop:~$

tact some of the CD Data disks wers donloaded from windows XP, a few from Vista, and from Fiesty Fawn and Gutsy...

and i never dowloaded them as root user...

it looks like the process that copied the files is what changed the ownership, al'a Hardly Heron!

now what?

as mentioned, can use the tar method for all the files on my current Gutsy installition, just would like it to work as it should without the fuss...

thanks

rz

---

### Post by tact on 2008-07-03
> **rustyz said:**
> ran what you asked,and this is what we have...

dr-xr-xr-x 1 root root  4096 2007-08-08 14:16 Desktops
patrick@patrick-desktop:~$

tact some of the CD Data disks wers donloaded from windows XP, a few from Vista, and from Fiesty Fawn and Gutsy...

and i never dowloaded them as root user...

it looks like the process that copied the files is what changed the ownership, al'a Hardly Heron!

now what?

as mentioned, can use the tar method for all the files on my current Gutsy installition, just would like it to work as it should without the fuss...

thanks

rz

You cannot change what is on the CD's now.   If it was burned on there with root as the owner then you gotta live with it now.

Perhaps an easier way to manage all this, since you have so many CD's to copy from - is to open up an instance of nautilus as "root" and then you will have a graphical interface to work with.

The process will still be similar -  you will need to (as root - whether GUI or commandline) copy the files from the CD to a temporary rowking directory... then change ownership, group and permissions on all the files.

To do it with a gui press ALT-F2 and in the dialog box type "gksudo nautilus".

Now you will have a GUI filemanager open running as root.  (Mentioned this method many msgs ago).

Using this nautilus window you have all the powers of root so be careful!  

Using it you will be able to copy all files from the CD's no matter who owns them.  Copy to a temporary folder like the one we created with commandline (/home/patrick/working).

Then right click on the folder that is containing everything (this folder may show you as owner, but all the CD files inside it are owned by root - right?)....  select Properties>Permissions (tab)...

Make sure the permissions and owner and group are set as you want for all the contained files...  and click the button "Apply Permissions to enclosed files".

After this all files inside that temp working folder will have the permissions set how you want them.   You can then close the nautilis that has root powers and work normally.

---

### Post by rustyz on 2008-07-04
tact, lets say i want to Re-Burn all my files to CD from my Gutsy OS ( all files on there already)

and how do i burn them "Not as Root..."

how do i make shure the path when burning them is set correctly...

as mentioned before, some were burned on a xp rig, a few from feisty, and from my current gutsy...

i do not see how they were burned as root to begin with?

thanks again!
rz

---

### Post by tact on 2008-07-04
> **rustyz said:**
> tact, lets say i want to Re-Burn all my files to CD from my Gutsy OS ( all files on there already)

and how do i burn them "Not as Root..."

how do i make shure the path when burning them is set correctly...

as mentioned before, some were burned on a xp rig, a few from feisty, and from my current gutsy...

i do not see how they were burned as root to begin with?

thanks again!
rz

Ok so all the files you want to back up are on your gutsy box...  what software are you using to burn files to CD?   Describe your process when you burn a CD on the Gutsy box.

I never bother burning CD's so its been a while.  The tools for burning a CD that come as standard are also different for Gutsy as compared to Hardy.  But let me know what you are using and I will look into it.

For my purposes I use HDD's in external (USB) cases for all my backing up.  Suits me.  Maybe not for everyone.  :)

---

### Post by rustyz on 2008-07-04
all files are on gutsy now...

i use gnomebaker and CR-R's for burn

put cd in drive, open up gnomebaker... click or drag files from home folder... ; music/docs/pic/bookmarks for firefox... ect...

set to burn data...

then start burn...

a simple process...

---

### Post by tact on 2008-07-04
Dead simple process :)   I have no idea why the files end up on the CD owned by "root".  

I guess you could look see if there are any settings related to preserving ownership etc.. other than that - I am at a loss.

Sorry

---

### Post by rustyz on 2008-07-04
what i have discovered tact...

my home user files are set as ROOT!

i just re-installed the out today Hardly 8.04.1 version, and its the same...

my home user, me!... is set as Root!

could it be from the "Guided/Use Entire Disk Format?

i look at my Gutsy Home user Files, and their set to me, not Root!

stumped!

thanks, as always tact...

rz

---

### Post by tact on 2008-07-05
hehehe ok that explains why files end up on back up CD's with root as owner!  

Ok fix that by going to the super-power nautilus:
ALT-F2 and type in the box "gksudo nautilus"

Navigate to /home.   You should then see your home folder /home/patrick

Right click on the folder patrick and then "properties".  Select the permissions tab and change user to patrick, change group to patrick, set permissions so that owner (patrick) and group (patrick) have full folder and file access...  perhaps set others so they have no access.

Alternatively from the commandline:
```
sudo chown -hR patrick:patrick /home/patrick
```
(changes owner and group of all files inside /home/patrick to "patrick")

```
sudo chmod -R 0700 /home/patrick
```
(makes /home/patrick and all files in all directories under it readable/accessible to patrick only)

As to how your home directory got pwned by root at all - hehehe...  I leave that to you to figure.

---

### Post by rustyz on 2008-07-06
from terminal...

`/home/patrick/.gvfs': Permission denied

and when i did from nautilus, no home/me file folder found... just desktop folder?

---

### Post by tact on 2008-07-07
You can ignore the "no permission" error concerning .gvfs  -   that is acceptable.  Its a special folder.

All the rest of the files in your home directory (/home/patrick) should now have you as owner....  correct?

(BTW when you open up nautilus with sudo so you get the super user powers it will open up in /root   ie. in "root's" home directory.   You would have to then navigate to /home and then you will see your folder (/home/patrick) and will be able to use the GUI method I outlined)

---

### Post by rustyz on 2008-07-07
tact> All the rest of the files in your home directory (/home/patrick) should now have you as owner.... correct?not!

it will allow me to change them, when i click on apply permission to permission to enclosed files!

it sits there as changed a few secondes,then reverts back!

now this has happened on all the latest distros on the machine i'm useing!

the last versions of mint, fedora, and pclinux os 2007, and of course, my trusted Gutsy! do not have this problem

i have a thought, i have a spare hard drive with a copy of XP on it, might hook it up on the workhorse computer i have Gutsy on, and install Hardly...

see if this time again my home files are set as Root!

if they do, i say its a problem with the new distros!

and something has been changed, i see a lot of problems with printers, CD/DVD's, file shareing, and other user permissions problems blasted all over the Ubuntu forums...

global/world settings i see a lot, do you know if that could be where this problem might be?

thanks again for taking the time out tact...

or anyone else that may like to hop on in this one!

rz

---

### Post by tact on 2008-07-08
Ok... well.... looks like this runs deeper than my ability to assist..  I hope someone will have a look and assist.

Because this thread has gone on for a number of pages and no one else is stepping in - perhaps you should start a new thread "Root owns my home directory and I cannot change it" ...or something to that effect.  Might attract further help.

Cheers

---

### Post by rustyz on 2008-07-08
wil do just that tack...

another thanks to you!

i have learned quite a bit from this...

rz

---

