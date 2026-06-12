---
title: "Problem with folder permissions (I think)"
date: 2013-01-08
forum: General Help
---

### Post by disco.sleeze on 2013-01-08
One of my computers which is running Ubuntu suddenly has a problem where I cannot download or create any new files, or move any files from one folder to another. Due to some of the error messages I have been receiving, I believe the file system's permissions have been messed up somehow.

Is there a quick way to determine if this is the case, and if so how would I go about fixing it?

Thanks in advance for your help guys!

---

### Post by dabl on 2013-01-08
It sounds more like a full filesystem or perhaps a network connectivity issue. Directory permissions don't change themselves, and only root can change them in a way that would make things formerly accessible to the user no longer accessible.

One way to screw up your user's home folder is to run gui packages with "sudo" and then save things or modify things in your user's home folder, which attaches root privileges to them.

That said, with Alt-F2 "gksudo nautilus" you can (carefully!) examine the permissions on files and folders to see if that's the problem.

---

### Post by ScottDeagan on 2013-01-08
> **disco.sleeze said:**
> 
Is there a quick way to determine if this is the case, and if so how would I go about fixing it?


A quick way to determine if it's a directory permissions problem is to:

1. First find out where your browser is trying to save these files when the error occurs. If you're using Firefox, you can see this by clicking on EDIT, then PREFERENCES, and then clicking the GENERAL tab (which should be selected by default anyway). Either the "Save files to" radio button will be selected, or "Always ask me where to save files" will be selected. I'm going to assume your browser is trying to save things to your DOWNLOADS directory (i.e. /home/[your_user_name]/Downloads).

2. Open up a terminal (by pressing CTRL + ALT + T). It should open up in your home directory. In the terminal, type in the following commands (don't forget to press <ENTER> after each line:

```

cd ~
ls -l

```

You should see something similar to this:

```

drwxr-xr-x 2 scott scott 4096 Jan  7 20:43 Desktop
drwxr-xr-x 2 scott scott 4096 Jan  8 12:29 Documents
drwxr-xr-x 2 scott scott 4096 Jan  4 21:15 Downloads
drwxr-xr-x 2 scott scott 4096 Jan  4 15:33 Music
drwxr-xr-x 4 scott scott 4096 Jan  6 01:33 Pictures
drwxr-xr-x 2 scott scott 4096 Jan  4 15:33 Public
drwxr-xr-x 2 scott scott 4096 Jan  4 15:33 Templates
drwxrwxr-x 8 scott scott 4096 Jan  4 20:19 Ubuntu One
drwxr-xr-x 2 scott scott 4096 Jan  4 15:33 Videos

```

The permissions in the above for my Downloads directory are:

```

drwxr-xr-x

```

The first 'd' means it's a directory, the next three characters, the 'rwx' means the owner (which in 'scott' in my case) has read, write and execute permissions. The next three characters, the 'r-x', means the group permissions (in my specific case the group is 'scott') has read and execute permissions. The last three characters, 'r-x', means that everyone else has read and execute permissions.

You can make sure your downloads directory is writable by you by entering the following commands (again, remember to press <ENTER> after each line):

```

cd ~
sudo chown -R [your_user_name]:[your_user_name] ./Downloads
sudo chmod -R 755 ./Downloads

```

Actually, if you don't want to touch the terminal and enter commands, you can open Nautilus, right-click on the Downloads folder, select PROPERTIES, and then select the PERMISSIONS tab. From here, set FOLDER ACCESS to "Create and Delete Files" for the owner (if the owner is set to a user other than yourself, then something is wrong, so use the terminal instructions above).

It's strange that your permissions have changed in the first place (if indeed this is the problem). Another possibility is that your browser is trying to save to a directory other than ~/Downloads (probably more likely). If this is the case, just change the browser's default directory for saving files to DOWNLOADS (by clicking EDIT, PREFERENCES, the GENERAL tab, clicking the SAVE FILES TO radio button and then clicking the BROWSER button and finding/selecting your DOWNLOADS directory).

---

### Post by disco.sleeze on 2013-01-10
Thanks for your help guys, you definitely pointed me in the right direction.

What ultimately worked was rebooting into a recovery terminal and typing the following commands:

chown -R username:username /home/username

Where I replaced "username" with my system's username. That worked like a charm. Don't know how the problem got started in the first place, so that's still confusing, but at least everything has been solved!

---

### Post by efflandt on 2013-01-11
**Keep an eye on it.**  It could be the same problem I had when I would suddenly get errors about read-only filesystem when I would try to cp or download a file.

Although, if you were using sudo to cp files or doing other things as root, it is possible that files ended up with root ownership.

My Linux system is at the far end of a 1 TB drive, and apparently due to some occasional drive errors, the system would spontaneously remount "/" as read-only (everything is in one partition).

After that happened a few times in 12.04, I ran **sudo e2fsck -pc /dev/sda4** from 11.10 on my SSD sdb1, and the problem has not reoccurred yet.  But I did purchase a new drive and eSata/USB drive caddy and intend to copy everything over to the new drive soon.

---

### Post by dabl on 2013-01-12
> **disco.sleeze said:**
> 

What ultimately worked was rebooting into a recovery terminal and typing the following commands:

chown -R username:username /home/username


That is the remediation for this problem:

> One way to screw up your user's home folder is to run gui packages with "sudo" and then save things or modify things in your user's home folder, which attaches root privileges to them.

---

