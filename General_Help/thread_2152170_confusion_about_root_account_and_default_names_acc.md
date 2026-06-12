---
title: "confusion about root account and default names account created upon installation"
date: 2013-06-07
forum: General Help
---

### Post by cheeseburger38 on 2013-06-07
Unix/Ubuntu newbie here. A question about user accounts.

I installed the latest stable of Ubuntu to setup a file share. When I installed it I gave a user name for an account it asked for and also a password. This is the user name and password I have to use when I log in. 

I setup a folder to share in my home/<username> directory by right clicking, selecting sharing options, and enabling sharing of the folder to all users. Then I went to my Windows PC on the same LAN and selected the folder that I just shared on Ubuntu to map to a drive in Windows. However, I am prompted to enter root as the username and the password I supplied for the account that was setup at install time. The username (and associated password) I see on login prompt is not accepted.

I know what su and sudo do. I never setup a root password at install time. But sudo works with the same password as my name user account. I do not get how that works. Why are the passwords the same for user name and root accounts?

I just want to be clear so that I am not inadvertently setting up a security issue.

I tried searching the forums for similar topics but could not find it so I hope others who have this same confusion are cleared of it.

Help appreciated

---

### Post by bantuvez on 2013-06-07
For sudo you use your own password, not the root's password. (On Ubuntu  the root account has no password, so it is not possible to login as  root.) Sudo just gives you root privileges.

---

### Post by 3rdalbum on 2013-06-07
Sudo allows chosen users to become root without learning root's password. When sudo asks for a password, it is to authenticate the user and confirm that the user has the right to access root privileges.

---

### Post by cheeseburger38 on 2013-06-07
Then why does my user name and and login password not work for registering the Samba share from the Windows machine? Why does it only work when I use root and my password?

---

### Post by redmk2 on 2013-06-07
> **cheeseburger38 said:**
> 

[COLOR="#0000FF"]Sudo allows chosen users to become root without learning root's password. When sudo asks for a password, it is to authenticate the user and confirm that the user has the right to access root privileges. [/COLOR]
> 
Then why does my user name and and login password not work for registering the Samba share from the Windows machine? Why does it only work when I use root and my password?

These are 2 different notions.  Sudo is used to run specific commands using the root account.  The user doesn't become the user root at all.  The That's the magic of the tool sudo.  Are you saying the the dialog box is requiring that you use the user name: *root* and your your user password.  Have you enabled the user: *root*'s password?  Can you su to root (with the prompt of **#** ?  

As far as accessing a Samba share with any specific name; it really has to do with how you set up the share.  Did you add any users to the Samba user database.  From Ubuntu, what is the output of ```
sudo pdbedit -L
```

Let's see what the share looks like```
net usershare info --long
```

And finally; what are the permissions for the share directory ```
ls -ld <path/directory>
```... where <path/directory> is the actual path to the directory you shared (i.e. /home/<user>/directory).

---

### Post by cheeseburger38 on 2013-06-08
sudo pdbedit -L gives

root:0:root


net usershare info --long gives:

[myshare]
path=/home/myname/myshare
comment=
usershare_acl=Everyone:F,
guest_ok=n



and the permission check gives:

drwxrwx--- 5



Clearly I have not set up my username for sharing. But I do not see this option in the sharing menu when you right click on a folder to share. I presumed becaus eI was logged into my username, a samba entry for my user would be created. However this does not appear to be the case. The sharing dialog box has no option to add certain users. 


I suppose I should use swat. But getting the options set in swat is no easy task for a newbie, which is why I used the dialog box.

This username by the way is the one Ubuntu asked me to make upon installation


Thnkyou for the help

---

### Post by bab1 on 2013-06-08
...

---

### Post by redmk2 on 2013-06-08
> **cheeseburger38 said:**
> sudo pdbedit -L gives

root:0:root

So you don't have an smbpasswd user with your login.  My guess is that you were the user *root  *when you made the share (maybe gksudo nautlilus).
> 

net usershare info --long gives:

[myshare]
path=/home/myname/myshare
comment=
usershare_acl=Everyone:F,
guest_ok=n

This share only allows a valid user (acl=Everyone:F) and no guests (guest_ok=n).  Since the only user in the smbpasswd data base is the user *root* and there is no password for this user, you are locked out.
> 

and the permission check gives:

drwxrwx--- 5
This does nothing to help us.  How about the entire output please.  Samba provides access but not ownership and permissions.> 

Clearly I have not set up my username for sharing. But I do not see this option in the sharing menu when you right click on a folder to share. I presumed because I was logged into my username, a samba entry for my user would be created. However this does not appear to be the case. The sharing dialog box has no option to add certain users.

I'm not a big fan of usershares anyway.  It's trivial to setup a share using a simple text editor.  The file we would edit is /etc/samba/smb.conf.  
> 

I suppose I should use swat. But getting the options set in swat is no easy task for a newbie, which is why I used the dialog box.
Samba SWAT sucks.  it will cause you more trouble than it's worth.> 

This username by the way is the one Ubuntu asked me to make upon installation

And that would be...

We need all the info to help you.  The user name and the directory ownership are helpful to providing the correct commands for you to use to resolve your issues.  This is not a security problem.  The info is only valid to check and see what needs done to set up sharing correctly.

If you want to do this on your own, here is what you need to do:

[LIST]
[*]Add you login to the smbpasswd data base (smbpasswd -a)
[*]Edit the smb.conf file (as root) to create a share with the correct path and Samba access
[*]Create the directory that holds the share at the site you defined in smb.conf
[*]Set the ownership and permissions on the entire path including the directory you are sharing
[/LIST]

---

### Post by Sef on 2013-06-08
Click on [RootSudo]("https://help.ubuntu.com/community/RootSudo") for information.

---

