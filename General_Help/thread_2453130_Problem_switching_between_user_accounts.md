---
title: "Problem switching between user accounts"
date: 2020-11-03
forum: General Help
---

### Post by username2758 on 2020-11-03
Hello!

I'm definitely not an expert in Linux but could sucessfuly switch between two different user accounts at the same time on Ubuntu version 16.xx (1x admin account and 1x standard account), accessing the standard account while keeping the admin account logged in simultaneously.

Now on a fresh install of Ubuntu 20.04 I can't access both accounts at the same time as I did before, having to logout from the main account before logging into the second account.

Why is that?

---

### Post by TheFu on 2020-11-03
Why not just use **su - {admin-account-name}** in a terminal to have a window with admin rights and use the non-admin user all the time? 
Standard Unix techniques have been lost for last 25+ yrs, but they still work.  Any basic Unix Beginner book explains the use of **su {admin-account-name}** and **su - {admin-account-name}** to change to different userids.

Or you could use the {admin-account-name} and **su - {standard-account}**, but that would be less desirable for security reason.

I've never used the GUI "switch user" stuff. Never saw the point, when it was so trivial to access a different userid from any terminal on the system.

---

### Post by username2758 on 2020-11-03
Hi there,

I don't think I fully understand your reply. I am aware using an admin account on Linux all the time can be dangerous, but that didn't answer my main question.

My main question was why is it I can't access two different user accounts at the same time on Ubuntu 20.04? Now I have to first log out from whichever user account in order to log in to the other registered user account.

How can I solve this?

---

### Post by TheFu on 2020-11-03
> **username2758 said:**
>  
My main question was why is it I can't access two different user accounts at the same time on Ubuntu 20.04? Now I have to first log out from whichever user account in order to log in to the other registered user account.
 

You don't need to logout to access another account.
[LIST=1]
[*]Open a terminal. 
[*]Enter **su - {name of other account}**
[*]Type in the password for the other account. Now you are that other useid, inside that terminal.
[*]Launch programs from that terminal.
[/LIST]
This has worked for 40 yrs.

---

### Post by username2758 on 2020-11-04
> **TheFu said:**
> You don't need to logout to access another account.
[LIST=1]
[*]Open a terminal. 
[*]Enter **su - {name of other account}** 
[*]Type in the password for the other account. Now you are that other useid, inside that terminal. 
[*]Launch programs from that terminal. 
[/LIST]
This has worked for 40 yrs.
Thanks, I didn't know that. But what I'm trying to do is a little different.

Since I'm using this fresh Ubuntu 20.04 install as my main home server, it stays up 24/7. It is a simple home setup and I'm sharing the same Ubuntu 20.04 machine with another family member to use the operating system via GUI. So, in my case there are two user accounts: 'user 1' (me) and 'user 2' (relative).

The problem is that I can't log in to 'user 2' without logging out from 'user 1' account first. I'm trying everything. For example, when I click on the 'user 2' icon after hitting CTRL+ALT+L (Lock/Switch Account), nothing happens. It used to work in my previous installation of Ubuntu 16.xx.

What is happening?

---

### Post by TheFu on 2020-11-04
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1825544](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1825544)
has some things to try. Seems 17.10 and later had the problem.  Some people didn't see the problem until 18.04 or later.

I've never used this. My "servers" don't have GUIs. We each have our own client devices and use **x2go** to connect to remote desktops if we need a GUI on a faster machine. That won't work for everyone.

[https://help.ubuntu.com/stable/ubuntu-help/shell-exit.html.en](https://help.ubuntu.com/stable/ubuntu-help/shell-exit.html.en) is the Ubuntu Desktop Guide. Seems switching-users should still work, since it is documented there. Multiple accounts must already be setup on the system.

Hopefully, someone else, perhaps a GUI person, will come and have a better answer.  Sorry, I can't make any other suggestions.

---

