---
title: "Grant user access to multiple sftp folders"
date: 2018-05-23
forum: General Help
---

### Post by billybobjay on 2018-05-23
Hi, 

I am trying to give a specific user access to multiple sftp user folders in order to have one account to handle our data retention, pull data from each folder individually and such.  But I am little lost on the best way to grant this user access to each folder and am looking for recommendations?  I want the user to be able to traverse between each folder but not allow the owners of each folder to traverse between each of them.  I have tried ACL's but I keep running into an issue where the recursive does not hold once a new folder is created.  I have tried the following below-

sudo setfacl -R -m u:example_user:rwX,d:u:example_user:rwX,G:example_group:RwX /folder_location

And a few other combinations but whenever a owner creates a new folder and places a file in it the new user I am attempting to create this for does not retain the permissions.

Any help would be appreciated.

Thanks,

---

### Post by TheFu on 2018-05-24
Welcome to the forums.

sftp honors Unix permissions just like they are local accounts.

I wouldn't use ACLs.  They are often forgotten and will trip up the next guys.
I would use Unix groups.  Each userid is placed into their own group by default on Ubuntu systems. Using group membership, you could add the sftp-admin userid to the personal groups for each user and set the sgid permission bit on the directories that both users should have access into with a umask of 002.   
If you don't want the sftp-admin to have access anywhere each user does, but just 1 specific directory structure, then create a new group (userid-sftp) for each userid and add the userid into it along with the sftp-admin account.  Then use normal group sharing file permission techniques for the specific directories involved. 
Main things for this are:
* force the userid-sftp to be the group on the folder (chgrp) with group write permissions (g+w)
* force all new files in that folder to be in that group (g+s)
* make the admin and userid part of the same group
* ensure the umask is 002 or 007, whatever you need

That should do it.  No hidden permissions with ACLs that are forgotten. All new files and subdirs get the correct group automatically.

If you need more details, ask. I can find step-by-step group sharing info if it isn't already understood.

You can place all these sftp directories somewhere next to each other, if you like, or in the HOME directory, but I'd be inclined NOT to put them into the HOME for users as a way to clearly show they are shared.

---

### Post by billybobjay on 2018-06-05
Thanks appreciate the help, I understand the concept but yes a tutorial would be helpful, I have not had a ton of experience in setting up users within groups and retaining those permissions for each user in linux, given this is the SFTP server and it is located in the DMZ I want to make sure I get it right for security reasons.  So any info you would have on the steps needed would be really appreciated.

Thanks again,

---

### Post by TheFu on 2018-06-05
> **billybobjay said:**
> Thanks appreciate the help, I understand the concept but yes a tutorial would be helpful, I have not had a ton of experience in setting up users within groups and retaining those permissions for each user in linux, given this is the SFTP server and it is located in the DMZ I want to make sure I get it right for security reasons.  So any info you would have on the steps needed would be really appreciated.

Thanks again,

Sorry, I don't have a tutorial, just steps from a beginning Linux class I taught.
```
Working Together

1.   Put everyone into the same group.
2.   Create a directory where they can share files.
3.   Make the group on that empty directory have rws permissions

               $ sudo gpasswd -M  user1,user2,user3  ourgroup
               $ mkdir -p /tmp/Workspace
               $ chmod g=rwxs Workspace
               $ ls -l Workspace
                  drwxrws---   owner    group    Workspace/ 
               $ chgrp ourgroup Workspace
               $ ls -l Workspace
                  drwxrws---   owner    ourgroup    Workspace/ 

```
It is expected that you understand Unix directories, permissions, user, and group management already. Do not copy/paste.

---

### Post by billybobjay on 2018-06-05
Were I get confused is, if I put everyone in the same group wont't that alter the permissions they have for the group they are already in?  Or does it simply add them to another group and each user now belongs to 2 groups?

---

### Post by TheFu on 2018-06-05
> **billybobjay said:**
> Were I get confused is, if I put everyone in the same group wont't that alter the permissions they have for the group they are already in?  Or does it simply add them to another group and each user now belongs to 2 groups?

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) or the LPI training docs are probably what you need.
Really, you should spend 45min in a temporary directory with 3+ userids and 5+ groups and play around with the settings until the light bulb clicks 2-3 times. Nothing will replace that knowledge.

---

### Post by billybobjay on 2018-06-06
Thank again for helping, I read the chapter on Linux file permissions, did some more searching and came up with the following,

I created 2 test users named tom & jerry

This created to SFTP folders one named Tom and one named Jerry, I then created a group called cartoon.  

