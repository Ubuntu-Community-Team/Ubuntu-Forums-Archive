---
title: "Global Permissions"
date: 2018-09-07
forum: General Help
---

### Post by bobgrey1997 on 2018-09-07
I am rather new to this operating system (just a few days).
Right now, I am attempting to create a new folder and extract files into it.

Problem is; my system seems to think that I; the only account on the system, in turn an Administrator, does not have permissions to do so...

I have found some posts online for adding permissions to existing directories, but only one directory at a time, and it will not allow me to make new ones to give myself permissions to.
My question is; is there a command that gives me full access to read, write, change, and run anything anywhere at one time? A single command that does that, rather than having to go folder-by-folder, file-by-file, across the entire system...

---

### Post by bobgrey1997 on 2018-09-07
Okay, this is really becoming an issue now...
I can't download any files from the web, I can't install anything via Terminal, I can't save any files from any program, and I can't open many programs...

---

### Post by DuckHook on 2018-09-07
> **bobgrey1997 said:**
> &#8230;is there a command that gives me full access to read, write, change, and run anything anywhere at one time? A single command that does that, rather than having to go folder-by-folder, file-by-file, across the entire system...
The short answer is "Yes". The responsible answer is: "Yes, but it's an absolutely terrible idea to do so.

Changing permissions is admittedly somewhat convoluted and obscure. But it's that way for good reason. New users, and in particular those coming from Windows, tend to bring their bad Windows habits with them. Especially if they were Windows power users, those habits are almost guaranteed to get them into deep trouble. I'm sorry if this sounds like a lecture&#8212;I certainly don't intend it as such&#8212;but there's no delicate way to say it.

Your post illustrates a number of Windows behaviours and assumptions that are problematic:

[LIST=1]
[*]Linux is designed as a multiuser system with much higher native security than Windows. Therefore, even though you may be the only user on your system, *you are not the administrator.* No one is, until they briefly elevate themselves into that role using *sudo*, and then, only for one command at a time. This is one of the measures that makes Linux more secure than Windows.
[*]Linux files have ownerships&#8212;the result of aforesaid multiuser design. Generally speaking, it will not allow one user access to files owned by another user. In a typical default install, there are at least two users: you and the root user. To prevent the possibility of foul play, neither should be permitted to fiddle with the files of the other unless special commands are used.
[*]Linux files also have permissions that are lacking in a typical Windows install&#8212;again the result of aforesaid multiuser capacity. This is to allow for fine-grained control so that users can share *some* files with other users while keeping sensitive files visible only to themselves.
[/LIST]
The way you phrased your question leads me to conclude that you wish to operate as root permanently. This so strongly discouraged and such poor computing practice that I am unwilling to show how it can be done. Instead, please provide some more context so that we can advise you on an appropriate way to do things that won't hose your entire system.

[LIST=1]
[*]Are you trying to make a new folder in your /home directory or some system directory?
[*]If a system directory, why?
[*]Are you the only user on your system?
[*]Why do you need to change permissions across multiple directories and files?
[/LIST]
The added info, context and background will allow us to better advise you.

---

### Post by DuckHook on 2018-09-07
> **bobgrey1997 said:**
> Okay, this is really becoming an issue now...
I can't download any files from the web, I can't install anything via Terminal, I can't save any files from any program, and I can't open many programs...
…likely the result of you tampering with permissions and unintentionally locking yourself out of certain directories.

Please answer the questions in my previous post.

---

