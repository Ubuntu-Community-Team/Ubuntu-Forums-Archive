---
title: "Help needed with Samba"
date: 2013-07-07
forum: General Help
---

### Post by Nik2013 on 2013-07-07
I've tried my luck setting up samba to work with the other computers in my home network and based on the tutorials I followed I should have been able to connect to my share. Not happening =/ When I map the network drive I get a "access denied message."   On the other hand the drive/share is still displayed under my computer network location once i've mapped it.

All I'm after right now is a basic setup just to get shared printers and files working, nothing more really. I have security set to user and I've added my Windows 7 account name/password to both the ubuntu server and samba.

Here's my samba config setup

```
[global]
    ; General server settings
    netbios name = ********
    workgroup = WORKGROUP
    security = user
    encrypt passwords = yes
    smb passwd file = /etc/samba/smbpasswd
   

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[share1]
    comment = drive partition
    path = /media/New Volume/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    locking = yes

```

Sorry that the file is a mess, I'm pretty newbish at this. Can anyone give me some help getting everything working please? thanks.

---

### Post by Morbius1 on 2013-07-07
I'm going to go after the most obvious thing and I'll admit I'm jumping to a conclusion based solely on the path of your share:
> path = /media/New Volume/
"New Volume" smells of Windows since that is something they do and it also implies an NTFS formatted partition. Having it mounted to /media also suggests that you don't have an entry in /etc/fstab for this partition but you are mounting it as needed through Nautilus.

** So I would make sure that it it is currently mounted. The output of this command should tell you that:
```
mount
```
** Then I would see who has permissions to access the directory:
```
ls -dl "/media/New Volume"
```
In order for the Win7 user to gain any kind of access to the share he must have access to the folder being shared.

---

### Post by Nik2013 on 2013-07-07
thank you Morbius. As you suspected it is a windows ntfs partition for new volume. Following your advice I found that it was mounted, but didn't have permissions set.

Im curious, whats the best method for changing the permissions? I'm running ubuntu desktop so could use the gui to make the changes, but is that advisable? Would it be better to do it via the command line, and if so what commands would be needed?

---

