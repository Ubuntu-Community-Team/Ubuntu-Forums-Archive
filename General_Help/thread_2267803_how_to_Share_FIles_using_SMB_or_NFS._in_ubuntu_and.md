---
title: "how to Share FIles using SMB or NFS. in ubuntu and windows"
date: 2015-03-04
forum: General Help
---

### Post by offir on 2015-03-04
I have a home computer network with several computers

Some of them have a Windows 7 operating system (2 pc)
Some of them have a Windows XP operating system (1 pc)
Some of them have Ubuntu 14.04 operating system (2 pc)
Some of them have Ubuntu 12.04 operating system (2 pc)
Some of them have Ubuntu 10.04 operating system (3 pc)

All computers running Ubuntu
I installed Samba

All computers have a folder or two
Some also have three or four
Shared Folders

The problem is
When accessing a shared folder
Receive a message that there is no permission

Each computer a different message
Some of them do not have the problem
And easily accessed

Some Receive a message
that there is no Username
Or no password

[COLOR="#0000FF"][SIZE=4]How to adjust the settings
Reach a state
Where each user has access to any folder from any computer
Without messages
Without problems[/SIZE][/COLOR]


[COLOR="#FF0000"][SIZE=4]what is Avahi mDNS daemon
What his role[/SIZE][/COLOR]

---

### Post by bab1 on 2015-03-04
> **offir said:**
> I have a home computer network with several computers

Some of them have a Windows 7 operating system (2 pc)
Some of them have a Windows XP operating system (1 pc)
Some of them have Ubuntu 14.04 operating system (2 pc)
Some of them have Ubuntu 12.04 operating system (2 pc)
Some of them have Ubuntu 10.04 operating system (3 pc)

All computers running Ubuntu
I installed Samba

All computers have a folder or two
Some also have three or four
Shared Folders

The problem is
When accessing a shared folder
Receive a message that there is no permission

Each computer a different message
Some of them do not have the problem
And easily accessed

Some Receive a message
that there is no Username
Or no password

[COLOR="#0000FF"][SIZE=4]How to adjust the settings
Reach a state
Where each user has access to any folder from any computer
Without messages
Without problems[/SIZE][/COLOR]


[COLOR="#FF0000"][SIZE=4]what is Avahi mDNS daemon
What his role[/SIZE][/COLOR]
The Avahi mDNS daemon is the method for resolving dns names for computers using the format of <hostname>.local.  The top level domain (TLD) .local is not needed for either Samba or NFS.

The first question is whether you want to centralize any of the data on one of the Ubuntu hosts?  I have a Ubuntu workstation that also serves as a Samba server for most of the data in my home network.  This makes it easier to manage a set of shares for all the users instead of shares on all the machines.  Do you have a machine that you can leave on most of the time?

The next thing you need to address is user naming across the network.  Samba will require both Linux user names and Samba user names to be successful.  It is best that these be the same from machine to machine.  NFS requires that  all user UID/GIDs be the same across all the machines.

Finally,  if you are sharing files with multiple users you need to group the users by a common user group.  For instance, if you wanted all of the family to have access you might create a user group named ***family***.  If you had friends on the network you could create a group named ***friends***.  If you wanted to combine these to groups you could also add them to a group named ***users***.  Now you can configure the files system to have semi private and public shared files and directories.

How do you want to manage the *users*, *user-groups* and *share locations*?  It's worth noting that ALL SHARES managed by an administrator (root) should be directories outside of any users /home/<user> directory.  The standard location is: */srv*.  I would make the location */srv/share* for the Samba or NFS shares.  Since you are using Windows you will need to use Samba as Windows NFS sharing is problematic.

In short you will find the you need to do these things[LIST]
[*]Manage User Naming
[*]Design and Manage the Shares File System
[*]Manage the Shares Themselves
[*]
[/LIST]

---

### Post by offir on 2015-03-04
> The first question is whether you want to centralize any of the data on one of the Ubuntu hosts?

It's an idea I want to do for a long time
But I can not do it with the current hardware
And new hardware costs a lot of money  that I do not have
That's why I use it like this


> The next thing you need to address is user naming across the network. Samba will require both Linux user names and Samba user names to be successful. It is best that these be the same from machine to machine. NFS requires that all user UID/GIDs be the same across all the machines.

I did not understand

> Samba will require both Linux user names and Samba user names to be successful
What does that mean[COLOR="#0000FF"][SIZE=4] ?[/SIZE][/COLOR]

> It is best that these be the same from machine to machine
I need to create on each computer all the users[SIZE=4][COLOR="#0000FF"] ?[/COLOR][/SIZE]

> NFS requires that all user UID/GIDs be the same across all the machines.
samba is linux and NFS is windows[SIZE=4][COLOR="#0000FF"] ?[/COLOR][/SIZE]

> Finally, if you are sharing files with multiple users you need to group the users by a common user group. For instance, if you wanted all of the family to have access you might create a user group named family. If you had friends on the network you could create a group named friends. If you wanted to combine these to groups you could also add them to a group named users
All computers are in a group called ```
[SIZE=4][COLOR="#0000FF"]home.plex[/COLOR][/SIZE]
```

> Now you can configure the files system to have semi private and public shared files and directories.
I did not understand this

> How do you want to manage the users, user-groups and share locations?
Why do you mean manage them [SIZE=4][COLOR="#0000FF"]?[/COLOR][/SIZE]

>  It's worth noting that ALL SHARES managed by an administrator (root) should be directories outside of any users /home/<user> directory. The standard location is: /srv. I would make the location /srv/share for the Samba or NFS shares
What is the difference between them[COLOR="#0000FF"][SIZE=4] ?[/SIZE][/COLOR]
Does  /srv. Known as a network folder location
Or more adjusted to it [SIZE=4][COLOR="#0000FF"]?[/COLOR][/SIZE]