### Post by bobgrey1997 on 2018-09-08
Alright, I will start with 4, as that basically covers everything else.
[COLOR=#000000]Why do I need to change permissions across multiple directories and files?[/COLOR]
I tend to edit and create new files almost constantly.
For example; when I was on Windows, I spend the majority of my time breaking games apart to learn how they work, then rebuilding them into something different.
Right now, I am trying to learn a new image-editor.

At this very moment, I need access to ~/.local/share/fonts, which does not exist, so I need to create it, which I cannot do because of permissions.
I need access to Downloads so I can, well, download.
I need access to Pictures so I can save my edited images.
I need access to Documents so I can create, edit, save, and remove any number of millions of files I mess with for any number of hundreds of programs that I like to tinker around with.
I need access to ~/.steam so that I can create copies of such files to move them to Documents to edit them.
Note, all of those directories that I mentioned, I will also need access to every sub-directory and file inside them.
If I go about this one command at a time, I will be sitting here, quite literally, for the next 3 or 4 days typing command-after-command.

As for question 3:
I am going to go ahead and say yes, I am the only user on my system.
Sure, the "root" is considered a "user", but it is only a program, not an actual user. There is not another person, or any other kind of living thing, that is ever interacting with my system.
So, why do I want access to all of these files? Because those files are on MY hard drive.
Also, I don't have a tendency to go about messing with system files as they are. The most I will ever do is add a new file to it, in the form of updates, installs, etc. (I don't usually have an interest messing with the system itself), or I will copy a file and paste it somewhere else to take a look inside, if I am that curious.
That said, many programs will have files inside the "system directories" that I may be interested in taking a look at.
Problem is, I can't even install such programs as it sees those directories as read-only!

And, no, I have not done anything with permissions. I tried to set permissions to that fonts directory, only to get an error saying that such directory does not exist. Another time I tried to set permissions to Downloads, only to get an error that I don't have permission!

---

### Post by ajgreeny on 2018-09-08
Your post #5 suggests that many of the files/folders in your home folder are not owned by you which will cause many problems of the sort you have mentioned and is definitely not normal.

To check this properly please show us the output of terminal command ```
ls -la
```

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by bobgrey1997 on 2018-09-08
Here is the output:
```

spencer@spencer-GA-78LMT-USB3-6-0:~/.local/share$ ls -la
total 116
drwx------ 25 spencer spencer  4096 Sep  7 17:01  .
drwx------  3 spencer spencer  4096 Sep  4 20:50  ..
drwxr-xr-x  8 spencer spencer  4096 Sep  5 03:31 'American Truck Simulator'
drwxr-xr-x  3 spencer spencer  4096 Sep  4 20:54  app-info
drwx------  2 spencer spencer  4096 Sep  4 22:17  applications
drwxr-xr-x  2 spencer spencer  4096 Sep  4 22:17  desktop-directories
drwx------  7 spencer spencer  4096 Sep  4 20:52  evolution
drwxr-xr-x  2 spencer spencer  4096 Sep  4 20:52  gnome-settings-daemon
drwx------  2 spencer spencer  4096 Sep  7 18:11  gnome-shell
drwxr-xr-x  2 spencer spencer  4096 Sep  4 21:01  gnome-software
drwx------  2 spencer spencer  4096 Sep  7 16:24  gvfs-metadata
drwxrwxr-x  2 spencer spencer  4096 Sep  4 20:52  ibus-table
drwxrwxr-x  2 spencer spencer  4096 Sep  4 20:52  icc
drwx------  3 spencer spencer  4096 Sep  4 22:12  icons
drwx------  2 spencer spencer  4096 Sep  7 16:19  keyrings
drwxrwxr-x 17 spencer spencer  4096 Sep  6 01:15  krita
drwxr-xr-x  6 spencer spencer  4096 Sep  4 22:17  mime
drwxrwxr-x  3 spencer spencer  4096 Sep  4 20:53  nautilus
drwxr-xr-x  3 spencer spencer  4096 Sep  7 17:01 'Paradox Interactive'
drwxrwxr-x  2 spencer spencer  4096 Sep  6 21:22  RecentDocuments
-rw-------  1 spencer spencer 11958 Sep  6 21:48  recently-used.xbel
-rw-rw-r--  1 spencer spencer   100 Sep  4 20:52  session_migration-ubuntu
drwx------  2 spencer spencer  4096 Sep  4 20:52  sounds
drwx------ 27 spencer spencer  4096 Sep  7 16:55  Steam
drwxrwxr-x  3 spencer spencer  4096 Sep  5 01:25  vulkan
drwx------  2 spencer spencer  4096 Sep  7 16:14  xorg
drwx------  3 spencer spencer  4096 Sep  6 20:53  zeitgeist

```
By the way, the code tag works the exact same here as it does on the forum I spend most my time on (SCS Software Forums), so that's nice! Thank you for pointing out a tutorial though. The more of those, the better, especially for someone like me (switching to an operating system only to find that it is all code-bases, while having no idea how to code in this way!)

