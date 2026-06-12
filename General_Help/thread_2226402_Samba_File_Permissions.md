---
title: "Samba File Permissions?"
date: 2014-05-27
forum: General Help
---

### Post by chris193 on 2014-05-27
[COLOR=#000000][FONT=Helvetica Neue]Hello, [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]I've got Samba set up and running on a Ubuntu 12.04 server, accessing the files through Windows 7. [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]There are three samba users and when ever one user uploads something, it restricts the permissions of all the other users to 'Read Only'. The only way to get around this so far is to access the file from the user that uploaded it and manually change Properties>Security>Everyone>Full Control. [/FONT][/COLOR]

[FONT=Helvetica Neue][COLOR=#000000]Does anyone know what could be causing it?  [/COLOR][/FONT]

---

### Post by bab1 on 2014-05-27
> **chris193 said:**
> [COLOR=#000000][FONT=Helvetica Neue]Hello, [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]I've got Samba set up and running on a Ubuntu 12.04 server, accessing the files through Windows 7. [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]There are three samba users and when ever one user uploads something, it restricts the permissions of all the other users to 'Read Only'. The only way to get around this so far is to access the file from the user that uploaded it and manually change Properties>Security>Everyone>Full Control. [/FONT][/COLOR]

[FONT=Helvetica Neue][COLOR=#000000]Does anyone know what could be causing it?  [/COLOR][/FONT]
What's causing this is the Linux default file ownership and permissions.  The problem can be solved in at least a couple of ways.

How did you create the share?  Did you use the GUI (usershares) or configure them using the /etc/samba/smb.conf file.

If you are going to have a share that is for multiple users to access and manipulate, then you either make *Everyone* automatically have read-write permissions with usershares or have a common user group for the users that has the proper permissions (smb.conf).  The group should be set to automatically inherit the group ownership  (GID) for all files created in that share.

---

### Post by chris193 on 2014-05-28
Thanks for the reply, I've configured them in the samba.conf file, with an example being:

```
[Locations]
comment = Locations Visited and relevant documentation
path = /files/Locations
browesable = yes
readonly = no
valid users = User1 User2 User3

``` 

I was unsure as to whether it was a problem here as the permissions appear to be set by Windows. So would bundling the Users into a group mean when User1 uploads something to the file 'Locations', User2 and User3 will be able to edit it? As it stands only User1 can edit a file they upload, User2 and User3 would only be able to read it. 

Sorry for any ignorance, I'm a noob with Ubuntu.

---

### Post by bab1 on 2014-05-28
> **chris193 said:**
> Thanks for the reply, I've configured them in the samba.conf file, with an example being:

```
[Locations]
comment = Locations Visited and relevant documentation
path = /files/Locations
browesable = yes
readonly = no
valid users = User1 User2 User3

``` 

I was unsure as to whether it was a problem here as the permissions appear to be set by Windows. 

The Linux OS sets the file permissions and ownership.  The default ownership is owner:ownergroup:others and the default permissions are 0664 for files and 0775 for directories.  This translates to *u=rw g=rw o=r *for files and *u=rwx g=rwx o-r-x*.
> 
So would bundling the Users into a group mean when User1 uploads something to the file 'Locations', User2 and User3 will be able to edit it? As it stands only User1 can edit a file they upload, User2 and User3 would only be able to read it. 

If all the users are added to a common group and that group has ownership and permissions then all those users will have access, regardless of who the user was that created the file.  So if user1 creates a file the ownership might be user1:commongroup and if the permissions for that file were 0664 (u=rw g=rw o=r.  This smeans all users in the group=commongroup have read/write permissions
> 
Sorry for any ignorance, I'm a noob with Ubuntu.
No problem. Everyone starts there.

I prefer to use the user group named *[COLOR="#0000FF"]**users**[/COLOR]*.  This group already exists (gid=100).  One other thing you need to do is create group inheritance for the created files.  Since the default ownership is user1:user1 we need a mechanism that changes that default to user1:users (or some such group name) when a file or a directory is created.  You do that by setting the group ID bit (sgid) on the root directory of the share. In your case it would be: /files/Locations.  This means that every file below that location would inherit the gid of the user group you wanted.

I have a list of steps needed to create a public (open to all) share.  The list includes setting up the users you want in the user group and checking their Samba user status. All of the instructions are professed by a # sign and the commands are to be used from the terminal command line (CLI).  In the instructions I have used the directory /srv/samba/public but you can use whatever directory you want. I do suggest that you think about designing the directory tree to allow for other shares. If I was to have shared just /srv/samba I would not be able to create a private share at /srv/samba/private.  

See the instructions below```

*# Check to see if Linux user has been added to the smbpasswd database*
  sudo pdbedit -L  

*# Add the user <username> to the users group*
  sudo adduser <username> users

*# Check to see if <username> is in the users group*
  getent group users    

*# Create the share root directory*
  sudo mkdir -p /srv/samba/public

*# Set the group inheretance for the directory*
  sudo chown root:users /srv/samba
  sudo chmod 2775 /srv/samba/public

*# Check the directory settings*
  ls -ld /srv/samba
    
*#### To create the share you add this to the bottom of the smb.conf file*
[public]
	comment = Shared Data
	path = /srv/samba/public
        browseable = yes
        guest ok = yes
        writeable = yes
        force group = users
        create mask = 0664
        force directory mode = 0775       
        
*# Restart the smb daemon*
  sudo service smbd restart

```
NOTES:
The above instructions assume there are no files or directories in the newly created directory that you are sharing.  If you have data already in the directory you are sharing you will need to use a different method to set the share ownership and permissions. You need change the ownership with this```
sudo chown -R root:users /srv/samba/public
```...this sets the ownership on all files and directories.  Then you do this to set the sgid bit for group inheritance ```
sudo chmod -R g+s /srv/samba/public
```

If this Ubuntu 13.10, we need to take care of a bug in Nautilus permissions.  Luckily there is a repair already available. See here  for the answer at post#23 and on: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686)
  
 The package is for Trusty (14.04) and is backwards compatible to 13.10, which is the only version that has this problem.

Don't be afraid to ask questions if you don't understand.

---

### Post by chris193 on 2014-05-30
Thanks so much, that was explained beautifully! Problem solved.

---

