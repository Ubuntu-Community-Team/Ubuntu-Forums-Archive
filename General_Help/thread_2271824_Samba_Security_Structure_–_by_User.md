---
title: "Samba Security Structure – by User"
date: 2015-04-01
forum: General Help
---

### Post by freakky on 2015-04-01
I'm having trouble determining the security structure for my Samba server and client.   
 
 I granted the appropriate permissions for each shared folder on the server and mirrored the permissions in smb.conf.  The client computer automounts the shared folders thanks to the additional line I inserted into /etc/fstab.
 
 However, my understanding of fstab is it can only provide the username and password for 1 samba user, and does this during the client machine's boot.  So all users on the client machine have to use the same samba credentials.  Thus, regardless of user on the client, the same folder shortcuts would appear on the left program bar in Gnome.
 
 I would like the samba credentials provided to the server from the client to vary with the user that is logging into the client, i.e. if Tom logs into the client, I only want to mount the shared folders to which Tom has access, or the folders his groups have access.  Then if Tom logs off of the client machine and Harry logs in, I only want to mount the shared folders to which Harry has access.  Also, I need the folders to automount.
 
 Can this be accomplished by having fstab understand which user is logging in?  Or am I thinking about this completely wrong and there's a better solution?
 
 Thanks in advance for any help.

---

### Post by bab1 on 2015-04-01
> **freakky said:**
> I'm having trouble determining the security structure for my Samba server and client.   
 
 I granted the appropriate permissions for each shared folder on the server and mirrored the permissions in smb.conf.  The client computer automounts the shared folders thanks to the additional line I inserted into /etc/fstab.

This implies that you are locally mounting (on the server) an ext4 partition.  Is this so?

Samba provides authentication (who are you?).  The authorization (you can do this) is always via the Linux file (directory) permissions.
> 
 
However, my understanding of fstab is it can only provide the username and password for 1 samba user, and does this during the client machine's boot.  
this is only true if you are mounting a NTFS formatted partition.  This is due to the NTFS formatting having no POSIX style permissions.  The ntfs-3g driver and mount.ntfs provide that functionality when the partition is mounted. > 
So all users on the client machine have to use the same samba credentials.  Thus, regardless of user on the client, the same folder shortcuts would appear on the left program bar in Gnome.
As it should be with Linux.  Multiple users should be accommodated by the user-group permissions not the user permissions. > 
 
I would like the samba credentials provided to the server from the client to vary with the user that is logging into the client, i.e. if Tom logs into the client, I only want to mount the shared folders to which Tom has access, or the folders his groups have access.  Then if Tom logs off of the client machine and Harry logs in, I only want to mount the shared folders to which Harry has access.  Also, I need the folders to automount.

Can this be accomplished by having fstab understand which user is logging in?  Or am I thinking about this completely wrong and there's a better solution?
 
 Thanks in advance for any help.
The /etc/fstab file is the configuration file used for *_mounting partitions at boot up time_*.

In the end you if you want to share files amongst a group of users via a Linux host (using Samba), the simplest method is to add the users to a common group and manage the file and directory permissions via that group.

Describe what you want to share and to whom and we can then advise you on how to accomplish that.

---

### Post by freakky on 2015-04-02
BAB1, thank you for the reply.  To provide an example of what I want to share and to whom:
 
Users:  tom, ****, harry, sally (all users access Samba shared folders from one of two client machines; each user does not have his/her own client machine)
Groups:  tandd (tom and ****), tdhs (tom, ****, harry, sally)
Samba Folder1:  0750, user=tom, group=tandd
Samba Folder2: 0775, group=tandd
Samba Folder3: 0770, group=tdhs
 
If harry logs into a client machine, I want the client machine to automatically mount the shared folders to which harry has any permissions.  In this case, Samba Folder2 and Folder3 only.  Samba Folder1 should not appear as a shortcut on the Unity desktop since harry does not have any permissions.  Then if tom logs into a client machine, then all 3 shared folders should mount since tom has permissions in each folder.
 
Please let me know if this is not clear.
Thanks again.

---

### Post by bab1 on 2015-04-02
> **freakky said:**
> BAB1, thank you for the reply.  To provide an example of what I want to share and to whom:
 
Users:  tom, ****, harry, sally (all users access Samba shared folders from one of two client machines; each user does not have his/her own client machine)
Groups:  tandd (tom and ****), tdhs (tom, ****, harry, sally)
Samba Folder1:  0750, user=tom, group=tandd
Samba Folder2: 0775, group=tandd
Samba Folder3: 0770, group=tdhs

Referring back to what I said before about managing data authorization via groups; you have 2 groups.  One of those groups has 2 folders with differing permission settings.  **[COLOR="#0000FF"]Why is that?[/COLOR]**  
> 
If harry logs into a client machine, I want the client machine to automatically mount the shared folders to which harry has any permissions.  In this case, Samba Folder2 and Folder3 only.  Samba Folder1 should not appear as a shortcut on the Unity desktop since harry does not have any permissions.  Then if tom logs into a client machine, then all 3 shared folders should mount since tom has permissions in each folder.

