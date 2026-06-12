---
title: "Samba setup with individual remote user folders and shared folders"
date: 2013-08-13
forum: General Help
---

### Post by CampSoup1988 on 2013-08-13
I will first admit, I am pretty new with Ubuntu and Samba and researched many tutorials, I started to get Samba working, but then moved to another tutorial to get another feature working, and now after a few tutorials, its a jumbled mess.

Goal: there is will be 4 users each using Windows computers that will have an individual folder that when opened will ask them to log in with a username/password (just an individual password per user is sufficient) to view their folder.  I do not want the security to set based on computer name or the Windows user name as the computers are sometimes shared.  I also would like to have a master account that has permission to access all the folders.  Finally, I would like one shared folder that all users could access without needing to log in.

Current Situation:

       On the Ubuntu computer, unable to move/delete/rename files or folders in the main shared folder (the folder that the user folders/general folder will be in), but I could create/delete/rename newly created files/folders.  (One of the tutorial made it that I could only edit/delete/rename files and folders created after that tutorial).  (I think this seems to be a problem with Ubuntu user permissions

       On the Windows computer, one folder requiring a login but has no username/password set (as far as I could tell), another folder, I could create new files/folders, but I can not edit/delete files, even newly created files.

Here is a link to my smb.conf file:  [http://pastebin.com/CvrzmE35](http://pastebin.com/CvrzmE35)

Thank you in advance for your time and advice

---

### Post by bab1 on 2013-08-14
> **CampSoup1988 said:**
> 
Goal: there is will be 4 users each using Windows computers that will have an individual folder that when opened will ask them to log in with a username/password (just an individual password per user is sufficient) to view their folder.  I do not want the security to set based on computer name or the Windows user name as the computers are sometimes shared.  I also would like to have a master account that has permission to access all the folders.  Finally, I would like one shared folder that all users could access without needing to log in.

Current Situation:

       On the Ubuntu computer, unable to move/delete/rename files or folders in the main shared folder (the folder that the user folders/general folder will be in), but I could create/delete/rename newly created files/folders.  (One of the tutorial made it that I could only edit/delete/rename files and folders created after that tutorial).  (I think this seems to be a problem with Ubuntu user permissions

       On the Windows computer, one folder requiring a login but has no username/password set (as far as I could tell), another folder, I could create new files/folders, but I can not edit/delete files, even newly created files.

Here is a link to my smb.conf file:  [http://pastebin.com/CvrzmE35](http://pastebin.com/CvrzmE35)

Thank you in advance for your time and advice
To summarize what you have said, you want to implement the following[LIST=1]
[*]Create private shares for each user
[*]Create a public share for all users
[*]Provide for an administrative user
[/LIST]

The first item on the list (#1) can be handled by the use of the [homes] share.  Configuring this share allows all Samba user to have a private share automatically.  The requirement is that these users must be first, Linux users on that host and second, they must be Samba users with the same login as the Linux user.  This is the section in your smb.conf file that needs configuration```
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no
 
# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes
 
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700
 
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700
 
# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S
 
# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
```

The second item (#2) can be configured by providing a common user group that owns a directory with the proper permissions set.  I use the directory /srv/samba/<some_dir> .  i place all the users in a common group.  You could use the group *sambashare*.  Then I change the group ownership on the directory to be shared (some_dir).  After that I set the permissions to 2775 (u=rwX, g=rwX, o=rx).  Now when you create the share you use the path to this directory.  The share might look like this```

[public]
        comment = Shared Data
        path = /srv/samba/public

        browseable = yes

        valid users = +sambashare
        force group = sambashare
        writeable = yes

        create mask = 0664
        force directory mode = 2775


```
 

As to the third item (#3); The only user that can configure Samba is the user root.  Root always has permissions to all of the data stored anywhere on the host (computer).  Root is the the only administrative user on a Linux host.

The Windows user name does not have to be the same, but the logged in Windows user name is what Samba sees.  If the user on the Windows machine is not the same, that user will need to be careful when logging into the shares.  You might find that you can't use [homes] if the users don't use their login when using the Windows client.  In that case you will need to create and secure separate private shares using the *valid user = user* share parameter.

On the Public share you can use ```
valid user = +sambashare
```...This validates all users in the user group *sambashare*.

---

### Post by CampSoup1988 on 2013-08-14
BAB1, your summarization is correct.  Could you please take your instructions a step simpler?  In particular, what do you mean by [home] and I dont know how to setup usergroups.  Also, would the initial administrative account be considered the root account?

Thank you.

---

### Post by bab1 on 2013-08-15
> **CampSoup1988 said:**
> BAB1, your summarization is correct.  Could you please take your instructions a step simpler?  

Sure thing.   I assume you are using Ubuntu.  What version are you using?  Is there a GUI installed that you will be using?  I use terminal commands in because they are more precise and quite frankly, they are easier for me to describe what you should do.  I'll explain as I go. 
> 
In particular, what do you mean by [home]
The [homes] share (with an s) is a special share.  The one share definition serves all users private home directories on the Samba server.  Every user that you add to the sever (via a user account + samba account) automatically gets a private [homes] share in the users name.  If you set NO path in the share definition then it is automatically set to to the Linux users home home directory.  Usually this is /home/<user> (where <user> is the Linux user name.  You can turn off browsing so the user can't see the share, but can always get to the share with: smb://COMPUTER/<user> (Using Windows Explorer I assume).  Or you can leave browsing on and everyone will see all the private shares, but have access only to their own private share.

Do the users have Linux and Samba accounts on this server?  To see the user accounts you can use this command```
getent passwd | grep 100
```...this will display the users in the 1000 or > range.  The passwd database no longer has the passwords in it but the name stuck.

You can see the samba users too.  I want to see those.  You this command and post the results back here```
sudo pdbedit -L
```
>  
I don't know how to setup user groups.  That's easy.  But we should add the users first if you haven't done that already.  How many users do you expect over the life of the Samba server?  Not just today, but also in the long run?   The reason is we can specify a distinct series of user and group IDs (UID/GID) for these Linux/Samba users if you want.

The basic steps for creating the public share are just a little bit more complex than the [homes] share, but not really all that hard.  
A simple Samba user and share creation list would look like this: [LIST=1]
[*]Add the user to the Linux system (sudo adduser <user>)
[*]Add the user to the sambashare group (sudo adduser <user> sambashare (note: this group already exists)
[*]Add the user to the Samba user database (sudo smbpasswd -a <user>)
[*]Create the Samba share directory (sudo mkdir -p /srv/samba/public)
[*]Set the group ownership on that directory (sudo chgrp sambashare /srv/samba/public)
[*]Set the permissions on that EMPTY directory (sudo chmod 2775 /srv/samba/public) 
[*]Create a Samba share that has a path to the */srv/samba/public* directory
[*]
[/LIST]

> 
Also, would the initial administrative account be considered the root account?
There is only one root user on any Linux host.  This user has the power to execute almost any command available on the host (computer).  

The initial user has the right to use the command *sudo*.  Using this command means you are temporally switching to the root user and executing a command that you normally don't have access to.  Most folks think of it as allowing the *sudo* user  to execute the restricted command, but that simply is not true.  If the root user is the only one with permissions to execute the command then it root user doing that.  Remember that on a multiuser system like Linux you have the right to switch user if you know the users password the you are switching to.  By default the root user password is disabled for all users. 

Why use *sudo*?  Linux OS *_administrative users_* originally had access to the root user password.  If you left the root user logged in and walked away the system was vulnerable to anyone that wanted to do harm with root access.  Sudo allowed the administrative user to Switch User and DO a command  and then switch back to the original non-privileged user. 

The reason the initial user has the right to use *sudo *is because this is the user that installed the OS and during that time the initial user was added to the *sudo* group.  You can see this with this command```
getent group sudo
```

A lot of this stuff is confusing in the beginning.  I'm willing to explain (or not) any of these steps if that is what you want.

---

### Post by CampSoup1988 on 2013-08-15
> **bab1 said:**
> Sure thing. I assume you are using Ubuntu. What version are you using? Is there a GUI installed that you will be using? I use terminal commands in because they are more precise and quite frankly, they are easier for me to describe what you should do. I'll explain as I go. 

I am currently using Ubuntu 13.04 64-bit (Desktop).  I prefer GUI interface, just because it is easier for me to remember what to do, but I don't mind terminal commands.  Prior to setting this computer up, my only main experience with Linux was that my C++ classes had me using Solaris Terminal to compile and run the scripts.

> **bab1 said:**
> 
The [homes] share (with an s) is a special share. The one share definition serves all users private home directories on the Samba server. Every user that you add to the sever (via a user account + samba account) automatically gets a private [homes] share in the users name. If you set NO path in the share definition then it is automatically set to to the Linux users home home directory. Usually this is /home/<user> (where <user> is the Linux user name. You can turn off browsing so the user can't see the share, but can always get to the share with: smb://COMPUTER/<user> (Using Windows Explorer I assume). Or you can leave browsing on and everyone will see all the private shares, but have access only to their own private share.

Do the users have Linux and Samba accounts on this server? To see the user accounts you can use this command```
getent passwd | grep 100
```...this will display the users in the 1000 or > range. The passwd database no longer has the passwords in it but the name stuck.

 *I* only set up one initial account when I install Ubuntu.  I did not plan to install more users as this computer will be running headless as primarily a file server (Samba), media server (Serviio), and a localhost webserver (XAMPP).

 If I understand correctly, I will have to set up an Ubuntu account for each of private folders?  I do not mind if all users could see each user's folders but need to put in a password to access their folder.

 Looking at the command you gave me it seems that one of the tutorials that I followed made a 'Samba Guest' account

 ```
  

 libuuid:x:100:101::/var/lib/libuuid:/bin/sh 

 soupserver:x:1000:1000:Charles,,,:/home/soupserver:/bin/bash 

 noone:x:1002:1001:Samba guest account:/home/noone:/dev/null 

```

 
> **bab1 said:**
> You can see the samba users too. I want to see those. You this command and post the results back here```
sudo pdbedit -L
```
That's easy. But we should add the users first if you haven't done that already. How many users do you expect over the life of the Samba server? Not just today, but also in the long run? The reason is we can specify a distinct series of user and group IDs (UID/GID) for these Linux/Samba users if you want.
 I expect to only need four private shares plus one public share.  It is unlikely that I would need more.
 Here is the results of the command:
 ```
  
 noone:1002:Samba guest account 
 avahi:111:Avahi mDNS daemon
 
```

> **bab1 said:**
> The basic steps for creating the public share are just a little bit more complex than the [homes] share, but not really all that hard. 
A simple Samba user and share creation list would look like this:
 
[LIST=1]
[*]Add the user to the Linux system     (sudo adduser <user>) 
[*]Add the user to the sambashare     group (sudo adduser <user> sambashare (note: this group     already exists) 
[*]Add the user to the Samba user     database (smbpasswd -a <user>) 
[*]Create the Samba share directory     (sudo mkdir /srv/samba/public) 
[*]Set the group ownership on that     directory (sudo chgrp sambashare /srv/samba/public) 
[*]Set the permissions on that EMPTY     directory (sudo chmod 2775 /srv/samba/public) 
[*]Create a Samba share that has a path to the */srv/samba/public*     directory 
[/LIST]
 
 I will try that when I get back

> **bab1 said:**
> There is only one root user on any Linux host. This user has the power to execute almost any command available on the host (computer). 

The initial user has the right to use the command *sudo*. Using this command means you are temporally switching to the root user and executing a command that you normally don't have access to. Most folks think of it as allowing the *sudo* user to execute the restricted command, but that simply is not true. If the root user is the only one with permissions to execute the command then it root user doing that. Remember that on a multiuser system like Linux you have the right to switch user if you know the users password the you are switching to. By default the root user password is disabled for all users. 

Why use *sudo*? Linux OS *_administrative users_* originally had access to the root user password. If you left the root user logged in and walked away the system was vulnerable to anyone that wanted to do harm with root access. Sudo allowed the administrative user to Switch User and DO a command and then switch back to the original non-privileged user. 

The reason the initial user has the right to use *sudo *is because this is the user that installed the OS and during that time the initial user was added to the *sudo* group. You can see this with this command```
getent group sudo
```

A lot of this stuff is confusing in the beginning. I'm willing to explain (or not) any of these steps if that is what you want.  
    
That makes sense about the sudo.  And I would appreciate as much help you could give me.  I am sure it will also help me in the long run as well (like your explanation of Sudo vs root user).

---

### Post by bab1 on 2013-08-15
So you are the user **soupserver**  and the test user is **noone**.

The Samba uses the Ubuntu builtin user **nobody** as the anonymous (guest) user.  Notice the UID for **soupserver** is 1000 and the matching GID is also 1000, but not so for the user **noone**.  I'm picky, what happened to the user 1001?

Down the road there are reasons to keep the UID/GID's consistent.

---

### Post by CampSoup1988 on 2013-08-15
> **bab1 said:**
> So you are the user **soupserver**  and the test user is **noone**.

The Samba uses the Ubuntu builtin user **nobody** as the anonymous (guest) user.  Notice the UID for **soupserver** is 1000 and the matching GID is also 1000, but not so for the user **noone**.  I'm picky, what happened to the user 1001?

Down the road there are reasons to keep the UID/GID's consistent.

At one point I somehow had gotten a couple users through the tutorials and when the computer was restarting, was taking me to a login page instead of automatically loging into my acocunt. (Yes, I know its not safe, but I plan on once I get everything set up, running it headless.)

---

### Post by bab1 on 2013-08-15
> **CampSoup1988 said:**
> I am currently using Ubuntu 13.04 64-bit (Desktop).  I prefer GUI interface, just because it is easier for me to remember what to do, but I don't mind terminal commands.  Prior to setting this computer up, my only main experience with Linux was that my C++ classes had me using Solaris Terminal to compile and run the scripts.
I'll try and relate the terminal commands to the GUI as best as I can.> 
 *I* only set up one initial account when I install Ubuntu.  I did not plan to install more users as this computer will be running headless as primarily a file server (Samba), media server (Serviio), and a localhost webserver (XAMPP).
If you are going to run this host without a Monitor and keyboard what is the real need for the GUI.  I assume you will be managing this host with SSH; right?

As far as Samba goes you will need to create accounts for each user.  This doesn't mean that they have to login to this host.  But they do need the login and password.  You are the system administrator so you get to manage these accounts.> 

 If I understand correctly, I will have to set up an Ubuntu account for each of private folders?  I do not mind if all users could see each user's folders but need to put in a password to access their folder.

Both a Linux account and a Samba account.  Then the users [homes] share will be available (if configured).

> 
Looking at the command you gave me it seems that one of the tutorials that I followed made a 'Samba Guest' account
 ```
  

 libuuid:x:100:101::/var/lib/libuuid:/bin/sh 

 soupserver:x:1000:1000:Charles,,,:/home/soupserver:/bin/bash 

 noone:x:1002:1001:Samba guest account:/home/noone:/dev/null 

```


 I expect to only need four private shares plus one public share.  It is unlikely that I would need more.
 Here is the results of the command:
 ```
  
 noone:1002:Samba guest account 
 avahi:111:Avahi mDNS daemon
 
```


 I will try that when I get back

No, you need 1 [homes] share and 1 public share.  The 1 [homes] share expands (progamically) to each users home directory (/home/<user>). 
> 

  
    
That makes sense about the sudo.  And I would appreciate as much help you could give me.  I am sure it will also help me in the long run as well (like your explanation of Sudo vs root user).

---

### Post by bab1 on 2013-08-15
> **CampSoup1988 said:**
> At one point I somehow had gotten a couple users through the tutorials and when the computer was restarting, was taking me to a login page instead of automatically loging into my acocunt. (Yes, I know its not safe, but I plan on once I get everything set up, running it headless.)

We can straighten the users UID/GID out pretty easily if we do it before they start populating the shares with data.

Why is running headless unsafe?  I don't see headless hosts as unsafe at all.

---

### Post by CampSoup1988 on 2013-08-15
> **bab1 said:**
> I'll try and relate the terminal commands to the GUI as best as I can.If you are going to run this host without a Monitor and keyboard what is the real need for the GUI.  I assume you will be managing this host with SSH; right?

If you can't relate everything to GUI, don't worry.  I know Linux seems to focus more on terminal then GUI.  I'll just be taking a little more notes.

I plan to use Vino (since it came with Ubuntu) as the host from the Ubuntu computer and access it via TightVNC Client on my computer.  I know this is off topic, but Vino has been really annoying me.  It seems whenever I restart the computer, I have to restart the computer like 3 times before I could get Vino to not close a few seconds after the computer boots.

> **bab1 said:**
> 
As far as Samba goes you will need to create accounts for each user.  This doesn't mean that they have to login to this host.  But they do need the login and password.  You are the system administrator so you get to manage these accounts.
Both a Linux account and a Samba account.  Then the users [homes] share will be available (if configured).


Ok, so I understood that correctly. :P

> **bab1 said:**
> 
No, you need 1 [homes] share and 1 public share.  The 1 [homes] share expands (progamically) to each users home directory (/home/<user>).

Ok.

---

### Post by bab1 on 2013-08-15
> **CampSoup1988 said:**
> If you can't relate everything to GUI, don't worry.  I know Linux seems to focus more on terminal then GUI.  I'll just be taking a little more notes.

I plan to use Vino (since it came with Ubuntu) as the host from the Ubuntu computer and access it via TightVNC Client on my computer.  I know this is off topic, but Vino has been really annoying me.  It seems whenever I restart the computer, I have to restart the computer like 3 times before I could get Vino to not close a few seconds after the computer boots.

I use SSH redirecting X server to use GUI based apps (ssh -X).  I didn't like VNC at all.  It just transports the video.  SSH actually allows you to run the remote GUI locally.  Are you using Ubuntu for your personal use?

---

### Post by CampSoup1988 on 2013-08-15
The one feature I did like with Vino compared to some of the other desktop sharing programs is that it allows me to share the same session (?).  If I open a window through the client, it opens it on the host.  It doesnt require to be logged out or a second session, like the other ones seem to be, but I could be mistaking.

This will be used for a family server, yes.  But I dont plan to use it for personal use (ie: my personal laptop).

---

### Post by bab1 on 2013-08-15
> **CampSoup1988 said:**
> The one feature I did like with Vino compared to some of the other desktop sharing programs is that it allows me to share the same session (?).  If I open a window through the client, it opens it on the host.  It doesnt require to be logged out or a second session, like the other ones seem to be, but I could be mistaking.

This will be used for a family server, yes.  But I dont plan to use it for personal use (ie: my personal laptop).

My question was to what OS you use on your laptop.  Is it Ubuntu or Windows? 

Have you tried SSH from your laptop to the "server"?

---

### Post by CampSoup1988 on 2013-08-15
Oh, sorry, the rest of the computers in our house is either Windows Vista (various versions) or Windows 7.  I have also tried the androidVNC app from my phone, but I am finding that to be way too much work then its worth.

I have not in this case.  The only time I have used SSH before was in my capstone class where we had to use PuTTy and WinSCP to access our Amazon ec2 Ubuntu server we had to develop for our project (my team mates did most of the Ubuntu work, my main focus was the database, but for that we only had terminal access).  I will look more into it in a bit, as we are getting a bit off topic here?

---

### Post by bab1 on 2013-08-15
> **CampSoup1988 said:**
> Oh, sorry, the rest of the computers in our house is either Windows Vista (various versions) or Windows 7.  I have also tried the androidVNC app from my phone, but I am finding that to be way too much work then its worth.

I have not in this case.  The only time I have used SSH before was in my capstone class where we had to use PuTTy and WinSCP to access our Amazon ec2 Ubuntu server we had to develop for our project (my team mates did most of the Ubuntu work, my main focus was the database, but for that we only had terminal access).  I will look more into it in a bit, as we are getting a bit off topic here?
Indeed.

Have you added the other users yet? These do not need to have administrator access.  You can do this to create the user and add them to the sambashare group```
sudo adduser <user> sambashare 
```...try one and see what it looks like using this```

sudo getent passwd <user>
```...remember to substitute the real user name for <user> in these commands.

---

### Post by CampSoup1988 on 2013-08-15
> **bab1 said:**
> Indeed.

Have you added the other users yet? These do not need to have administrator access.  You can do this to create the user and add them to the sambashare group```
sudo adduser <user> sambashare 
```...try one and see what it looks like using this```

sudo getent passwd <user>
```...remember to substitute the real user name for <user> in these commands.

I am creating the account for my private folder right now.  I knew what you meant by <user>.

I just got to the step for ```
smbpasswd -a <user>
``` and after I realized I needed sudo for it, what is this password for?  Is it the password that I need to access the folder from another computer and not the account's login password?

---

### Post by bab1 on 2013-08-15
> **CampSoup1988 said:**
> I am creating the account for my private folder right now.  I knew what you meant by <user>.

I just got to the step for ```
smbpasswd -a <user>
``` and after I realized I needed sudo for it, what is this password for?  Is it the password that I need to access the folder from another computer and not the account's login password?

The command adds a user to the Samba users database.  The name and password should match the Linux user name/pass.  This will be the password used to access the shares we make.

---

### Post by CampSoup1988 on 2013-08-16
> **bab1 said:**
> 
The basic steps for creating the public share are just a little bit more complex than the [homes] share, but not really all that hard.  
A simple Samba user and share creation list would look like this:
[LIST=1]
[*]Add the user to the Linux system (sudo adduser <user>)
[*]Add the user to the sambashare group (sudo adduser <user> sambashare (note: this group already exists)
[*]Add the user to the Samba user database (sudo smbpasswd -a <user>)
[*]Create the Samba share directory (sudo mkdir -p /srv/samba/public)
[*]Set the group ownership on that directory (sudo chgrp sambashare /srv/samba/public)
[*]Set the permissions on that EMPTY directory (sudo chmod 2775 /srv/samba/public)
[*]Create a Samba share that has a path to the */srv/samba/public* directory
[/LIST]


Ok, I have done up to step 7.  I am not sure what to do for that step.

---

### Post by bab1 on 2013-08-16
> **CampSoup1988 said:**
> Ok, I have done up to step 7.  I am not sure what to do for that step.

To add the share we add this at the bottom of the smb.conf file```

[public]
        comment = Shared Data
        path = /srv/samba/public

        browseable = yes

        valid users = +sambashare
        force group = sambashare
        writeable = yes

        create mask = 0664
        force directory mode = 2775


```

This will require the user to log in, but all 4 users logins should work.  All files and folders should be available to the users in the sambashare group.  This means read, write, delete, move, copy, etc.  The only thing that is not permitted is creating executables in this directory by those that do not have sudo rights.

Let me know if it all works.  I am curious myself.  If you have problems let me see what is going on by posting output of the following commands```

getent passwd | grep 100

getent group sambashare

sudo pdbedit -L

ls -ld /srv/samba/public

ls -l /srv/samba/public

ls -ld /srv/samba

ls /ld /srv


```

---

### Post by CampSoup1988 on 2013-08-17
> **bab1 said:**
> To add the share we add this at the bottom of the smb.conf file```

[public]
        comment = Shared Data
        path = /srv/samba/public

        browseable = yes

        valid users = +sambashare
        force group = sambashare
        writeable = yes

        create mask = 0664
        force directory mode = 2775


```

This will require the user to log in, but all 4 users logins should work.  All files and folders should be available to the users in the sambashare group.  This means read, write, delete, move, copy, etc.  The only thing that is not permitted is creating executables in this directory by those that do not have sudo rights.



Done, though I used a different folder name instead of public, in which I substituted my folder name in its place.

> **bab1 said:**
> To add the share we add this at the bottom of the smb.conf file```

Let me know if it all works.  I am curious myself.  If you have problems let me see what is going on by posting output of the following commands[CODE]
getent passwd | grep 100

getent group sambashare

sudo pdbedit -L

ls -ld /srv/samba/public

ls -l /srv/samba/public

ls -ld /srv/samba

ls /ld /srv


```

I have created only one additional account so far, for my private folder, and I was unable to access the folder (my Windows computer kept asking me to log in).  Here is the results of those commands:

```

soupserver@Pantry:~$ getent passwd | grep 100
libuuid:x:100:101::/var/lib/libuuid:/bin/sh

soupserver:x:1000:1000:Charles,,,:/home/soupserver:/bin/bash
noone:x:1002:1001:Samba guest account:/home/noone:/dev/null
campsoup1988:x:1001:1003:CampSoup1988,,,:/home/campsoup1988:/bin/bash

soupserver@Pantry:~$ getent group sambashare
sambashare:x:124:soupserver,campsoup1988

soupserver@Pantry:~$ sudo pdbedit -L
noone:1002:Samba guest account
campsoup1988:1001:CampSoup1988
avahi:111:Avahi mDNS daemon

soupserver@Pantry:~$ ls -ld /srv/samba/PantryShelves
drwxrwsr-x 2 root sambashare 4096 Aug 16 14:35 /srv/samba/PantryShelves

soupserver@Pantry:~$ ls -l /srv/samba/PantryShelves
total 0

soupserver@Pantry:~$ ls -ld /srv/samba
drwxr-xr-x 4 root root 4096 Aug 16 14:35 /srv/samba

soupserver@Pantry:~$ ls /ld /srv
ls: cannot access /ld: No such file or directory
/srv:
samba
```

Update

I just realized, you probably meant for me to do ```
ls -ld /srv
```  Correct?

In that case, I got the following results:
```

drwxr-xr-x 3 root root 4096 Jul 23 15:06 /srv

```

---

### Post by bab1 on 2013-08-17
You were correct.  I made a typo and I will correct it for others that might follow.

> I have created only one additional account so far, for my private folder, and I was unable to access the folder (my Windows computer kept asking me to log in). 

I assume that the [homes] share expanded to your private share correctly and you just can't get in.  What user are you logged in as?  Windows sends that information to Samba when you try and access the Samba share.

[COLOR="#0000FF"]**Edit:** Post your version of the [homes] share please.[/COLOR]

[COLOR="#0000FF"]**Edit2:** How did you get to the [homes] share?  Did you try and browse or use the direct location bar? [/COLOR]

---

### Post by CampSoup1988 on 2013-08-17
> **bab1 said:**
> You were correct.  I made a typo and I will correct it for others that might follow.



I assume that the [homes] share expanded to your private share correctly and you just can't get in.  What user are you logged in as?  Windows sends that information to Samba when you try and access the Samba share.

[COLOR=#0000FF]**Edit:** Post your version of the [homes] share please.[/COLOR]

[COLOR=#0000FF]**Edit2:** How did you get to the [homes] share?  Did you try and browse or use the direct location bar? [/COLOR]

No problem, everyone makes mistakes once in a while and that was a simple mistake.

Oh the server I am logged in as soupserver.  On my laptop the username is CampSoup1988.

I don't know how to check the version of [homes]

If you are referring to how I got to the shared folder on my laptop, I went My Computer --> Network --> [ComputerName] --> Pantry Shelves

---

### Post by bab1 on 2013-08-17
> **CampSoup1988 said:**
> No problem, everyone makes mistakes once in a while and that was a simple mistake.

Oh the server I am logged in as soupserver.  On my laptop the username is CampSoup1988.

I don't know how to check the version of [homes]

If you are referring to how I got to the shared folder on my laptop, I went My Computer --> Network --> [ComputerName] --> Pantry Shelves

Aren't you going to use the [homes] share for the private shares?  Are we going to use the shares that I talked about?  Even if it is located here: /srv/samba/PantryShelves?

If not, what shares are you proposing to use?

The remote user needs to be the same as the samba user (which by extension this means the Linux user too).

---

### Post by CampSoup1988 on 2013-08-18
I am sorry for misunderstanding how you want me to set up the [homes]  I must not fully understand it yet.  Sorry.

By remote user, do you mean that their username they used to log into the computer is the same as their Ubuntu username?

This project of mine is making me so noobish.  I know Ubuntu is different then Windows, but I didn't expect this much troubles.....

---

### Post by bab1 on 2013-08-18
> **CampSoup1988 said:**
> I am sorry for misunderstanding how you want me to set up the [homes]  I must not fully understand it yet.  Sorry.
I provided you the exact instructions on how to create a [homes] share.  Maybe you didn't see that.  Check post #2 in this thread.  If you don't understand it completely, ask ***before *** you start the configuration. > 
By remote user, do you mean that their username they used to log into the computer is the same as their Ubuntu username?

Yes.  If this host is a Windows machine then the logged in users name is presented to Samba for authentication BEFORE you even see the share.  This means the Windows user and the Linux user must match.  As the Linux user should also have a Samba user of the same user name, all 3 should match.
> 
This project of mine is making me so noobish.  I know Ubuntu is different then Windows, but I didn't expect this much troubles.....
Samba is complex.  It can be configured many different ways.  Do you want me to provide you with specific commands?  It seems as if you just wanted the idea of what to do and you would handle the rest.

Your test user should have an account on both Windows and Linux with the same user name (login).
The Linux user needs to have a samba user with the same user name (smbpasswd -a)

The [homes] share needs to be configured in the smb.conf file

The Linux file system needs to be configured for the Samba public share
The Samba [public] share needs to be configured in the smb.conf file

If you have questions, ask BEFORE you start to configure anything.  I think you are close.  The actual commands are simple, understanding what they mean may need some explanation.  Do you need step by step help?

---

### Post by CampSoup1988 on 2013-08-18
> **bab1 said:**
> I provided you the exact instructions on how to create a [homes] share.  Maybe you didn't see that.  Check post #2 in this thread.  If you don't understand it completely, ask ***before *** you start the configuration. 


I *thought* I had understood it.  I overlook post #2 when I actually got started, and started with post #4.  I shall go back and look again.

Is this how you want me to configure [homes]?

```


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
[homes]
   comment = Home Directories
   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
   valid users = %S

```

> **bab1 said:**
> Yes.  If this host is a Windows machine then the logged in users name is presented to Samba for authentication BEFORE you even see the share.  This means the Windows user and the Linux user must match.  As the Linux user should also have a Samba user of the same user name, all 3 should match.


I thought I explained I did not want the authentication to be the Window's computer log in names since each computer has only one user name, and the computers are sometimes shared.  What I wanted was when the user clicked on the private folders (regardless of their Windows username, they are asked to log in with a username and password (or just a password).

What I did was Linux username == Samba username =/= windows username.  Actually I was going to make them all match initially, but Ubuntu did not let me create a new user with capital letters.

I am able to see the PantryShelves folder on my Windows computer when I go My Computer --> Network --> [ComputerName] but i cant open the folder.

> **bab1 said:**
> 
Samba is complex.  It can be configured many different ways.  Do you want me to provide you with specific commands?  It seems as if you just wanted the idea of what to do and you would handle the rest.


Initially I thought I could understand what I needed to do with you just guiding me through it, but I seem to be stumbling through it too badly and frustrating both yourself and myself. (Again, I apologize for your patients)

> **bab1 said:**
> 
Your test user should have an account on both Windows and Linux with the same user name (login).
The Linux user needs to have a samba user with the same user name (smbpasswd -a)

The [homes] share needs to be configured in the smb.conf file

The Linux file system needs to be configured for the Samba public share
The Samba [public] share needs to be configured in the smb.conf file

If you have questions, ask BEFORE you start to configure anything.  I think you are close.  The actual commands are simple, understanding what they mean may need some explanation.  Do you need step by step help?

---

### Post by bab1 on 2013-08-18
> **CampSoup1988 said:**
> I *thought* I had understood it.  I overlook post #2 when I actually got started, and started with post #4.  I shall go back and look again.

Is this how you want me to configure [homes]?

```


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
[homes]
   comment = Home Directories
   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
   valid users = %S

```


Yes this is correct.  If you want to use /home/<user> as the "private directory.  As you can see you need to have created a user so you can have the home directory created too.  
> 

I thought I explained I did not want the authentication to be the Window's computer log in names since each computer has only one user name, and the computers are sometimes shared.  

I didn't make the rules.  Windows will send the logged in user name in the background when you try and connect with the Samba server. 
> 
What I wanted was when the user clicked on the private folders (regardless of their Windows username, they are asked to log in with a username and password (or just a password).
Just follow along and let's see what you get with what I said to do.  This is a test bed for you anyway I hope.

What I did was Linux username == Samba username =/= windows username.  Actually I was going to make them all match initially, but Ubuntu did not let me create a new user with capital letters.
Trust me; You don't want to use capital letters, spaces or weird characters anywhere when configuring Linux or Linux based apps.> 

I am able to see the PantryShelves folder on my Windows computer when I go My Computer --> Network --> [ComputerName] but i cant open the folder.
Is the user a member of the smbshare group?  I'll bet not.  Every Samba share is either authenticated or the user  changed to nobody and the group is no group.  If you want shares that are completely open to anyone on the network and the server is really a desktop then I would just use the GUI to make a "usershare" open to **everbody**.> 

Initially I thought I could understand what I needed to do with you just guiding me through it, but I seem to be stumbling through it too badly and frustrating both yourself and myself. (Again, I apologize for your patients)
It is important to understand what you can and can't do with Samba.  You can't have authenticated private shares that don't have a user in a database to authenticate too.  In addition if you try and connect with a user that is NOT in the database you won't ever be allowed to attempt authentication.  I just added a temporary [homes] share to a test Samba server.  I can login to the share with a different user name as long as the user I connect with is in the database also.

My test would be the following:

[LIST=1]
[*]Two Linux users with matching Samba users (smbpasswd -a) 
[*]One Windows user that matches 1 of the Linux users above
[*]
[/LIST]

Then we can test.  I'm sure this will work.

You can PM me about why and I'll try and explain.

---

### Post by CampSoup1988 on 2013-08-18
To summarize to make sure I understand properly.  I will not be able to connect with any Windows user accounts that the username has a capital letter, correct?

---

### Post by bab1 on 2013-08-18
> **CampSoup1988 said:**
> To summarize to make sure I understand properly.  I will not be able to connect with any Windows user accounts that the username has a capital letter, correct?

I didn't say that.  You said that.  I just said you will learn that there are less problems if you learn to use lower case letters, no spaces or characters that are not - or _ or . (dot) for user names or when configuring the system.  Out of habit I try and make any name as short as possible.

This is really a PM type topic.  Would you like to PM me?

---

