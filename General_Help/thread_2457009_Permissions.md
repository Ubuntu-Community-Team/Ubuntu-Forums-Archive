---
title: "Permissions"
date: 2021-01-24
forum: General Help
---

### Post by Disabled20241022 on 2021-01-24
Hi,

I have a external harddrive with multiple partitions and is bootable and i can access it however when i boot the drive (live install) i cannot excess the partitions and was wondering what are the best permissions for me to use keeping in mind both safety and that it supports my current username and the user from the bootable live install (linux)?

What do i put into the terminal without formatting the drive?
(username is john)


> Edit: i was just on the bootable linux image (live setup) and i tried to change it using: [QUOTE]sudo chmod 777 /media/pop_os/"Externe schijf" -R and then i created a file on it, now being back at my normal harddrive i can read the created file but it shows a lock on it and the permissions are different then the rest of the drive.[/QUOTE]



Second part,
How do i do the same thing with my default harddrive with multiple partitions, like what permissions are best used here, i think that i should only give access to my own username and have it denied access for others. Or do you disagree?

And what do i type in the terminal without messing things up?

---

### Post by ajgreeny on 2021-01-24
The live system will need to mount the partition, easiest usually by clicking it in the left hand pane of the file manager, but to carry out any actions on the files in those partitions will, I think require root permissions.
You can use sudo in live systems with no password required, just hit Enter, but you can not make any permanent changes in a live system because any such changes are lost when it's rebooted.

What does "default harddrive with multiple partitions" mean? Does that drive have an OS on it or just data?
If there is an OS do not mess with permissions unless you know exactly what you're doing or you may kill the OS itself.

---

### Post by Disabled20241022 on 2021-01-24
I mean i have a harddrive in my laptop that have 3 partitions on it. but i have changed permissions over time without understanding them, i was wondering what are the right permissions for me and what are the terminal lines for these?

Back to the first question, it is mounted but unable to do anything, permissions need to change but into what and how.

To make some thing clearer these are the values when i right click a partition, i'm comparing 4 different places. I don't understand which once is correct for what i want. Read allot about it but still...

**New usb        **
- _Owner_: ME > Create and delete files.
- _Group_: ayudha > Access files
- _Others >_ Access files.    


**External HD**
same
Create + delete
Create + delete

**Overige**
same
access files
no list, no create,/del, access

**Fresh OS**
same
access files
access files

Overige is my partition with data, it is on the same harddrive as the Fresh OS (newly installed)
Then i have a USB newly bought and a old external drive whereby the settings where changed.
As you can see everything is differnet and i am unsure what to do next.

---

### Post by yancek on 2021-01-24
All Linux operating systems are designed as multi-user systems.  That means that as a default, the ordinary user has limited access, primarily to the data in the /home/user directory and sub-directory.  You can change either the owner or the permissions on external or internal partitions with data on them.  Do not change permissions on system files of your OS unless you completely understand what the commands you use will do.  The command to change owner is chown, to change group chgrp and permissions with chmod.  Countless sites available online explain the various parameters.

If you want to write to the partition "Overige" you need to give your user write permissions and/or change owner to the user you want to give access to.

---

### Post by Disabled20241022 on 2021-01-24
There is only one owner, me. I'm not trying to change the linux permissions of where it is installed.
 But i really don't know what to do, i already tried allot of things and nothing seems to work as i want it hence this forum post.

---

### Post by yancek on 2021-01-24
> There is only one owner, me.  

No, there are always at least 2 owners on any Linux OS, the user name you use and root.  The vast majority of directories and files are owned by root.  The directories in your /home/user directory sould be owned by you, from your initial post you indicate the user is named john.  To find out what the owner:group and permissions are on any secondary data partitions on the same hard drive or other hard drives, you can run the following command as these partitions are available for access under /media/username:

```
ls -l /media/john
```

>  But  i really don't know what to do, i already tried allot of things and  nothing seems to work as i want it hence this forum post. 


Sorry but that is really vague.  If you are trying to accomplish something specific like granting permissions, you need to use specific commands and you need to keep notes of what you are doing so that if what you do fails, you can undo it.  You also need to post the specific commands you use and the resulting output if it fails.  Details are important so if you get instructions from a specific source like a web site, post a link to it.  Specifics are needed so simply saying nothing seems to work doesn't help anyone to help you.

