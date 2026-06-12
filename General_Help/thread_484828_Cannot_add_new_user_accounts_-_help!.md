---
title: "Cannot add new user accounts - help!"
date: 2007-06-26
forum: General Help
---

### Post by LinuxBob on 2007-06-26
The only account other than root that I have is the one I created when installing Ubuntu via CD.  This is a system admin account.  I tried using the System> Adminstrator> User (don;t hold me to the correct menu names as I am on Win PC now)  interface, select "add user," enter name, username, password etc and all looks good.  Account shows in the list.

I then log off and attempt to log on with new user name and pw, and get account not recognized.  I re-log on with my admin account and access the add user graphical interface and only root and the admin account are listed.  I have tried a dozen times now to add desktop user accounts to no avail.  

Anone know what I am doing wrong?  I only want desktop users for myself (hate running everything as admin), spouse and one guest account.

Can I get to where I need to go using "adduser" command?  If so, please list commands using generics for username and group.


Thank you

---

### Post by LaRoza on 2007-06-26
> **LinuxBob said:**
> 
Anone know what I am doing wrong?  I only want desktop users for myself (hate running everything as admin), spouse and one guest account.


In ubuntu, you will not do anything as root unless you specify it. This is not Windows.

---

### Post by LaRoza on 2007-06-26
commands:

To add acount:
```

useradd

```
Put the user name after the command

To change passwd:
```

passwd

```
Put user name after command.

---

### Post by LinuxBob on 2007-06-26
Thank you for taking the time to respond, but I still do not understand how as a system administrator I am being prevented from adding new users via the Manage User Accounts GUI under System> Administration.  

I would appreciate any infromation as this seems a basic requirement of any multi-user system.

---

### Post by Rui Pais on 2007-06-26
> **LinuxBob said:**
> Thank you for taking the time to respond, but I still do not understand how as a system administrator I am being prevented from adding new users via the Manage User Accounts GUI under System> Administration.  

I would appreciate any infromation as this seems a basic requirement of any multi-user system.

Hi.
As administration of your system your are not prevented of making new users. If the new user don't get a home after you run the Gnome GUI it's because you done something wrong or you found a bug.

Try:
```
userslist
``` to check if you have really add a user and it was just the make of home that failed.

Retry again with the GUI, but start it from command line to see if outputs any error:
```
gksudo users-admin
```
If that fails you can try command line. 
I've seen reports that useradd is broken. Didn't check for launchpad bug entries... 

There is a better (at least easier) script for that.
```
sudo adduser
```
it will ask you all needed about the new account and then add the new user and make home for it.

hth

---

### Post by LinuxBob on 2007-06-26
That is great help and will get to work on your suggesitons as soon as I return home!  Thsi typ eof reply is what makes these forums work!

---

### Post by LinuxBob on 2007-06-26
NO luck again.

$ sudo adduser
Password:
adduser: Only one or two names allowed.


Not sure what this means, any help?

---

### Post by Rui Pais on 2007-06-26
> **LinuxBob said:**
> NO luck again.

$ sudo adduser
Password:
adduser: Only one or two names allowed.


Not sure what this means, any help?

Oops, sorry my mistake :(
(bad script, not tuned for sudo use)

it should be:
```
sudo adduser *<name_of_new_user>*
```
hth

---

### Post by LinuxBob on 2007-06-26
Now it says:

$ sudo adduser bob
Password:
adduser: The group `bob' already exists.



Help more, you been great :)

---

### Post by Rui Pais on 2007-06-26
well, in that case (and assuming that bob is not your first user) either you delete that user and add it again with adduser, use **gksudo users-admin** to access it's properties or use **usermod -d** to set  to set the new home for bob :)

you can use **userslist** to chack the user that already exist (and of course ls /home to see if homes are made)

hth

---

### Post by hsweet on 2007-06-26
I had a similar problem at work.  Not sure if this is the problem, but make sure the password you assign is non-trivial.  I think there is a bug in feisty.  no warning but no account.
You can check in /home to see if a folder is made.

---

### Post by LinuxBob on 2007-06-26
gksudo users-admin
(users-admin:9947): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


This is awful, bob was name of first user but changed it to admin, boith /home/admin and /home/bob exist

????

---

### Post by LinuxBob on 2007-06-26
YOu are right problem with user bob, added one using wife's name it OK

---

### Post by Rui Pais on 2007-06-27
Hi, sorry the late reply.

> **LinuxBob said:**
> 
This is awful, bob was name of first user but changed it to admin, boith /home/admin and /home/bob exist

????

Ok, now it becames understandable. You changed the name of first user...
That can be an issue with Ubuntu administration model. 
With Ubuntu there shouldn't  exist a root (admin) account with an assigned password. The first user its assumed that is the administrator of system and sudo is used (instead of su to access root) to give a user command administrative powers. 

So your system admin is your first user, no matter it's name. But to change the name you have to use that account (the one with administrative privileges) so you will be changing the account that it's running... a tricky thing.

In order to do that rename the best option would be add another user with administrative powers and change the first account name from the second (and remove that 2nd account if not needed and after check if sudo worked for the new renamed, of course)

Can you login with both accounts, bob and admin? and they both have admin powers (they are both in sudoers list)? 
Check too if they have different ID numbers (echo $UID)

---

### Post by LinuxBob on 2007-06-29
Rui

Thanks for your patience and help, going to stick with the "admin" and forget abotu a "bob" account.  Wnated it so I could connect to an XP machine that has "bob" account but it not that huge a deal

---

### Post by Rui Pais on 2007-06-29
> **LinuxBob said:**
> Rui

Thanks for your patience and help, going to stick with the "admin" and forget abotu a "bob" account.  Wnated it so I could connect to an XP machine that has "bob" account but it not that huge a deal

No problem :)

But you can keep bob (;) he must be a nice guy) and just add that user to admin group and use it by default.
Or you can: 
```
sudo visudo
```
and add a line:
```
bob  ALL=(ALL) ALL
```
to make it a sudo user with exactly the same powers as the 1st account.

Btw, are you sure that XP need an account with same name? never heard about it (never used XP :-k)

---

### Post by Jored on 2007-08-03
Bom dia, Rui.

Your posts have been very helpful to me and allowed me to make my laptop usable again without having to reinstall Xubuntu. But perhaps you can help me solve the original problem that created my mess.

While changing some of the desktop settings on Xfce, my computer froze and I had to shut it down by cutting the power off. When I rebooted, I only got a plain blue screen with no toolbars or desktop or anything. It responded to nothing, right or left clicking.

After requesting help and browsing the forum posts, I tried tens of "solutions" but nothing worked. I could only login as root from the recovery console or go into terminal mode from my dead desktop by hitting Ctrl+Alt+F2, 

I followed your post to create a new user and grant it admin priviledges from the recovery console. This worked fine and I recreated my original envoronment successfully.

But some stuff was left over in my broken account that I would like to recover. Any ideas on how?

Also, is there a way to change my new username to the old one once everything has been transferred to the new one?

By the way, on the broken desktop, when I try to reload the panels or the background or anything, I get a Gtk WARNING ** cannot open display xfce4-panel.

Obrigado.

---

### Post by Rui Pais on 2007-09-30
Oops...

Jored, sorry, only now i stumble on the mail notification of this thread.
I got it during holidays and made a mental note to answer (i shouldn't trust my mental resources these days, to take notes :( ... ), but completely forgot 

Are you still around? have you already solved your issues?

---