---

### Post by bab1 on 2015-03-04
> **offir said:**
> ...I did not understand

I can see that now.  I think this is true on many levels and I have thought about your situation for a  long while before answering you.

I think at this time you need to spend some time learning some computer basics before starting out on a project like managing the networking all of these machines.  In all reality; you don't even know what you don't know.  I would take classes in school and read about how computers in general and how computer systems management and networking works.  I am not prepared to go through all the basics at this time.  Also, this certainly is not the forum for that anyway.

If you want to share your own personal files at this time on an Ubuntu machine you can just right click on the directory that you want to share >> go to properties >> click on the "Local Network Share" and follow the instructions there.  This is just like it is in Windows.

---

### Post by offir on 2015-03-05
> If you want to share your own personal files at this time on an Ubuntu machine you can just right click on the directory that you want to share >> go to properties >> click on the "Local Network Share" and follow the instructions there. This is just like it is in Windows. 

That's exactly what I'm doing right now
And there are problems with it

---

### Post by bab1 on 2015-03-05
> **offir said:**
> That's exactly what I'm doing right now
And there are problems with it
What are the problems exactly?  What are the error messages?  What exactly are the steps you are using. Documenting your steps is part of the process.

---

### Post by offir on 2015-03-05
when i want to share a folder 
i right click on the folder
go down to properties
and then to the last tab "local network share"
mark the three Rubrics 
And press "create share" button

in the permissions tab i dont Changes anything




in windows
similar process
Right click on the folder
go down to properties
and then to the "share" tab
press on "share" or "advanced sharing"
add premissions to evryone
then "apply" and "ok"



the problem is that Not always I have access to a shared folder or files
In some cases, the computer prompts
Username and password
or 
i can see the files but cant access them 
If I'm in windows
And I save files to a folder on Linux

I went to physically to the computer with Linux
And I am looking for the file
There is a padlock icon on it
I do not have access to it
Or have access to the file and I can not delete the file

If it Linux or Windows

More screenshots

---

### Post by bab1 on 2015-03-05
> **offir said:**
> when i want to share a folder 
i right click on the folder
go down to properties
and then to the last tab "local network share"
mark the three Rubrics 
And press "create share" button

in the permissions tab i dont Changes anything




in windows
similar process
Right click on the folder
go down to properties
and then to the "share" tab
press on "share" or "advanced sharing"
add premissions to evryone
then "apply" and "ok"



the problem is that Not always I have access to a shared folder or files
In some cases, the computer prompts
Username and password
or 
i can see the files but cant access them 
If I'm in windows
And I save files to a folder on Linux

I went to physically to the computer with Linux
And I am looking for the file
There is a padlock icon on it
I do not have access to it
Or have access to the file and I can not delete the file

If it Linux or Windows

More screenshots

I can't give you any help on the Windows side other than to tell you the Everyone group might not work for Ubuntu users.  In this context the term Everyone does NOT mean everybody.  I usually add the UNIX (Linux) groups and users to the windows machines.

On the Ubuntu (Linux) side you have not given access to any group or or world access (others).  Most likely because the permissions are too restrictive on some parent directory along the path from /home to wherever the directory is that you are attempting to share.

The best thing you can do is create a test folder in your /home/<user> directory that has the default permissions and then share it.  Allow every user access and the ability to create files.  Then test this first by connecting from other Ubunt machines and then from a Windows machine.

I'm not sure that **home.plex** is a valid workgroup domain.  I use single words (e.g. home or plex).  The dot (.) might have unwanted significance).

---

### Post by Mark Phelps on 2015-03-05
> Where each user has access to any folder from any computer

I don't believe this is possible in Windows 7. One Win7 user can NOT access the private folders of other Win7 users.  This is the way Win7 is designed to enforce account security.  You have to create shared folders to have each user address other user files.

---

### Post by offir on 2015-03-06
> I'm not sure that home.plex is a valid workgroup domain. I use single words (e.g. home or plex). The dot (.) might have unwanted significance). 

by Default it says "local" Instead of "plex"
I can not leave it blank - I tried



> 
On the Ubuntu (Linux) side you have not given access to any group or or world access (others). Most likely because the permissions are too restrictive on some parent directory along the path from /home to wherever the directory is that you are attempting to share.

The best thing you can do is create a test folder in your /home/<user> directory that has the default permissions and then share it. Allow every user access and the ability to create files. Then test this first by connecting from other Ubunt machines and then from a Windows machine
Folder in question is located in the path you specify
I tried several times to change the default permissions 
But it is not saved
It returns to default


But I understood what you said

I opened a new folder
where it is saved
Now I will see if it works

---

### Post by bab1 on 2015-03-06
> **offir said:**
> by Default it says "local" Instead of "plex"
I can not leave it blank - I tried

But you can just use a workgroup like this```
mshome 

myworkgroup

thenetwork
```...or some such.
I don't recognize the first graphic.  it doesn't relate to the use of domain for a Samba workgroup. 

> 

Folder in question is located in the path you specify
I tried several times to change the default permissions 
But it is not saved
It returns to default


But I understood what you said

I opened a new folder
where it is saved
Now I will see if it works
Does it work?

---

### Post by offir on 2015-03-06
> But you can just use a workgroup like this


```
mshome 

myworkgroup

thenetwork
```



I did not think about it
I will do it

> ...or some such.
I don't recognize the first graphic. it doesn't relate to the use of domain for a Samba workgroup. 
it is pfsense router

> Does it work? 
It will take me a few days to check it out (Because I should try from any PC)
Right now it seems to work
Files I put in this folder
Still appear with a padlock icon on them
But I have access to them and I can delete them without problems

---