Also, I has no idea what any of that output is, but I see
```

drwxrwxr-x  3 spencer spencer  4096 Sep  5 01:25  vulkan

```
and it's got me curious.

---

### Post by ajgreeny on 2018-09-08
Strange!
You are obviously user **spencer** and everything in your home is owned by you.
However in your previous post you say
> At this very moment, I need access to ~/.local/share/fonts, which does not exist, so I need to create it, which I cannot do because of permissions.
I need access to Downloads so I can, well, download.
I need access to Pictures so I can save my edited images.
I need access to Documents so I can create, edit, save, and remove any number of millions of files I mess with for any number of hundreds of programs that I like to tinker around with.
I need access to ~/.steam so that I can create copies of such files to move them to Documents to edit them.
Note, all of those directories that I mentioned, I will also need access to every sub-directory and file inside them.
If I go about this one command at a time, I will be sitting here, quite literally, for the next 3 or 4 days typing command-after-command. and you only showed us the listing of your ~/.local/share folder which is not what I wanted to see, though it shows that you do not have a .local/share/fonts folder (neither do I; it's not a default folder in anyone's home unless created). You can easily create it with command ```
mkdir .local/share/fonts
``` but normally when running commands make sure that the working directory you're in is your user and the prompt shows just**spencer@spencer:~$** and we can then check that you do have the folders Documents, Pictures etc etc that you say you have no access to, possibly because your current working directory when you tried was not your home folder but something else, as you used when running that **ls -la** command for me.

---

### Post by bobgrey1997 on 2018-09-08
So, I attempt to make the directory...
```

spencer@spencer-GA-78LMT-USB3-6-0:~/.local/share$ cd
spencer@spencer-GA-78LMT-USB3-6-0:~$ mkdir .local/share/fonts
mkdir: cannot create directory &#8216;.local/share/fonts&#8217;: Read-only file system
spencer@spencer-GA-78LMT-USB3-6-0:~$

```

I noticed the "GA-78LMT-USB3-6-0", what is that?

