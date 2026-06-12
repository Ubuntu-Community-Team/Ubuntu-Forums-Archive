---
title: "Don't have user rights to copy files"
date: 2007-10-22
forum: General Help
---

### Post by jf1991999 on 2007-10-22
I am a new Ubuntu and Linux user.   I have set up a dual boot system with XP and Gutsy.  I want to copy my windows Firefox profile into the Gutsy firefox profile and when I try to copy and paste it won't allow me to,

I thought this might have been due to the different file systems.  However, I tried to edit the html file with a text editor and it got the don't have permissions error when trying to save the file.  I can't see how I would log in as an admin.  In my user settings I seem to have admin rights.  Any help would be greatly appreciated.

---

### Post by UK-Wobbie on 2007-10-22
> **jf1991999 said:**
> I am a new Ubuntu and Linux user.   I have set up a dual boot system with XP and Gutsy.  I want to copy my windows Firefox profile into the Gutsy firefox profile and when I try to copy and paste it won't allow me to,

I thought this might have been due to the different file systems.  However, I tried to edit the html file with a text editor and it got the don't have permissions error when trying to save the file.  I can't see how I would log in as an admin.  In my user settings I seem to have admin rights.  Any help would be greatly appreciated.

You can login as root that will give you permissions!
But do not set your profile as root! 

Go to (SYSTEM) Then to (ADMINISTRATION) Then (USERS AND GROUPS)

When you are in user and groups click on root then click on properties... In properties go to set password by hand! You need a new password to log in as root.

Then when that is done click close and go to (SYSTEM) Then to (ADMINISTRATION) Then (LOGIN WINDOW).. When you are in there go to security. Then click on the box next to
 "Allow local system administrator login" When you have done that log out and put your password to log in as root... And User name is ROOT :lolflag:

Your now in as root and you have ever permission to do what you like to do!

But do not make your profile as root! 
Or play about with files what you do not no.

Only use the root login for your own work!

If you got a file what you like on your own desktop... Right click on it and go to "properties"..
Then go to "permissions".. Where it says owner that can be root or you or a program!

Click on your name if you like it to by yours.. NOT ROOT .

Thats it your done ;)

---

### Post by jf1991999 on 2007-10-22
Thanks for the tip.  I was able to log in as root and copy the firefox bookmarks.html file successfully.  I changed the user permissions to my normal login as the owner.  When I launch firefox as root the bookmarks are there however when I log out and login as my normal user there are no bookmarks.  What is really annoying is that I can add a bookmark and clearly the file is stored somewhere else but I am unable to find it.

Also I read that you can get temporary admin rights using sudo in the terminal application.  I am new to this and terminal boxes scare me.  I also read that 'nautilus' which I assume is the file browser can get admin rights.  How do I do this within the file browser?

Any help with these two issues is greatly appreciated.

---