---

### Post by ajgreeny on 2021-01-24
There is nothing that is going to be more useful to you that understanding Linux file permissions, so I suggest you research this subject in more detail before changing permissions of files and folders; if you do this incorrectly, particularly for system files and folders (anything not in your home), you could quite easily completely ruin the OS and have to start again with a re-installation.

Here's a good starting place for you to read through.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by oldfred on 2021-01-24
With an installed system, the default user is 1000.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ id [/COLOR]
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),121(lpadmin),131(lxd),132(sambashar
e)

[/FONT]
```

But when you boot with live installer, user is 999, so you do not automatically have full access to an installed systems files on other partitions.

---

### Post by grahammechanical on 2021-01-24
When I use the file manager to view the permissions of a file that I have created and stored in the Documents folder, this is what I see

Owner: Me
Access: Read and Write
Group: graham
Access: Read-only
Others: 
Access: Read-only

This is logical. If I decide to create another user on my system they can access and read that file but they cannot delete it. Neither can they write to it (edit it). I can change the permissions of Group and Others to allow Read and Write, or to have no permission at all (none).

If I check the permissions of the Documents folder, this is what I see

Owner: Me
Access: Create and delete files
Group: graham
Access: Access files
Others: Access files

This also is logical. Another user on the system should not be allowed to delete, or edit files, or put files in my documents folder. Unless, of course, I change the permissions.

If I look at the permissions of the /etc folder, this is what I see

Owner: root
Access: Create and delete files
Group: root
Access: Access files
Others
Access files

Do you begin to see the logic? Or, to put it another way, there is method in the madness. I, as a standard user cannot change these permissions and neither can anyone else. To edit system files I have to gain permission by running a command or utility using sudo. For example, I can view the contents of the sources.list file in /etc/apt/ but to edit it I need to run a text editor using sudo. Or I can use Software & Updates to add and remove repositories but I will be asked to authenticate the action.

Another example is Software Updater. That utility has permission to update system files but when it comes to upgrading and removing  Linux kernels we get asked to authenticate. If we update/upgrade through the terminal then the use of sudo takes care of it.

Regards

---

### Post by Disabled20241022 on 2021-02-01
> **yancek said:**
> No, there are always at least 2 owners on any Linux OS, the user name you use and root.  The vast majority of directories and files are owned by root.  The directories in your /home/user directory sould be owned by you, from your initial post you indicate the user is named john.  To find out what the owner:group and permissions are on any secondary data partitions on the same hard drive or other hard drives, you can run the following command as these partitions are available for access under /media/username:

```
ls -l /media/john
```




Sorry but that is really vague.  If you are trying to accomplish something specific like granting permissions, you need to use specific commands and you need to keep notes of what you are doing so that if what you do fails, you can undo it.  You also need to post the specific commands you use and the resulting output if it fails.  Details are important so if you get instructions from a specific source like a web site, post a link to it.  Specifics are needed so simply saying nothing seems to work doesn't help anyone to help you.

Ok got it, i will do that next time. Right now i have installed linux again to undo what i did but the other partitions and external harddrive/usb i have done nothing to so they are still messed up.


When i do what you asked me to do i get: ```
total 0

```

> **ajgreeny said:**
> There is nothing that is going to be more useful to you that understanding Linux file permissions, so I suggest you research this subject in more detail before changing permissions of files and folders; if you do this incorrectly, particularly for system files and folders (anything not in your home), you could quite easily completely ruin the OS and have to start again with a re-installation.

Here's a good starting place for you to read through.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thanks for the warning. I think i never did anything to the filesystem itself, just some files in home perhaps but mostly it is on a external harddrive, usb and other partitions with files on them. These are the problem and not the filesystem.
Anyway i already installed linux again just in case.

> **oldfred said:**
> With an installed system, the default user is 1000.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ id [/COLOR]
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),121(lpadmin),131(lxd),132(sambashar
e)

[/FONT]
```

But when you boot with live installer, user is 999, so you do not automatically have full access to an installed systems files on other partitions.

