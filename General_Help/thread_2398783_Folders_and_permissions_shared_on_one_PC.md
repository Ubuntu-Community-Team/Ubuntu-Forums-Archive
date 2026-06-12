---
title: "Folders and permissions shared on one PC"
date: 2018-08-17
forum: General Help
---

### Post by mexp on 2018-08-17
I never had to work with permissions in Ubuntu, so I'm getting grey hair here...

I have two users on a PC. I want to make a shared folder, where I can put files and where the other user can access and modify them. I tried creating a group and assigning both users to that group and giving permissions and all that stuff, but it did not work. Perhaps some permissions were missing, but I could not figure this out.

Then I tried modifying the permissions from the other user so that I or anyone will be able to access and modify files on their desktop. That works, but if I add a new file there, it's then read only. 

The ideal situation would be that I could add files and folders to their Desktop, and they will be able to modify them as well, but they should not be able to access my files.

Any pointers?

---

### Post by yancek on 2018-08-17
Each user can do this type of thing in his/her own /home directory.  If you want to do it outside your user /home directory, you will need root permissions to do that, using sudo.  sudo permissions would be available with your primary user which you created during the install.  Have you used sudo to make the changes?  The site below gives a detailed explanation of changing permissions/ownership.  You might give an example of exactly how you did this, using a GUI or terminal, specific commands.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

> The ideal situation would be that I could add files and folders to their  Desktop, and they will be able to modify them as well, but they should  not be able to access my files.

Sorry, but that doesn't make sense.  If you can add files to the Desktop of userB as userA, then userA can write to and delete and obviously access files on that Desktop.  If you want a shared directory for multiple users you should do it outside the user /home directory.  I'm not really clear on the above, do you mean each users /home/Desktop directory?

---

### Post by mexp on 2018-08-20
Sorry, I was unclear on this - the other user should not be able to access my home directory. I think by default it's possible, which was surprising to me.

---

