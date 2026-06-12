---
title: "Permission problems i need a folder with unlimited permissions"
date: 2008-03-14
forum: General Help
---

### Post by CameronCalver on 2008-03-14
Hello ok this might be a bit confusing so ill try to make it simple firstly i have a ubuntu computer set up with proftpd ftp server and it shares /home/FTP-shared and inside it has /uploads and /downloads
 but forget about the uploads  folder right now.
I have xsane setup so it scans a multipage document which when saves comes out as image...tiff  for eg and then at a computer an hour drive away i can access this folder by loggin into the ftp with userftp and then the password.
So ...
When i scan something and it creates the file and then go on the ftp on the other computer i can see the file but if i try and copy it it says permission problems.
Well this ftp has a password so im not to worryed about security so could i make this /home/FTP-Shared/uploads/ a folder which anyone can access . yes i no i can just change that in the permission dialog box but inside /uploads there is folders like /scans and inside /scans there is folders like how do i set it so whenever someone creates a folder inside there it is goin to have a certain permissions? anyone please help

---

### Post by arvevans on 2008-03-14
If you just want to open up all permission options, then using the Command Line Interface may be the easiest way to go:
[INDENT]cd path_and_directory
sudo chmod 777 ./*.*
cd ..
sudo chmod 777 ./your_directory[/INDENT]

Use "man chmod" to see what you will be doing.

Hope this helps.  It is brute-force but it should get the job done.

Arv
_._

---

### Post by CameronCalver on 2008-03-15
i did those commands to /home/FTP-shared/ and /home/FTP-shared/download and /home/FTP-shared/download/scan but still if i scan and it makes /home/FTP-shared/download/scan/img.tiff i cannot dowload the file  i dont no wat to do?

---

### Post by ibuclaw on 2008-03-15
Perhaps creating a new Group in Ubuntu could solve it?

To give you a quick rundown through what I would do. I'm only making judgemental guesses here. Though I've done the same thing on my filesystem and it's worked where chmod hasn't before. (I don't have a network storage device, so I don't know if it works the same)

First, Go Into:
System>Administration>Users and Groups

When the app loads, click on "Manage Groups" followed by "Add Group"

Now name the group something memorable. For example : "ftpshare".
And tick all the users who you want to be part of that Group (ie: who are going to use the folder.)
[[IMG]http://img243.imageshack.us/img243/2053/groupgq6.th.png[/IMG]](http://img243.imageshack.us/my.php?image=groupgq6.png)
Change the group ID if you must, Though it isn't necessary.
Also note, that my screenshot has an error. Linux won't accept CAPITALS in user and group names.

Next, go into the directory outside the folder you're trying to change (preferably in the terminal).
if your in the terminal enter this
```
 sudo chown root:ftpshare /home/FTP-shared -R && chmod 775 /home/FTP-shared -R 
```
or
```
 sudo chown ftpshare:ftpshare /home/FTP-shared -R && chmod 755 /home/FTP-shared -R 
```

chown is a command that changes the "ownership:group member" of the folders. -R does this recursively, so applying it to the parent folder is all you need to do!
NOTE: Depending on whether or not you want root to be the owner of the folder, I've set out the code accordingly. And the path-to may be wrong, I'm only writing this as of what I know from what you wrote down in your first post.

After that, logout and log back in again. And fingers crossed, I hope it works.

Iain

---

### Post by CameronCalver on 2008-03-15
haha well  i tryed to do it as calver:ftpshare and it worked but to sign into my ftp i use another account on my computer called userftp so i tryed userftp:ftpshare AND it worked!! BUT! i could copy and transfer all files but then when opening xsane it could not write to it because it ran as user cameron not userftp so it did not have write acess haha how do i do this?

---

### Post by ibuclaw on 2008-03-15
If I'm reading this right.
Xsane runs as another user?

 Ermm... First impression, make sure that the folder permission is 775:
```
 sudo chmod 775 /home/FTP-share -R 
```

 o Re-Open "**Users and Groups**"
 o Go back to the "**Manage Groups**" and 
 o Scroll down till you see "**ftpshare**", and 
 o Click "**edit**".
 o Make sure that "**cameron**" is part of the group (his name should be checked).

If you are still having trouble...
NOTE: If someone uses the "**cameron**" account, I advice not doing this, but if it is there purely for the Xsane app, try this:
 o Go back to "**Manage Groups**"
 o Scroll down till you see "**userftp**" and
 o Add "**cameron**" to the "**userftp**" group.

Logout, login...

Hope this fixes it!

Regards, Iain

[EDIT]
PS:
If you get this working, great!
Else, perhaps waiting for 8.04 to be released first before you have a crack at it again, Ubuntu's new PolicyKit looks like a very promising way of handling these sorts of things. Hope it handles folders as well as apps!

---

### Post by CameronCalver on 2008-03-15
oh well you got it a little wrong cameron is the default account for this computer and userftp is the user that has the /home/FTP-share yeah and maybe i should try making the ftp share the folder /home/cameron/FTP-share ill give it a go

---

### Post by CameronCalver on 2008-03-15
got it there was a umask option on the  config i needed to set to 777

---

