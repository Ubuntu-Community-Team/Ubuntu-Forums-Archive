---
title: "User Command Permissions"
date: 2008-03-29
forum: General Help
---

### Post by asellus on 2008-03-29
First off, I'll start by saying hello.  Been lurking a while, but I've found an issue that I haven't been able to easily find a solution for.  In fact, I'm not quite sure if it's possible...

I've been working on an Ubuntu server for my company -- specifically, my department within this company.  It'll be a corporate monitoring and internal knowledge base server (as well as any other neat toys we want to play with).

As this is a corporation, we have an IT department.  I need the following for their user account:

[list]Access to only directory navigation commands as well as "sudo passwd" and "sudo su" -- they need to be able to force themselves into accounts and/or password reset accounts.[/list]

[list]Heavy logging on their particular account.  I need to know when they log in, and what they do.  If easier, this can be a system-wide setting.  .bash_history tells only so much...[/list]

[list]Force a password change upon first login, and every 60 days after.  An email reminder will need to be sent for this, as they will seldom log in.[/list]

[list]Minimum password policy being x chars long, uppercase, lowercase, and numbers.[/list]

How would I do these things?  This is my first I've ever had to deal with permissions outside of "sudoer, yes/no?". :\

The server is a Proliant DL380 running Ubuntu 7.10.  If any further information is needed, please ask.

Thanks in advance!

-Ian

---

### Post by jken146 on 2008-03-29
> **asellus said:**
> [list]Access to only directory navigation commands as well as "sudo passwd" and "sudo su" -- they need to be able to force themselves into accounts and/or password reset accounts.[/list]
You can edit the file /etc/sudoers (you must use the command "sudo visudo") to include options for particular users and/or groups.  That's for the sudo commands.  If you want to prevent those users from doing anything other than viewing files and being limited sudoers, just don't give them directories in /home.

> [list]Force a password change upon first login, and every 60 days after.  An email reminder will need to be sent for this, as they will seldom log in.[/list]
I think that the **passwd** command has some options for expiry.  You might need to do a bit of scripting for the whole plan to come together on this one.


Also, file permissions allow you to restrict who can read, write and execute which files.  Very useful.  By default, a user can only write to files within his own $HOME directory.

---