### Post by Morbius1 on 2013-07-08
There's a couple of ways to solve this specific problem. The easiest way is to force the remote user to become the user that owns the mounted partition:
> 
[share1]     
comment = drive partition     
path = /media/New Volume/     
browseable = yes     
read only = no     
guest ok = no
[COLOR=#0000cd]**    force user = nik2013**[/COLOR]     
create mask = 0755 
    locking = yes
After the remote user supplies the correct credentials to gain access to the share his identity is forced to be nik2013. If nik2013 is the owner of the mounted partition then the remote user has access to the underlying directory.

As far as having it mounted with correct permissions and assuming this is an internal ntfs partition I would argue that there is no current utility that will create the correct entry in /etc/fstab to have it mounted correctly. I use a template:
```
UUID=DA9056C19056A3B3 /media/NewVolume ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
** To find the correct UUID number for your partition:
```
sudo blkid -c /dev/null
```
** Create the new mount point:
```
sudo mkdir /media/NewVolume
```
[COLOR=#0000cd]*I have purposely removed spaces in the name of the mount point - in the long run it saves a lot of aggravation.*[/COLOR] [COLOR=#0000cd]*You will need to change the path in smb.conf to reflect this new mount point.*[/COLOR]

** If the partition is currently mounted unmount it:
```
sudo umount "/media/New Volume"
```
** Then run the following command which checks for syntax errors and if there are none silently mounts the partition to it's new home with it's new permissions:
```
sudo mount -a
```

Note: The template above will make you the owner of the partition and give all local users access. You then use the share definition in smb.conf to act as a gatekeeper on which remote user is allowed access.

---

### Post by Nik2013 on 2013-07-08
SO I finally got my samba shares working and accessible from windows machines, but because I'm a linux noob I haven't been able to get the permissions setup the way I'd like. What I'd like is for the samba users on my home network to have read, write and execute permissions for both files and directories in the shares. Also to have all those permissions for a file created by another samba user other then themselves.

Can anyone advise me in how to go about this? Any advice would be helpful.

---

### Post by ramreddy502 on 2013-07-08
"chmod -R 777 file name or directory name"  this may helpful to you

---

### Post by Nik2013 on 2013-07-08
chmod with that "-R" would make everything within the directory, including sub-directories and files set to the permissions specified, right?

Hey, could I add my samba users to a group then give groups full permissions for stuff within the shares, as opposed to giving such permissions to Other? Would that avoid permission issues for files between different samba users?

---

### Post by bab1 on 2013-07-08
> **Nik2013 said:**
> chmod with that "-R" would make everything within the directory, including sub-directories and files set to the permissions specified, right?

Hey, could I add my samba users to a group then give groups full permissions for stuff within the shares, as opposed to giving such permissions to Other? Would that avoid permission issues for files between different samba users?

You should have a common group.  You also need to set group inheritance on the root directory of the share.  If you don't then any file or directory created will have that users primary group instead of the common group.  The simple way to do this on  an empty directory is ```
sudo chmod 2775 <path/directory>
```
If the directory already has subdirectories and files then I recommend ```
sudo chmod -R u=rwX,g=rwX,o=rX <path/directory>
```...this preserves the correct executable settings for the files in all the directories.

---

### Post by Nik2013 on 2013-07-08
What do you mean by common group? Is group inheritance the group which owns the directory?

> If you don't then any file or directory created will have that users primary group instead of the common group.

If I understand correctly the users primary group is the group that gets created alongside the user account when it's first made right? 

This idea to use groups is starting to look like a hassel. Maybe it would be easier to just give rwX rights to Others then change the samba config to allow only the users I've created to have access to the shares.

---

### Post by bab1 on 2013-07-08
> **Nik2013 said:**
> What do you mean by common group? Is group inheritance the group which owns the directory?

Put all the users that will access the share in one group.  This can be the existing group sambashare.  You have to set inheritance as the primary group is not the common group.
> 
If I understand correctly the users primary group is the group that gets created alongside the user account when it's first made right?

The primary group is the group that is the owner of the file or directory that is created by the user.  If I create a file the user: group is bab:bab.
>  
This idea to use groups is starting to look like a hassel. Maybe it would be easier to just give rwX rights to Others then change the samba config to allow only the users I've created to have access to the shares.
It's really up to you what you do.  This whole thing takes about 2 minutes to do once you know what to do.

---

### Post by dannyboy79 on 2013-07-08
a common group means you either add everyone to a pre-existing group OR you create a smbusers group adn then add each user to that group and then make the group owner of hte folder smbusers.

---

### Post by Nik2013 on 2013-07-08
Ok, let me see if I got this all correct. Say I want to add my existing users to the group "sambashare" what would be the correct command to do that with? After that to change my share directory and it's sub directories I can use this command

```
chmod -R u=rwX,g=rwX,o=rX <path/directory>
```

Which would also change the permissions of the sub directories and files I think, right?

Lastly would there be any disadvantages to giving Other rwX permissions that you could think of? I just want to know which would be the better option.

Thanks for being so patient with a linux newb like myself =P

---

### Post by bab1 on 2013-07-08
> **Nik2013 said:**
> Ok, let me see if I got this all correct. Say I want to add my existing users to the group "sambashare" what would be the correct command to do that with? 
First you need to set the group ownership of the shared directory with ```

sudo chrgp -R <group> <directory>
```
Then you add the users to the group with this
```
sudo gpasswd -a <user> sambashare
```

After that to change my share directory and it's sub directories I can use this command

```
chmod -R u=rwX,g=rwX,o=rX <path/directory>
```
> 
Which would also change the permissions of the sub directories and files I think, right?

Correct.
> 
Lastly would there be any disadvantages to giving Other rwX permissions that you could think of? I just want to know which would be the better option.
Everyone on the system would have access, so why do the above?

---

### Post by Nik2013 on 2013-07-09
I'm trying to change the group ownership of my data partition and all it's sub directories, but when I made the attempt no changes were made. Used this terminal command:-

```
sudo chgrp -R <group> <directory>
```

Just so you know the partition is ntfs (left over from when I was using win 7 on this machine) and is mounted. After that failed I tried seeing if I could change the group of a test folder (In same partition as linux system), which worked fine this time. Since I'm on ubuntu desktop I tried to see if i could change the options via the gui. But as soon as I try to change the directories group ownership with the gui it switches back to it's default owner.

Anyone know whats going on and how I can get around it?

---

### Post by slickymaster on 2013-07-09
> **Nik2013 said:**
> I'm trying to change the group ownership of my data partition and all it's sub directories, but when I made the attempt no changes were made. Used this terminal command:-

```
sudo chgrp -R <group> <directory>
```

Just so you know the partition is ntfs (left over from when I was using win 7 on this machine) and is mounted. After that failed I tried seeing if I could change the group of a test folder (In same partition as linux system), which worked fine this time. Since I'm on ubuntu desktop I tried to see if i could change the options via the gui. But as soon as I try to change the directories group ownership with the gui it switches back to it's default owner.

Anyone know whats going on and how I can get around it?

You're issuing the wrong command. The command to change the ownership is **chown username:usergroup somefile**. In your case, and as you're speaking of directories would be** chown username somedir**.
See: ```
man chown
```

---

### Post by sudodus on 2013-07-09
The file and directory properties (permissions and ownership) do not work the same way with Windows file systems as with linux file systems. For Windows file systems (FAT and NTFS) used in linux, these properties are set when mounted. You can change the default properties with mount options (using the mount command or using mount lines in /etc/fstab). But once mounted, they stay the same (until unmounted and mounted again with other mount options).

So if you have files, that belong to an application, where the properties are important, you should keep them in a linux file system.

---

### Post by Nik2013 on 2013-07-09
But chown is for user ownership, is it not? I'm trying to change the group ownership of the directories here.

---

### Post by sudodus on 2013-07-09
You can change both user and group ownership with chown, and you can change group ownership with chgrp - provided the file system lets you do it.

---

### Post by Nik2013 on 2013-07-09
Ah, thanks for clearing up why this is happening sudodus. Can you tell me what would probably be the easiest method to implement the changes I want to make?

---

### Post by slickymaster on 2013-07-09
> **Nik2013 said:**
> But chown is for user ownership, is it not? I'm trying to change the group ownership of the directories here.

Yes, you're right. But you can change both user and group ownership with chown, or you can just change group ownership with chgrp.

**Edit:** sudodus already beat me to it. :D

But in any case I address you to [sudodus post]("http://ubuntuforums.org/showthread.php?t=2161033&p=12723884&viewfull=1#post12723884") as he raises a very important point.

---

### Post by sudodus on 2013-07-09
Please describe how you want to use the files (and why you want to change the group ownership)! I will leave for a while, so let us welcome other people to help with the details ... slickymaster is certainly qualified to help you.

---

### Post by Nik2013 on 2013-07-09
Well the directory is my main samba share. What I'm trying to do here is give the users on my home network the same permissions as the user who created the file in the share. So what I was planning on doing was adding the users to the sambashare group and then changing the group ownership of directory I'm using for the share. After that was going to use:-

```
chmod -R u=rwX,g=rwX,o=rX <path/directory>
```

to change the permissions of everything in the share.

Though based on what you told me about windows system files not working in linux system files, will samba be able to applying the the permissions I set in it's config file to newly created files/directories if the share directory is an ntfs partition?

---

### Post by Morbius1 on 2013-07-09
Including this topic you now have 3 threads on exactly the same topic:
[http://ubuntuforums.org/showthread.php?t=2160644&p=12721936#post12721936](http://ubuntuforums.org/showthread.php?t=2160644&p=12721936#post12721936)
[http://ubuntuforums.org/showthread.php?t=2160789&p=12722490#post12722490](http://ubuntuforums.org/showthread.php?t=2160789&p=12722490#post12722490)

Why you didn't respond to bab1 in your other topic is unknown. Why you didn't respond to me in the other one is unknown. 

For the benefit of others in this thread his share looked like this in the first of these posts:
> [share1]     
comment = drive partition     
path = /media/New Volume/     
browseable = yes     
read only = no     
guest ok = no
create mask = 0755 
    locking = yes                      
I suggested this change to his share definition since I don't think this ntfs partition is being automounted in fstab:
> [share1]
comment = drive partition
path = /media/New Volume/
browseable = yes
read only = no
guest ok = no
[COLOR=#0000cd]**force user = nik2013**[/COLOR]
create mask = 0755
locking = yes 
[COLOR=#0000cd]* Where nik2013 is the name of the user that owns the mounted ntfs partition.*[/COLOR]

I also suggested a permanent mount in fstab for that ntfs partition that would have eliminated the need  for the force user. If restricting access to a specific group is required it can either be done by adding gid=sambashare and changing umask to 002 to my suggested entry in fstab or adding another option to the share definition:
> [share1]
comment = drive partition
path = /media/New Volume/
browseable = yes
read only = no
guest ok = no
[COLOR=#0000cd]**force user = nik2013**[/COLOR]
[COLOR=#0000cd]**valid users = @sambashare**[/COLOR]
create mask = 0755
locking = yes 

Either way an ntfs partition is immutable so by definition if a given user has permissions to access it he has the exact same permissions as any other user who has access to it.

[COLOR=#0000cd][I]**EDIT**: Another thing which may be complicating things is I never thought to ask if he created any shares from Nautilus. If he did it may conflict with the one he created in smb.conf. The output of this command would have told him that:
```
net usershare info --long
```[/I][/COLOR]

---

### Post by Irihapeti on 2013-07-09
Threads merged.

Please do not start multiple threads on the same topic. It causes confusion and dilutes community effort.

---

### Post by Nik2013 on 2013-07-09
> **Irihapeti said:**
> Threads merged.

Please do not start multiple threads on the same topic. It causes confusion and dilutes community effort.

I was at fault for making multiple threads on this. Sorry for the trouble admin.

---

### Post by Nik2013 on 2013-07-09
Hi Morbius1, I followed the advice in your 2 posts and have created a permanent mount in fstab. The directory is now auto mounting at start up and Users, groups and Other have permissions set to rwX. It shouldn't be necessary for force user now, correct? Also out of curiosity is it the entry in fstab that's defining the permissions of the shared directory in this case?

Say in the future I want to expand the size of my shares by adding new physical drive (in this case probably an external drive), what would be the easiest/best way to set it up? Formatting it to a linux file system, then creating a permanent mount point in fstab maybe?

thanks for all the help by the way.

---

### Post by Morbius1 on 2013-07-09
> It shouldn't be necessary for force user now, correct?
I'm going to have to guess again because I gave you 2 options for fstab and you didn't specify which one you are using:
```
UUID=DA9056C19056A3B3 /media/NewVolume ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
UUID=DA9056C19056A3B3 /media/NewVolume ntfs defaults,nls=utf8,umask=002,uid=1000,gid=sambashare,windows_names 0 0
```
Either way you no longer need "force user" but in the second option the samba client user must be a member of the sambashare group to gain write access. 
> Also out of curiosity is it the entry in fstab that's defining the permissions of the shared directory in this case?
Yes, but keep in mind that you set ownership and permissions for mounted partitions in fstab only if the partition is formatted to NTFS or FAT32. For Linux filesystems ( i.e., ext4 ) you set ownership and permissions after it's mounted with a chown and chmod like everyone has been posting in this topic.

---

