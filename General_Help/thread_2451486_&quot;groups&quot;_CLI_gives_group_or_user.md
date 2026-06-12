---
title: "&quot;groups&quot; CLI gives group or user ?"
date: 2020-10-05
forum: General Help
---

### Post by helen314 on 2020-10-05
I am trying to implement "group" for purpose of accessing user files in multi-boot system 
My question is : 

The command 'groups"  reply includes the user who did the command. 
So in my case 
user a 
is included as a "group" , 

So is "a" a group" or user ? 
I am confused. 



a@a-desktop:~$ groups
a adm cdrom sudo dip plugdev lpadmin sambashare
a@a-desktop:~$

---

### Post by deadflowr on 2020-10-05
> So is "a" a group" or user ?
Both
When you create a user in Ubuntu it also creates it's own group for the user.

---

### Post by helen314 on 2020-10-05
OK, it doe not make much sense,     
so I have a group a  with  a user a ? 
Now I'll add existing user b to group a ? 
yes, I did check - user b exists. 



a@a-desktop:~$ sudo usermod -a -G a b
a@a-desktop:~$ groups
a adm cdrom sudo dip plugdev lpadmin sambashare
a@a-desktop:~$ 










Please explain this:

a@a-desktop:~$ groups
a adm cdrom sudo dip plugdev lpadmin sambashare
a@a-desktop:~$ sudo groupadd OS_group 
[sudo] password for a: 
groupadd: group 'OS_group' already exists
[B]
exists ? where ??[/B]

a@a-desktop:~$ sudo groupadd OS_a_group 
a@a-desktop:~$ groups
a adm cdrom sudo dip plugdev lpadmin sambashare
a@a-desktop:~$ 


[B]where is added group ?? ( do i need to reboot ?) 
[/B]

---

### Post by deadflowr on 2020-10-05
> **helen314 said:**
> OK, it doe not make much sense,     
so I have a group a  with  a user a ? 
Now I'll add existing user b to group a ? 
yes, I did check - user b exists. 



a@a-desktop:~$ sudo usermod -a -G a b
a@a-desktop:~$ groups
a adm cdrom sudo dip plugdev lpadmin sambashare
a@a-desktop:~$ 
The groups command as used only shows the current user's group list.
Since you only added group a to user b it's not going to show group a in user b's output, since it' not showing user b's output.
Try
```
id <user b>
or 
groups <user b>
```
change user b to the proper username.
It will list all groups that user b is in.

> Please explain this:

a@a-desktop:~$ groups
a adm cdrom sudo dip plugdev lpadmin sambashare
a@a-desktop:~$ sudo groupadd OS_group 
[sudo] password for a: 
groupadd: group 'OS_group' already exists
[B]
exists ? where ??[/B]

a@a-desktop:~$ sudo groupadd OS_a_group 
a@a-desktop:~$ groups
a adm cdrom sudo dip plugdev lpadmin sambashare
a@a-desktop:~$ 


[B]where is added group ?? ( do i need to reboot ?) 
[/B]
You only created a new group. (Well you actually created two groups; both OS_group and OS_a_group are two different groups)

It doesn't add it to any existing user's group until you add the group to a user's group listing.

---

### Post by helen314 on 2020-10-05
Let's clarify 
When "User" "a"  is created same name group "a" is also created. 
When "User" "b  is created same name group "b"  is also created. 

a@a-desktop:~$ sudo usermod -a -G a b 

Adds WHAT "b" - user or group (?)   to group "a"  - it should add user "b"  to group a. 

Is there any advantage of sing "ID" instead of name ?


Now - if I wnat to have "group"  of user "a"  - which is in one of the  mutiboot systems 
and user "z"  which is in another  of mutiboot system  -** how do I accomplish that **? 
( this question is sort of dupe / follow-up on my other post )

---

### Post by The Cog on 2020-10-05
> where is added group ?? ( do i need to reboot ?) 
You need to log out and back in to pick up the new group, no need to actually reboot.

---

### Post by Holger_Gehrke on 2020-10-05
> **helen314 said:**
> Let's clarify 
When "User" "a"  is created same name group "a" is also created. 
When "User" "b  is created same name group "b"  is also created.

Exactly.
> **helen314 said:**
> 
a@a-desktop:~$ sudo usermod -a -G a b 

Adds WHAT "b" - user or group (?)   to group "a"  - it should add user "b"  to group a. 


You can't have groups as members of groups. The name of the command -- 'usermod' should give it away: **user** account **mod**ification.
Perhaps it becomes more clear using long option names:
```

usermod --append --groups a b

```
So the 'a' is a parameter to the '--groups' option giving a comma-separated list without spaces of all the groups to which user b should be added. For more details see the manual to usermod, available by typing 'man usermod' into your shell. 
> **helen314 said:**
> 
Is there any advantage of sing "ID" instead of name ?

Rarely. Internally the system uses the numerical uid for everything, so there is a small overhead for looking that up for a given name, but unless you have thousands of users in the system it shouldn't matter.

> **helen314 said:**
> 
Now - if I wnat to have "group"  of user "a"  - which is in one of the  mutiboot systems 
and user "z"  which is in another  of mutiboot system  -** how do I accomplish that **? 
( this question is sort of dupe / follow-up on my other post )