Correct.

```
uid=1000(john) gid=1000(john) groups=1000(john),27(sudo)


```

> **grahammechanical said:**
> When I use the file manager to view the permissions of a file that I have created and stored in the Documents folder, this is what I see

Owner: Me
Access: Read and Write
Group: graham
Access: Read-only
Others: 
Access: Read-only

This is logical. If I decide to create another user on my system they can access and read that file but they cannot delete it. Neither can they write to it (edit it). I can change the permissions of Group and Others to allow Read and Write, or to have no permission at all (none).

If I check the permissions of the Documents folder, this is what I see

Owner: Me
Access: Create and delete files
Group: graham
Access: Access files
Others: Access files

This also is logical. Another user on the system should not be allowed to delete, or edit files, or put files in my documents folder. Unless, of course, I change the permissions.

If I look at the permissions of the /etc folder, this is what I see

Owner: root
Access: Create and delete files
Group: root
Access: Access files
Others
Access files

Do you begin to see the logic? Or, to put it another way, there is method in the madness. I, as a standard user cannot change these permissions and neither can anyone else. To edit system files I have to gain permission by running a command or utility using sudo. For example, I can view the contents of the sources.list file in /etc/apt/ but to edit it I need to run a text editor using sudo. Or I can use Software & Updates to add and remove repositories but I will be asked to authenticate the action.

Another example is Software Updater. That utility has permission to update system files but when it comes to upgrading and removing  Linux kernels we get asked to authenticate. If we update/upgrade through the terminal then the use of sudo takes care of it.

Regards

Thank you for explaing.

If a other person steals my laptop and removes the harddrive then plugs it in his computer can he see my files from his system with these permissions you have (that i also have now for that part) in the documents folder?

For /etc folders i have the same settins.

But the real problem is with the other things, i have other partitions, other external harddrives and usb's and these are messed up.
These are the once i am trying to fix but am unable to, well i can change them with sudo commands but every time with a reboot there seems to be a different issue thats why i wanted to know what the default settings for those (partitions, ex. drives and usb's) things where and also what the best options are regarding privacy with usb drives. And also to make it more complicated, i need to open these drives in a live envouronment when i reboot i boot up my external drives and so i can install linux etc. but when i am booted in a live install i am unable to access these drives and unable to change them because i'm then a different user. (popOs/ubuntu based)

---

### Post by Holger_Gehrke on 2021-02-01
> **ayudha said:**
> 
If a other person steals my laptop and removes the harddrive then plugs it in his computer can he see my files from his system with these permissions you have (that i also have now for that part) in the documents folder?


In the inode for the file (an internal data structure that exist for each file) the owner (and group) are stored as the numerical id only. So if someone were to remove your HD and plug it into another machine running Ubuntu (or some other Linux distribution) the files would get shown as owned by whoever has id 1000 on that machine. Generally speaking physical access to the machine / the drives trumps all security measures except for full disc encryption.

Holger

---

### Post by Disabled20241022 on 2021-12-24
I am still having these issues. Can somebody explain to me with terminal code how to change the permissions on a thumbdrive to read, write etc free 4 all?

---

### Post by ajgreeny on 2021-12-24
[LIST=1]
[*]Find the mountpoint of the thumb drive.  
[*]You can most easily do this by mounting it, ie plugging it in and seeing the full pathway in the location bar of the file manager.
[*]Copy this mountpoint.
[*]Run terminal command ***sudo chown -R username:username pasted-mountpoint***
[/LIST]
Take great care with the command and make sure you get the mountpoint correct by copying things and pasting where needed, and of course change **username:username** to your own user.

This will make the thumb drive read/write for you as user, but not for any other users logged in to the same machine. It may be read/write for other users on another machine as they will probably have the same user gid1000 as you if they are the first user on that computer.

---

### Post by HermanAB on 2021-12-25
Some clarifications may be needed for a confused new user:
The textual user and group names are a mere convenience.  The actual user and group names are numerical and the mapping between the text and numerics may not be the same on all systems.  These days on Ubuntu, the first user account that is created has the number 1000 (it used to be 500).  So if you move a disk from one system to another, expect to have some issues.

---