I also assume "[COLOR=#000000]and you only showed us the listing of your ~/.local/share folder which is not what I wanted to see, though it shows that you do not have a .local/share/fonts folder (neither do I; it's not a default folder in anyone's home unless created). You can easily create it with command[/COLOR]" you referring to that fact that I ran the command from "spencer@spencer-GA-78LMT-USB3-6-0:~/.local/share$"?
I just noticed I was in there (from my yesterday attempts to add the directory from within the directory, after not being able to add it from home), so here is the command again from, what I assume to be, home:
```

spencer@spencer-GA-78LMT-USB3-6-0:~$ ls -la
total 4564
drwxr-xr-x 21 spencer spencer    4096 Sep  7 16:49 .
drwxr-xr-x  3 root    root       4096 Sep  4 20:37 ..
-rw-------  1 spencer spencer     370 Sep  4 22:36 .bash_history
-rw-r--r--  1 spencer spencer     220 Sep  4 20:37 .bash_logout
-rw-r--r--  1 spencer spencer    3771 Sep  4 20:37 .bashrc
drwx------ 20 spencer spencer    4096 Sep  6 20:53 .cache
drwx------ 21 spencer spencer    4096 Sep  7 16:28 .config
drwxr-xr-x  3 spencer spencer    4096 Sep  6 20:53 Desktop
drwxr-xr-x  2 spencer spencer    4096 Sep  4 21:20 Documents
drwxr-xr-x  2 spencer spencer    4096 Sep  6 22:18 Downloads
-rw-r--r--  1 spencer spencer    8980 Sep  4 20:37 examples.desktop
drwx------  2 spencer spencer    4096 Sep  7 16:18 .gconf
drwx------  3 spencer spencer    4096 Sep  4 22:12 .gnome
drwx------  3 spencer spencer    4096 Sep  4 21:29 .gnupg
-rw-------  1 spencer spencer    1560 Sep  7 16:14 .ICEauthority
-rw-rw-r--  1 spencer spencer 1537911 Sep  7 16:41 .krita-8170-document_0-autosave.kra
-rw-rw-r--  1 spencer spencer 1481056 Sep  7 16:41 .krita-8170-document_1-autosave.kra
-rw-rw-r--  1 spencer spencer 1525589 Sep  7 16:41 .krita-8170-document_2-autosave.kra
drwx------  3 spencer spencer    4096 Sep  4 20:50 .local
drwx------  5 spencer spencer    4096 Sep  4 20:56 .mozilla
drwxr-xr-x  2 spencer spencer    4096 Sep  4 20:52 Music
drwxr-xr-x  2 spencer spencer    4096 Sep  7 16:24 Pictures
drwx------  3 spencer spencer    4096 Sep  4 21:17 .pki
-rw-r--r--  1 spencer spencer     807 Sep  4 20:37 .profile
drwxr-xr-x  2 spencer spencer    4096 Sep  4 20:52 Public
-rw-r--r--  1 spencer spencer    3122 Mar 28  2017 Release.key
drwxr-xr-x  5 spencer spencer    4096 Sep  7 17:05 snap
drwx------  2 spencer spencer    4096 Sep  4 21:29 .ssh
drwxrwxr-x  2 spencer spencer    4096 Sep  7 16:54 .steam
lrwxrwxrwx  1 spencer spencer      32 Sep  7 16:49 .steampath -> /home/spencer/.steam/sdk32/steam
lrwxrwxrwx  1 spencer spencer      30 Sep  7 16:49 .steampid -> /home/spencer/.steam/steam.pid
-rw-r--r--  1 spencer spencer       0 Sep  4 21:39 .sudo_as_admin_successful
drwxr-xr-x  2 spencer spencer    4096 Sep  4 20:52 Templates
drwxr-xr-x  2 spencer spencer    4096 Sep  4 20:52 Videos

```

---

### Post by ajgreeny on 2018-09-08
Your home seems to be a read only filesystem which it should not be, and we need to try to figure out why that is.
I also need to see the fstab file of the installed system, not that of the live system you may have to use to view it.  You will be able to see it from the file manager of the live system, but looking in the appropriate volume or partition which will show in the left hand pane.

As for that "GA-78LMT-USB3-6-0", it is just part of the hostname of your computer which it was given at installation and which I missed in my last post where I said incorrectly the prompt would show spencer@spencer, ie user@hostname; command ```
cat /etc/hostname
``` will tell us what the hostname is.

---

### Post by bobgrey1997 on 2018-09-08
Where to find this "fstab file"?

---

### Post by ajgreeny on 2018-09-08
In the left hand pane of the file manager of your live system you will see all the partitions of your hard disk listed but I do not know how nautilus shows them, but if you search you should find a file in one of them /etc/fstab, which is just a text file and should look similar to this 
```
# /etc/fstab: static file system information.
	#
        # Use 'blkid' to print the universally unique identifier for a
     	# device; this may be used with UUID= as a more robust way to name devices
     	# that works even if disks are added and removed. See fstab(5).
     	#
     	# <file system> <mount point>   <type>  <options>       <dump>  <pass>
     	# / was on /dev/sda2 during installation
     	UUID=53c1deb3-fab3-4577-8ec8-2f3c1f0f5e8a /               ext4    errors=remount-ro 0       1
    	# /boot/efi was on /dev/sda1 during installation
    	UUID=B6E8-249B  /boot/efi       vfat    umask=0077      0       1
    	# /home was on /dev/sda3 during installation
    	UUID=0cd847e0-572c-459d-8429-154cac24f4fb /home           ext4    defaults        0       2
    	/swapfile                                 none            swap    sw              0       0
```
Copy the one you find and paste it back here in code tags please.
See my signature below for a **How-to** of using code tags.

