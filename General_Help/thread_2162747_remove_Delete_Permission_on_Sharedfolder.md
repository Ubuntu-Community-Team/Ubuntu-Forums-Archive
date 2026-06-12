---
title: "remove Delete Permission on Sharedfolder"
date: 2013-07-15
forum: General Help
---

### Post by farazhamza on 2013-07-15
I m realy a new bee

i have installed Ubuntu desktop server and also install samba. its all working Fine.

I want to share a folder and want to remove Delete permission of guests. but i failed to do so.

is there any method so that i can share a folder in which Guest can paste and edit files but cannot delet those Files.

I dont want to use any username and group. just want to handle Guests.

---

### Post by theDaveTheRave on 2013-07-16
farazhamza,

as far as I understand, editing and deleting a file is 'the same thing'.

You could edit the file to have zero contents (delete all text, insert a whit box on a photo), both hence require the 'write' atribute.

Your only sensible option in that case is to backup any modifications made.

David

---

### Post by Warren Hill on 2013-07-16
Take a look here

[http://ubuntuforums.org/showthread.php?t=2138476&p=12616640#post12616640](http://ubuntuforums.org/showthread.php?t=2138476&p=12616640#post12616640)

You can prevent other users from deleting a file but since they have write access they can still edit so while you can stop them deleting the file they can still delete all its contents.

---

### Post by farazhamza on 2013-07-16
REaly Glad to see you REplies and Thanks a lot for your Sugestion. due to poor english i m not able to clear my point. Well let me explain Again.

I have shared a Folder on  sdb1/share your Files

All people on the Network can access the Folder "share your Files" and i have set Write permission on it. So all Client computers can paste files on this folder without any group access. i have permitt access as Guest. All can open the folder and paste files inside it as a guest.

Now i want that. every one can Paste Files in it. but nobody can delete files inside this folder.

Before ubuntu i was using Window server 2003 in it i can do that. but i m new in linux. so have no idea how to do that.
all people was able to paste there data in that folder but wasnot able to delete that files after uploading to that folder.

---

### Post by theDaveTheRave on 2013-07-17
farahzhamza,

Ah that is a little different.

my suggestion would be to perform 2 things.

In your shared folder (lets call it 'public'), have a sub folder for each user with write permission to that folder only.

A final folder on the shared folder called 'shared' (or similar)

Then in the users folder you mount these particular folders into thier own home folder.

You want to do this using the ```
mount
``` and ```
ln
``` commands.

You need to check the manual for ```
ln
``` as to whether you need soft or hard links, but there are controls to ensure that the permissions of the original folder are reflected in the link locations.

You are then going to require a fairly complex script to auto add the links and files into a new users home directory (I say compley, once you've got your command correct on the terminal you should be good for the script also).

David

---

### Post by farazhamza on 2013-07-18
I have almost 500 clients So i canot create too many users accounts so thats why i want to change permission of Guest account

So there is not any possiblity to remove Delete permission of Guest Account?

---

### Post by Morbius1 on 2013-07-18
I think you are using the wrong protcol. You might consider FTP or even a LAN based http server with upload capability.

For example, it's been a while since I've used vsftp but there is a parameter in it's config file that by default prevents the client from deleting uploaded files:

This parameter allows guest user write access when set to YES:
> **anon_upload_enable** 
If set to YES, anonymous users will be permitted to upload files under certain conditions. For this to work, the option **write_enable**  must be activated, and the anonymous ftp user must have write permission on  desired upload locations. This setting is also required for virtual  users to upload; by default, virtual users are treated with anonymous (i.e. maximally  restricted) privilege. 
Default: NO 

And this one prevents them from deleting anything when set to NO ( which is the default ):
> **anon_other_write_enable** 
If set to YES, anonymous users will be permitted to perform  write operations other than upload and create directory, such as  deletion and renaming. This is generally not recommended but included for completeness. 
Default: NO 

I would explore an FTP solution of some kind to meet your requirements.

---

