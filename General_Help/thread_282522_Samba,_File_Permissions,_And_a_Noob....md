---
title: "Samba, File Permissions, And a Noob..."
date: 2006-10-22
forum: General Help
---

### Post by Frankenchrist on 2006-10-22
Here is my problem.  I have an Ubuntu box that I want to use as a simple home file server.  I have two other xp boxes in the house. I just want both xp users to be able to access music, pictures, etc, and hve read/write permissions.  I've gotten Samba working PARTIALLY by monkeying with various changes to the smb.conf leading to sometimes being able to see/use files and sometimes I can see directories and not get into them. So here are the questions I have.

Do I need to have 2 separate users (aside the from the main root user) on my ubuntu box?

Do these users need to be in a group? And if so can I just use the group name as the value in valid users = , force group = , force user = ?

Do ALL three (ubuntu, samba, windows) users and PASSWORDS have to be the same?

Where is the best place to share my files so ALL the users in that particular group can have access to them?  

Would I do best having this shared directory on a separate partition/drive so that people don't see anything else?

After installing Ubuntu, when I create the first user (who I assume to be the root user because it's the root pass) would I do best to create an additional user for everday use and keep the root out of any groups/shares etc.?

I realize that this is an odd assortment of questions, but I have been combing through the forums for days now having minor bits of success, but I think that my problems stem from my lack of BASIC linux knowledge that is keeping me from having a FULLY functioning samba server. Please help, I'm drowning in coffee and I refuse to float on a window any longer... :)

---

### Post by Frankenchrist on 2006-10-22
Anybody?

---

### Post by featherking on 2006-10-22
You are sort of all over the map but lets see if i can offer anything (not an expert by any means but i have some samba functionality setup on my laptop)

1. It depends on what kind of security you want. You can specify different types in the smb.conf file (check man smb.conf for more info on the types) two types stand out from memory, user and share. If you want these other computers to just be able to have free reign and not have to sign in at all i think you can set user security in the smb.conf file

2. again depends on the security. it would probably be easy to just say "allow this group" but even still they would have to have a username specified somewhere to be able to login. Again, this is when you are using the "user" security. If this is changed to "share" all of those user validating procedures are skipped

3.i dont think so, probably easier for the user signing in though

4. It doesnt matter where the folder is. You can even go into System>Admin>SharedFolders and specify what folder you want shared and how. All of this info is saved in the smb.conf file though if you want to see it written out and in more detail

5. The shared directory will be the only thing they can see unless you specify otherwise. Also they wont even be able to write to the folder unless you allow them. So having them see things you dont want is not really a concern

6. Never use the root account for daily use, thats a big security risk. Thats why they have incorporated "sudo" when you use sudo you run that command as root without actually having to be root. It just asks you for your password when you use it

Dont know if that helps as my laptop isnt really a "file-server" but ive shared things to windows computers from it before

cheers

---

### Post by Frankenchrist on 2006-10-22
Thanks for the reply.  So now I know that my normal user is not the root user unless I specify sudo- I thought that I was root because all the folder permissions were in my name.  And twenty or so minutes after I posted this I realized that file permissions are my main problem, Samba had been working correctly.  I had actually gotten somewhat familiar with the smb.conf file even though I was fuzzy on root/sudo in Ubuntu ](*,) ...  The reason I asked about the naming conventions is that my other xp box is having more problems accessing files and I thought it had to do with the username I chose which had capital letters that I couldn't duplicate in samba because I'm a linux noob in many respects :).

---

### Post by featherking on 2006-10-23
For naming conventions i guess signing in from windows it would have to be case sensitive. The basic thing to know about what security you specify in the smb.conf file is that if you are using "security = user" then the user has to have a valid account on your linux box. if you use "security = share" the user doesnt have to have a valid account. 

Then in the smb.conf you can specify if the folder is viewable by these groups or these users, is the folder writable or browseable to which users or groups? You can even force a user account to anyone who signs in. So say i sign in you force me the account of power_user, then i have access to everything power_user has access to. Even though my sign in name might be mike. You can force me a different user or group for that matter.

If you havent read the man page for smb.conf the section that starts with security is pretty good. It goes into detail on how to set different options up. As far as using capital letters, i find myself using lowercase more frequently because i forget switching between windows and linux that one of them is case sensitive.

Were you able to get the XP box to sign in when using the case sensitive username?

---

### Post by Frankenchrist on 2006-11-04
Yes it's all good.  I already had the account set up, I realized the lack of access was because of permissions- the samba server itself was set up correctly.  Thanks for replying though I've been learning alot.

---