---

### Post by The Cog on 2018-09-08
> Where to find this "fstab file"?
The command "cat /etc/fstab" will print it.

The clue to your problem is the line: "mkdir: cannot create directory ‘.local/share/fonts’: Read-only file system"
The whole disk that your home directory lives on is read-only. That is not normal - there's a fairly basic problem somewhere.

Edit: Beaten to it. Distracted by the TV. Doh!

---

### Post by bobgrey1997 on 2018-09-08
I don't have partitions, so the left pane doesn't show anything for that, so I have no clue what "live system" means.

I did find it, though, by clicking "Other Locations", Computer, then etc.
Here is the fstab file, litsted on the top of the text editor as "fstab [Read-Only]" (go figure)
(Not that I plan to edit it, just noticed that everything seems to be Read-Only right now...)
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f1ed1060-1522-4264-aa50-c121b5944cfc /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0

```

---

### Post by ajgreeny on 2018-09-08
Sorry, yes The Cog is correct.

I am currently trying to help in two threads, one of which needs a live system to do anything as it will not boot; yours boots fine, however, so show us the ```
cat /etc/fstab
``` output.

EDIT:

Just seen your post, added while I was adding mine.
Your fstab seems OK, so we need to find the reason for your filesystem being read only, and there unfortunately I am unable to help so will have to leave this to others to answer further.

---

### Post by bobgrey1997 on 2018-09-08
I think I am getting used to this Terminal thing (I NEVER used Command Prompt in Windows other than to attempt to fix it's dumb issues)
Output
```

spencer@spencer-GA-78LMT-USB3-6-0:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f1ed1060-1522-4264-aa50-c121b5944cfc /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0

```
Wait a second...
Did I just open that file directly with the Terminal!?

---

### Post by The Cog on 2018-09-08
It may be worth rebooting to see if the error was a one-off. If not then I guess you will need to boot from the stick/dvd you installed from and run a filesystem check (program name is fsck and is similar to chkdsk on windows) to try to fix any errors on the disk. Come back and ask for more details if that seems necessary.

> Did I just open that file directly with the Terminal!? 
The command "cat" just reads and types the file to the console. You can't edit it with cat. But yes it did open it in order to type it.

---

### Post by bobgrey1997 on 2018-09-08
Well, I can now download things, extract my fonts, and install them (which resulted in a new directory being made). Now to try to save an image (yep, all of this has been keeping my from finishing my image, which I needed a new font for, which I needed to download)...
When I booted my system, it gave me some error (I can't remember what now) and told me to "run fsck manually" and a directory that had the error "dev/sda1". I had no idea what to do when I first seen this error, but I figured out (after typing commands to see if it was it, only to get no response) that it was "fsck dev/sda1". I then figured out the "reboot" command. After that, here we are!
Thank you all for the help. I think this particular situation is solved, but I will be sure to come back in the future as the chances of me either breaking it or not knowing how to do it are very high!

---

### Post by The Cog on 2018-09-08
Well, that's good news.
Needing to do an fsck is unusual and usually caused by bad power-downs, same as chkdisk. You were unlucky.

There is a Thread Tools pull-down at the top of the page where you can mark the thread solved.

---

### Post by bobgrey1997 on 2018-09-08
Ah, alright.
Yeah, I do have a bad hard drive (that I definitely cannot afford to replace any time soon), so I think I can expect similar issues to occur frequently.

---

### Post by ajgreeny on 2018-09-09
If you're sure your hard disk is failing, and that may indeed be so if this problem keeps happening, make sure you have good backups that you know you can restore.

Very happy to see this is now solved!

---

### Post by HermanAB on 2018-09-09
Hmm, if you have a known bad HDD, then you are wasting your time.  Linux doesn't take kindly to file system errors.

It would be worth your while to get a second hand disk at your local computer junk shop.

Typically, in any big city, you can get free or almost free computers at the city garbage dump.

---

