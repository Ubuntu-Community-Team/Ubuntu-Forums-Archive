---
title: "Xubuntu 14.04lts Default User Privileges and tweaks."
date: 2014-10-19
forum: General Help
---

### Post by Ubu1son on 2014-10-19
Hi,

I've installed Xubuntu 14.04lts about a 2 weeks ago, set up most things.
Just Wanting to finish off.

I created a standard user and admin user. For admin I went into groups and added to adm,lp,lpadm,sudo.

Did I create them correctly?

Also, I went into advanced and ticked some extra options like audio etc, but then read that it refers to something totally different, and shouldnt be checked.

What would be the default user Privileges checkboxes for both a standard user and admin user?



I also wanted to create a third account, sort of like the mac master account, that no user can deleted, not even another admin.  Is this possible in xubuntu?



Thanks.

Would really like to change the loading screen background too, before the logon screen, can this be done?

---

### Post by TheFu on 2014-10-19
> **Ubu1son said:**
> I also wanted to create a third account, sort of like the mac master account, that no user can deleted, not even another admin.  Is this possible in xubuntu?

Any user with a way to escalate to root can shoot any other user in the foot, chest, head ... including the root userid and their own userid.
A better way to manage access is NOT thru userids, but through groups and strictly controlling which commands + options any group is allowed via the sudoers controls.  **man sudoers** explains.  I believe that home Linux users do not use the idea of groups enough which are extremely powerful. 

BTW - I've never bothered to create a separate account to perform administrative tasks, but perhaps I should?  Why did you do that? Can you please explain?

Xubuntu is based on Linux and UNIX.  All UNIX systems work this way, unless something like SELinux has been added.

---

### Post by yancek on 2014-10-19
You should not have needed to create a separate admin user in Xubuntu as the primary user, the one you must create during the installation, is given root privileges through sudo.  Any users created after do not have those privileges unless you modify the system to grant them.  This would be similar to what you refer to as a 'master account', the primary user is the only one who can change anything for that specific account/user.

---

### Post by Ubu1son on 2014-10-20
To set up a pc for two people, one has to be able to do updates, install software, change settings ( display etc), and the other no installing or updating or changing settings .

So I have no choice but to make one admin ( thus part of sudo group) and the other standard user.  But the problem is, even the admin user can majorly stuff up settings, corrupt profile, delete users trying to "fix things".  So I  like to have an account to use that's set up and cant be deleted by the admin, can that be achieved only by configuring the sudoers file, or is it impossible?

Also, is there any way to remove a user form the logon screen and any "password" pop up screens, so that it can be used to log on only by choosing "other" on logon screen?


BTW, I checked default privileges, why is the connect to network and scanners unchecked, or are they similar to audio and mean something else?

---

### Post by Bucky Ball on 2014-10-20
*Thread moved to **General Help**.*

---

### Post by TheFu on 2014-10-20
> **Ubu1son said:**
> To set up a pc for two people, one has to be able to do updates, install software, change settings ( display etc), and the other no installing or updating or changing settings .  Or you could allow both to modify it or you could pay someone outside these 2 people to manage it for you and neither would ahve admin rights.  I remotely managed my Mom's PC for years before she died - from 500 miles away. She didn't have any admin rights.

> **Ubu1son said:**
> So I have no choice but to make one admin ( thus part of sudo group) and the other standard user.  But the problem is, even the admin user can majorly stuff up settings, corrupt profile, delete users trying to "fix things".  So I  like to have an account to use that's set up and cant be deleted by the admin, can that be achieved only by configuring the sudoers file, or is it impossible?

You have many choices - infinite choices actually.  An admin user on any computer system that doesn't implement roll-based authentication can trash a system. That is just the nature of the game.  Don't like that - get a Solaris machine, get trained in using it, pay the $10K extra for those features .... or live with the methods Linux, OSX, BSD and Windows provide.  Any user that has root edit permissions can delete any userid on the system. PERIOD. It is unlikely, but I know I could do it.  Are you trying to protect against stupidity or malicious intent?  Stupidity is easier since the GUI tools won't do it, but if they know how to run **sudo vi /etc/passwd** and delete a line and save the file - all is lost.  Make sense?

[http://www.ibm.com/developerworks/library/l-rbac-selinux/](http://www.ibm.com/developerworks/library/l-rbac-selinux/) - implies that **SELinux** can do what you want. That is not usually deployed on Ubuntu, but I suppose it could be.  The extra complexity is probably more effort than any Ubuntu desktop user is interested in learning, but feel free to have at it.

> **Ubu1son said:**
> Also, is there any way to remove a user form the logon screen and any "password" pop up screens, so that it can be used to log on only by choosing "other" on logon screen?  Yes - depends on the login screen program. I don't run nominal Ubuntu Desktop, so cannot help. There is a guide for this here somewhere or on help.ubuntu.com

> **Ubu1son said:**
> BTW, I checked default privileges, why is the connect to network and scanners unchecked, or are they similar to audio and mean something else?

Giving a userid the power to control networking is dangerous. To the uninformed, it doesn't seem like much, but they gain the power to read all network communications with that privilege - if they know what they are doing. For a home computer that doesn't move, there is no need for an average user to have network control permissions. If it is a laptop and they move to other networks, then changing network settings is mandatory for the system to be useful elsewhere.

Lots of great questions ... learning a little about the UNIX design philosophy will answer many more questions you probably have.  You'll see how smart the people before us were and will be thoroughly impressed, I'm certain. Lots of great reading on that stuff out.

---

### Post by Ubu1son on 2014-10-20
> **TheFu said:**
> Any user that has root edit permissions can delete any userid on the system. PERIOD. It is unlikely, but I know I could do it.  Are you trying to protect against stupidity or malicious intent?  Stupidity is easier since the GUI tools won't do it

No, not malicious.
But more like they do first, think later.  Don't want them to delete their own admin account, and be left with a user account....   But wouldn't xubuntu stop that via the GUI, if someone is trying to delete the only admin account?
The reason I want a untouched account, is if they totally corrupt their admin account, I have a fresh, setup admin account ready to go.  And they need to be admin, they wont accept not being able to install an app, change a setting, or do updates.


> Giving a userid the power to control networking is dangerous.....If it is a laptop and they move to other networks, then changing network settings is mandatory for the system to be useful elsewhere.

So if its installed on a laptop, then for them to join other wifi networks, the network box in user privileges should be checked?

---

