---
title: "gigolo configuration for all users"
date: 2013-10-04
forum: General Help
---

### Post by whatch on 2013-10-04
I have dual boot computers; windows7 and ubuntu 12.04, that are joined to our active directory domain via likewise.  

I would like to configure gigolo so that for any user that logs into their domain account, that some of the information (everything but username and password) is already filled in, so that users can easily get to the windows file server.  I don't want users to have to fill in this information every time they sit at a different computer.  

Is there any way to do this?  

Thanks

---

### Post by bab1 on 2013-10-04
> **whatch said:**
> I have dual boot computers; windows7 and ubuntu 12.04, that are joined to our active directory domain via likewise.  

I would like to configure gigolo so that for any user that logs into their domain account, that some of the information (everything but username and password) is already filled in, so that users can easily get to the windows file server.  I don't want users to have to fill in this information every time they sit at a different computer.  

Is there any way to do this?  

Thanks
Not easily.

How many shares are involved here?  From a Linux client post the output of this ```
smbtree
```

I use scripts to mount shares that are defined in the /etc/fstab file.  These scripts are initiated via .desktop launchers.  If you only have a few shares then I recommend that you think about using this method.  The user doesn't need to know anything other than to click on the icon to mount the share.

---

### Post by whatch on 2013-10-05
The Windows file server has one main share called "share".  Inside that share are two folders: "staff", and "students".  The samba path I have used to browse to get to the staff path, for example, is smb://fs3/share/staff/username

I do not know how to create the script. Can you point me in the right direction? Thanks.

---

### Post by bab1 on 2013-10-06
> **whatch said:**
> The Windows file server has one main share called "share".  Inside that share are two folders: "staff", and "students".  The samba path I have used to browse to get to the staff path, for example, is smb://fs3/share/staff/username

I do not know how to create the script. Can you point me in the right direction? Thanks.

You loose some security functionality by having only one share for both staff and students.