Let me see if I understand the situation: you have a multi-boot system with two (or more) Linux based operating systems. On OS1 you have a user a (with a group a), on OS2 you have a user z (with a group z). You want to set things up in such a way that user z is a member of group a. This really doesn't make much sense because each OS has it's own database of users and groups. The ownership and group of a file are stored as the numerical uid and gid in the inode for the file, and unless you carefully keep those databases of users and groups in sync between the two OSs (having the same users and groups on both systems with identical numerical ids) you're going to get some serious crossover (like user a being the first user account set up on OS1 and having uid 1000 and gid 1000 for his group, and user z being the first user of OS2 also having a uid and gid of 1000 -- if both systems follow the ubuntu numbering system for users and group which starts 'real' users and their groups at 1000; in that case if you mount a file system created on OS1 containing files owned by user a and group a in OS2 they would appear as being owned by user z and group z).

Holger

---

### Post by helen314 on 2020-10-05
**This really doesn't make much sense because each OS has it's own database of users and groups.**

Well - it does because for yet unknown reason I cannot boot to OS with user z. 

I started posting here with brief  explanation what I am trying to do, unfortunately my posts get answered  independently.  

It is not my intend to repost, but I found out that simple - sort of Yes /No posts are more productive than lengthy, covering   more ground , posts. 
So this is one of them "simple ones". . 

But to clarify - I have no issues with any "cross access" by BOTH users as you describe it. NONE.

[B]I need a user "a"  in perfectly functioning  OS  to access files in inaccessible OS , user "z ". 

In technical terms - I need a group with users a and z. 
( So far I am unable to do so - having access only to user a  ) [/B]

My intend is twofold 
1. do whatever to gain normal , boot, access to OS of user z  - I suspect problem with RAID5 array accessible only by user z.
2. if I cannot restore access to my primary OS  - with user z - I like to copy required files  from user z to user a 


I'll more then happy to use other method(s)  to recover access to my primary data - all in perfectly working RAID5 array.

---

### Post by TheFu on 2020-10-05
Normal users don't control booting of any Unix OS. Users only matter at and after login.  Before then, everything runs using daemon accounts. In the Windows world, they'd probably be called "service accounts."

I agree that it is unfortunate that Ubuntu creates users and groups with the same names whenever a new userid is created.
It is also unfortunate that the uid and gid (those are the numbers, like 1000, 1001, etc.) seem to match, but that is purely, 100% coincidence.  uid and gid are completely separate.

Those numbers need to match on any OSes that will share the same storage.  The names don't have to match, but you probably want them matching for your sanity.

System A
  uid 1000 - username steve - gid 1000 - groupname steve
  uid 1001 - username betty - gid 1001 - groupname betty

System B
  uid 1000 - username s - gid 1000 - groupname stevegroup
  uid 1001 - username b - gid 1001 - groupname bettygroup

If you want s and b to have read-write access to the same files, then create a new group and put both s and b into that group.  You'll probably want to do exactly the same on System A with usernames "steve" and "betty" too.

The next group created will probably get a gid of 1002 and if we use a groupname "ourfiles".  Just need to do the same on System B.

All of this assumes you use Linux file systems, not NTFS, not vFAT, not fat32, not exFAT.  Those don't support Unix groups without lots of effort and usually don't support chmod, chgrp, chown commands either.

If you need clearer commands and examples, search these forums for "working together" ... [https://ubuntuforums.org/showthread.php?t=2382965](https://ubuntuforums.org/showthread.php?t=2382965) is one example.

The real trick is to ensure any storage shared between systems - that can be dual, quad-boot or with NFS - that the uid and gids map between those systems.  The 'id' command should be used on both systems.  'id' has a few options, so be certain to check out the manpage so you can actually see the information you need to see with the least hassle.

As for RAID5, often the best solution for RAID issues is to wipe everything, pave the array, create a new array and restore from backups.  We all know that RAID is never a backup and that RAID solves only 2 problems while backups solve over 1000 problems, including bad RAID setups.

---

### Post by helen314 on 2020-10-06
I really appreciate your reply. It makes perfect sense in theory , however, as pointed out – I need more help applying the theory .  
 
 
 Here re is what Mrs Google found,  
 
 
 “First, we're going to add a temporary user, since we don't want to edit a user that we're currently logged into. So, run the following commands in the Terminal, hitting Enter after each one:
  sudo useradd -d /home/tempuser -m -s /bin/bash -G admin tempuser  sudo passwd tempuser  Type in a new password for the temporary user when prompted. Reboot and log in as tempuser. Then, open up the Terminal and type in the following commands, once again hitting enter after each one (and replacing yourusername with your Linux user's username):
  sudo usermod --uid 501 yourusername  sudo chown -R 501:yourusername /home/yourusername  This will change your Linux user's UID to 501 and fix your home folder permissions so that you still own them. Now, you should be able to read and write to both your Mac and Linux user's home folder, no matter what OS you're logged into.”
 

 
 
 
 The “problems” are multiple – starting with entering the entire first line  
 
 
 DOES not  
 create new user  
 does not stop for “enter”  after “each one”   
 there is no “admin” group ...
 purpose of many options is not explained
 ( there is a difference between -d and -D )  
 why /bin/bash ?
 Is “adm” the “common group users are being added to ?  
 
 
 
 
 Actually I did partially create (another) new user using Ubuntu “System setting” , but it does not show-up in /home/x  
 
 
 I feel the best way to add user to  “common” group  (adm?) would be to use single command and EXPLAIN, the original text does very poor job in that, what each individual step does.  
 
 
 For example start with plain “add user “  
 sudo su  
 useradd  NEW_USER  
 
 
 should work ?
 
 
 Now add such user to adm  group (?)  
 
 
 here I need some help, please.  




PS
Yes, I am about to delete the RAID causing "timeout ". 
I am going to make a separate post for the RAID issue

---