I added Tom and Jerry to the group using-

sudo user mod -a -G cartoon tom
sudo user mod -a -G cartoon jerry

I then changed the group on the directory for /srv/sftp/tom with-

sudo chgrp -R cartoon /srv/sftp/tom
sudo chgrp -R cartoon /srv/sftp/jerry

Then I modified the permissions with -

sudo chmod -R 775 /srv/sftp/tom
sudo chmod -R 775 /srv/sftp/tom


This works for access but it does not inherit from the top folder down, I found that tom cannot delete folders in the next directory that jerry created or vice versa, my question would be, how do I make all new folders, files and such inherit those same permissions to allow tom and or jerry to delete files?

---

### Post by TheFu on 2018-06-06
[B]chmod g=rwxs Workspace
[/B]
or
[B]chmod g+s Workspace
[/B]

The setgid permissions bit is important.

---

### Post by billybobjay on 2018-06-06
Thanks again for the help, I used to know more of this but then got a Windows job for 2 years lol.  

I reviewed on the setgid permissions here-

[https://linuxconfig.org/how-to-use-special-permissions-the-setuid-setgid-and-sticky-bits](https://linuxconfig.org/how-to-use-special-permissions-the-setuid-setgid-and-sticky-bits)

And attempted what you had said, but it still will not let me delete files uploaded by tom with jerry's account.  To Re-Cap I deleted each user, folders, groups and started fresh just to make sure I did not error on this.



When I did it this time I kept it closer to my real goal where winscp will be logging in and have access to testuser's folder, essentially I want to have a winscp account to be able to check each of the sftp directories for new uploads, pull information down or delete it for data retention.  

I used the following-

$ sudo groupadd sftp
$ sudo usermod -a -G sftp testuser
$ sudo usermod -a -G sftp winscp
$ sudo chgrp -R sftp /srv/sftp-users/testuser
$ sudo chmod -R 775 /srv/sftp-users/testuser
$ sudo chmod g+s /srv/sftp-users/testuser

The ls -l lists off as-

drwxrwsr-x 2 testuser     sftp         4096 Jun  6 13:47 testuser

Yet when I log in with the winscp account and access a folder that testusers has uploaded I cannot upload and or delete any files, this is ironically the same issue I had with setting the ACL's which was how I originally planned this, to be clear Winscp can upload and delete files in the testuser directory but cannot delete files or folders that are created in the testuser directory by testuser, sorry just trying to be clear lol.  I am not sure were I am erroring here but any help would be appreciated.

Thanks,

---

### Post by TheFu on 2018-06-06
What are the full permissions for the files that work and how are those different from the files that fail?

---

### Post by billybobjay on 2018-06-06
So I created a folder and a file in the test user directory, one file, one folder with each account.

drwxr-s--- 2 testuser sftp 4096 Jun  6 15:14 Test_Created_By_Testuser
drwxrwsr-x 2 winscp   sftp 4096 Jun  6 15:13 Test_Created_By_Winscp
-rw-r----- 1 testuser sftp  993 Jun  6 15:13 Uploaded_by_testuser.lnk
-rw-rw-r-- 1 winscp   sftp  993 May 11 15:53 uploaded_by_winscp.lnk


The group & public permissions differ from Winscp vs Testuser what is confusing me is I created the group sftp and added each user so shouldn't if reflect that when files are created or uploaded by either user since they belong to that group?

---

### Post by TheFu on 2018-06-06
umask under sftp(the protocol) appears to be non-standard for Testuser.  Should be 002 or 005 or 007.

[https://serverfault.com/questions/70876/how-to-put-desired-umask-with-sftp](https://serverfault.com/questions/70876/how-to-put-desired-umask-with-sftp) says to change an option inside the sshd_config file.
```
Subsystem sftp /usr/lib/openssh/sftp-server -u 002
```
The sshd_config manpage has more info, if you need it.   If that doesn't work, other possible methods are in the link too.

Fishing for answers is fun! See how we worked through the issue to get to the umask first?  
BTW, I don't know of any automatic way to apply ACLs to newly created files/directories.

---

### Post by billybobjay on 2018-06-06
Would that also be the reason the ACL's I created did not stick either, I had the same problem, except everything would work in any directory with either users except for after the acl was set a new upload would not retain the recursive option.

---

### Post by billybobjay on 2018-06-06
I appreciate the help and the digging is fun, I thought about adding the ACL command to cron so it would run every hour since the winscp account will not be checked by anyone other than automation, but I really would like to get this with a set solution instead of a patch script.

---