It would be better for you to create at least two *separate *file system sections ../staff and ../students) and two shares (i.e. //SERVER/staff and //SERVER/students).  Even then I don't know enough about your network to be confident that this really appropriate for you.  So let me find out some more about what you are trying to accomplish.

The first thing I do when I design this type of multiple user environment is determine where I need file system separation for security reasons and physical hardware needs (each user has a dedicated computer or not). Then I create the file system to accommodate the user security needs.  Next I create the shares and  lastly I create the scripts to access the shares if needed.  

Will each staff member have their own computer?  Will the students each have a dedicated computer too?  Will  there be a public share (i.e. //SERVER/public) that students and staff can use to share files.  Or maybe two public type shares.  One for the staff and one for the students.  To carry this further; do you wish to separate teachers for the support staff?

---

### Post by whatch on 2013-10-07
The computers are in a lab, and are mainly used by students.  We want them to be dual-boot, with Win7 so that staff can use them if necessary.  But they will mainly be used by students, and the teacher prefers Ubuntu.  Teacher/staff computers are Win7, and they do have their own computers.  Students do not.  We do have a public folder that is used as a dropbox by students, but I hope to move to Google Drive for this purpose.  

I hear you about having separate shares for students and staff, but it is too late to set it up like that now.  

We have discovered that once the Ubuntu system is joined to the domain, if browsing to the share via Samba, that users can only get to their own folder.  

I am going to make a script and get it on all user's desktops.  This might work.

---

### Post by bab1 on 2013-10-07
I know this looks like I'm being picky here.  I'm not, it's just that your response is not very clear to me.  See my comments in red below.

> **whatch said:**
> The computers are in a lab, and are mainly used by students. [COLOR="#FF0000"]<-- Do all the students use Windows?  No students use Ubuntu?[/COLOR]  
We want them to be dual-boot, with Win7 so that staff can use them if necessary. [COLOR="#FF0000"]<-- Isn't this more multi user login?  Are we talking Windows only in this case?[/COLOR]
But they will mainly be used by students, and the teacher prefers Ubuntu.[COLOR="#FF0000"]<-- Only one teacher wants to use Ubuntu ?  [/COLOR]  
Teacher/staff computers are Win7, and they do have their own computers.  Students do not.[COLOR="#FF0000"]<-- Other teachers ???[/COLOR]  

We do have a public folder that is used as a dropbox by students, but I hope to move to Google Drive for this purpose.[COLOR="#FF0000"]<-- Nothing to d with your shares[/COLOR]  

I hear you about having separate shares for students and staff, but it is too late to set it up like that now. [COLOR="#FF0000"]I'll leave that to you.  I feel that the shares can be reconfigured and the user would still see the same thing.[/COLOR]

We have discovered that once the Ubuntu system is joined to the domain, if browsing to the share via Samba, that users can only get to their own folder. [COLOR="#FF0000"]??? This means what? What folder?  Samba is only being used as a client for Ubuntu.  All the shares are configured and located on the Windows Server; correct?  Are you having authentication problems?[/COLOR]

I am going to make a script and get it on all user's desktops.  This might work. [COLOR="#FF0000"]<-- It appears that the Ubuntu machine is only for one user.  I can help you with that machine's desktop script.[/COLOR]

To sum this up: Most of this is Windows AD specific and I know next to nothing about Windows clients in an AD environment.  The Ubuntu machine(s) can have scripts that are dedicated to mounting a share into the Ubuntu file system and the share will show up on the desktop of the user.

Where are the Ubuntu users home directories located?  The scripts rely on share login information stored in a hidden file in the users home directory.  Are these local user accounts or domain user accounts held in AD?

---

### Post by whatch on 2013-10-08
After the Ubuntu system is joined to the Windows Domain, and a domain user logs in, a home directory is created for that user inside of /home/likewise.  We don't want users saving files to that directory.  We want them saving to the Windows network share.  

If I was to create a script that mounts the share on the Windows server, what would it look like.  The path is 192.168.1.254/share

Inside this share are folders staff and students.

---

### Post by bab1 on 2013-10-08
> **whatch said:**
> After the Ubuntu system is joined to the Windows Domain, and a domain user logs in, a home directory is created for that user inside of /home/likewise.  We don't want users saving files to that directory.  We want them saving to the Windows network share.  

If I was to create a script that mounts the share on the Windows server, what would it look like.  The path is 192.168.1.254/share

Inside this share are folders staff and students.
There are some support settings that need to be created before you can use the script.  Where you see this <user>, you must substitute the actual user name.

1.  Create a .smbcred file. Using a text editor, add this to the file```
<user>
<user password>
```...this should be located in the /home/likewise/<user> directory.It should be owned by <user>:<user> and the permissisons shouuld be 0600.  This setting means only the user (and root) can read and write to the file.
Create a mount point at the /media ```
sudo mkdir /media/<user>
```... now you need to create a text file in that directory.  This file is used by the mount script to see if the share is mounted or not.  I usually call it readme.smb.  In it you can name the user and what share you are mounting.  It's really for the administrator later on when no one remember what and why it is there.  It works like this:  If the file is visible then the share has NOT been mounted.  If the share has been mounted you won't find the readme.smb file anywhere.  The script uses this action to provide the if/else logic.  You will see this in the script below.
 
2.  Add these mount directives at the bottom of /etc/fstab
```

# Mount <users> share at /media/<user>
192.168.1.254/share /media/<user> cifs user,noauto,username=<user>,credentials=/home/<user>.smbcred,uid=<user id#>,gid=<users group id#>,nobrl 0 0

```  
To test this you can use this command```

sudo mount -a

``` This should mount the share.  If this is successful then you can make create the script.

3.  The script I use checks to see that the file server is running by pinging it.  If this is successful.  Then it checks the state of the share mount (mounted/unmounted) and does the appropriate thing.
```

SERVER=192.168.1.2

ping -c 1 "$SERVER" > /dev/null

if [ "$?" -eq 0 ] ; then
    if [ -f /media/<user>/readme.smb ]; then
#     We need to>> mount<< the share (via fstab) and inform the user
      mount /media/<user>
      zenity --info \
                --text="<user's> data is now available"
    else
#    We need to >>unmount<< the share and inform the user
     umount /media/<user>

      zenity --info \
                --text="<user's> data is now un-available"
    fi
else
# Failed to find the host via pinging IP address
  zenity --error \
                --text="The file server is down.  Please inform the Administrator"
fi

```
I have commented the script (#=comments).  The Zenity stuff brings up dialog boxes so the user sees something happening.
Mounting the share in the /media directory makes it appear on the desktop if you have that turned on in Ubuntu.

In my set up this script is launched by using desktop launchers with Samba icons that are integrated into the Unity DE.  To the user it looks like it belongs there.  One click to mount it and one more click to unmount it.  I've never had it fail.  If you want to use that I can give you the icon and the .desktop file.

This set up can be modified to be used by multiple Ubuntu user if it need be. 

Think about it and ask questions if you don't understand.

---