When you mount remote shares via fstab, they are mounted to the client machine regardless of who is logged in.  This *_mount occurs before the user has even logged in_*.  

You can mount the shares using a shell script, but it adds layers of complexity.  If you have set the permissions correctly it really doesn't matter if the user can see a share, they will be denied access if you don't want them to see anything but the share name.

[COLOR="#0000FF"][B]What is file system type (ext or ntfs or...) of the partition you are using? 
[/B][/COLOR]

---

### Post by LewisTM on 2015-04-02
I recommend you try the GNOME/gvfs method of automatically connecting to Samba shares at logon - using Gigolo
See [http://raphaelhertzog.com/2012/10/30/auto-mounting-windows-shares-in-gnome-with-gigolo-and-gvfs-fuse/](http://raphaelhertzog.com/2012/10/30/auto-mounting-windows-shares-in-gnome-with-gigolo-and-gvfs-fuse/)
It should work for any user without any need to play with fstab entries.
Good luck!

---

### Post by freakky on 2015-04-06
Sorry for the delay in replying - the long holiday weekend threw everything off.

BAB1,
Thanks again for the reply.  In regards to the file system, it is ext4.  The samba shares are on a computer running Ubuntu server 14.04.  The 2 clients run Ubuntu desktop 14.04.  An ipad, iphone, and android phone will be added once Samba is fully implemented on the Ubuntu clients.
In regards to a group having differing permissions on 2 folders, that's how I would like to setup my Samba shares for the house.  In Folder1, I want the group to have r-x permission.  In Folder2, I want the group to have rwx permission.

---

### Post by freakky on 2015-04-06
LewisTM,
Thanks for pointing me to Gigolo and GNOME/gvfs.  That works  well.  I'm surprised I never found it in my searches prior to you  mentioning it.  I have been a member of Ubuntu Forums since 2009, but  rarely post questions because I can almost always find answers to my  questions through Internet searches.  I'm surprised I didn't discover  Gigolo during my research.
Thanks again

---

### Post by bab1 on 2015-04-06
> **freakky said:**
> Sorry for the delay in replying - the long holiday weekend threw everything off.

BAB1,
Thanks again for the reply.  In regards to the file system, it is ext4.  The samba shares are on a computer running Ubuntu server 14.04.  The 2 clients run Ubuntu desktop 14.04.  An ipad, iphone, and android phone will be added once Samba is fully implemented on the Ubuntu clients.
In regards to a group having differing permissions on 2 folders, that's how I would like to setup my Samba shares for the house.  In Folder1, I want the group to have r-x permission.  In Folder2, I want the group to have rwx permission.

Since the Samba serve is using an EXT file system you can just set the ownership and permissions for the share(s) using the standard Linux tools (i.e. chmod and chown).  I would also NOT nest these shares inside one another.  For example I would create this file system```
root directory of all shares
/srv/samba/

# Folder one
/srv/samba/folder1/

# Folder two
/srv/samba/folder2/

# Folder three
/srv/samba/folder3/
```

Then I would set the owner (root) and group-owner (tandd or tdhs) like so```

sudo chown root:tandd folder1

sudo chown root:tandd folder2

sudo chown root:tdhs folder3
```...at this point the user tom has access to all the folders (via group membership).  The users harry and sally have access to only folder3 via their group membership.

Last you set the folder permissions and set the sgid bit for group ownership inheritance of all files and folders created under the three folders.  Here is where I don't really understand what you are trying to do.  The folder1 permissions you have set (i.e. 750) for this folder do not make much sense.  Why are you restricting the group to read an eXecute on the folder?  Why does the user need read, write, and eXecute permissions and group membership?

The sgid bit is the key to setting group inheritance which is definitely needed when you have multiple users that need create (write) permissions on a shared folder.  The way to set the sgid bit is like this ```

sudo chmod g=+s /path_to/folder1
```...or on a new folder you can just set the permissions and the sgid bit at the same time like this```
sudo chmod 2770 /path_to/folder1
``` 

I need more info to help you specifically on the permissions you should use.  You specifications (750 vs 770) are ambiguous.  Bear in mind that the permissions are only for that folder and not what is created inside the folder.  The umask setting sets the permissions.  The default umask is 0002.  This provides permissions on files created  of 664 and folders (directories) of 775 for all users except the root user.

Once you work out the permissions on the directories you are going to share you can, we can setup the Samba shares with very simple parameters.

FYI:  Gigolo uses the same GNOME gvfs libraries that are already installed on all Ubuntu Unity or GNOME desktops.  Gigolo is valuable for desktops that do not normally use GNOME components (e.g. KDE, LXDE, etc).

---

### Post by freakky on 2015-04-11
BAB1,
Thanks for the reply.  I'm relatively familiar in setting permissions with the standard linux tools and have already finished this step on the Samba server.  Thanks for the offer to help configure Samba, but I have already completed that step as well.
My biggest issue was resolved with Gigolo.  After a lot of research and trial & error, my file server is close.

---

