---
title: "Folder permission for multiple users"
date: 2015-02-12
forum: General Help
---

### Post by gundybandy on 2015-02-12
I live in a living community and I have setup a local machine (Ubuntu Server 14.04) with the purpose to serve media files over Plex to my devices.

Now my friends would like to also use Plex because they like it very much and want to contribute new media files.

This means that they have to get access to my Media folder. The problem is that all new created folders containing new media stuff still have the specific user as owner so that another user can't complete the TV shows etc. of another user.

What I did:

[LIST=1]
[*]Created 4 new users accounts (one for each community member)
[*]Created a new group "mediamember"
[*]Added all new user accounts to the group "mediamember" inlcuding the user plex and my account
[*]Changed the groupowner of my Media folder to the new group "mediamember". I did it recursive so all the subfolders would get the new groupowner.
[/LIST]


And this scenario does not work (more detailed):

[B]One of the new users wants to add a new TV Show:
[/B]
1) One of the new users logs in via remote desktop (xubuntu-desktop over x2go)

2) He opens a folder on his desktop which is a symbolic link to my "Media" folder

3) There he is going to the "TV Shows" folder

4) There he creates a new folder with the name "Name of a tv show"

5) He goes into the new folder and creates a new folder called "Season 1"

6) He uploads *.mkv files which does NOT cover all episodes of "Season 1"

7) Other user wants to complete the episodes but he can't create new episodes because he has no rights.

Like I allready mentioned I think it has something to do with the problem that every new created folder and file still have the user specific group and rights.

I would like to have all new created folders and files with the group "mediammeber" as owner so that everybody has the rights to contribute and organise the media files.

Google says it might have to do something with umask. However I did not understand the concept of umask.

Can anybody help?

Thank you very much!

---

### Post by SeijiSensei on 2015-02-12
Permission masks in *nix use "octal" (base-eight) numbers.  The umask is the difference between the largest octal digit, seven, and the mask.  Usually the default umask is 022, which results in directory permissions of 755.  To grant group-writable permissions, give the users a umask of 002 => 775.

The umask is set in each user's $HOME/.profile file.  To change the default for new user accounts edit the file /etc/skel/.profile.  That directory contains the "skeleton" of a user's home directory.

---

### Post by bab1 on 2015-02-12
> **gundybandy said:**
> I live in a living community and I have setup a local machine (Ubuntu Server 14.04) with the purpose to serve media files over Plex to my devices.

Now my friends would like to also use Plex because they like it very much and want to contribute new media files.

This means that they have to get access to my Media folder. The problem is that all new created folders containing new media stuff still have the specific user as owner so that another user can't complete the TV shows etc. of another user.

What I did:

[LIST=1]
[*]Created 4 new users accounts (one for each community member)
[*]Created a new group "mediamember"
[*]Added all new user accounts to the group "mediamember" inlcuding the user plex and my account
[*]Changed the groupowner of my Media folder to the new group "mediamember". I did it recursive so all the subfolders would get the new groupowner.
[/LIST]


And this scenario does not work (more detailed):

[B]One of the new users wants to add a new TV Show:
[/B]
1) One of the new users logs in via remote desktop (xubuntu-desktop over x2go)

2) He opens a folder on his desktop which is a symbolic link to my "Media" folder

3) There he is going to the "TV Shows" folder

4) There he creates a new folder with the name "Name of a tv show"

5) He goes into the new folder and creates a new folder called "Season 1"

6) He uploads *.mkv files which does NOT cover all episodes of "Season 1"

7) Other user wants to complete the episodes but he can't create new episodes because he has no rights.

Like I allready mentioned I think it has something to do with the problem that every new created folder and file still have the user specific group and rights.

I would like to have all new created folders and files with the group "mediammeber" as owner so that everybody has the rights to contribute and organise the media files.

Google says it might have to do something with umask. However I did not understand the concept of umask.

Can anybody help?

Thank you very much!

The default umask for all users on Ubuntu Server is aeady 002.  This mean any file created will have read/write permissions for the user:group and read only for all others.  The default for all directories created is read/write/eXecute for the user:group and read/eXecute for all others.  The only exception to this is the root account which has a umask of 022 which is more restrictive.

To achive group inheritance of directory you need to use SGID on the root folder.  To do this you need to set the SGID bit on the "mediafolder.  I use this command to do this```
sudo chmod g+s <mediadirectory>
```... where <mediadirectory> is your actual directory.

Since you hae already set the mediamember group as the group owner of that directory all files and directories *created *in that directory or any of the subdirectories will now have the mediamember group as the group owner.  The permissions will be fine.  There is no need to mess with the umask for any user on this version of Ubuntu Server.

The only fly in the oinment will be when you *copy * existing files or directories to the mediadirectory.  I have found that not all the time are the desired group ownership set.  You will hae to check to see if it works for your group members in this instance.

[COLOR=#0000FF]**Edit:** You can check your umask setting easily.  From the terminal use this command[/COLOR]```
umask
```

---

