---
title: "A dumb question about multiple simultaneous users"
date: 2020-09-04
forum: General Help
---

### Post by rsteinmetz70112 on 2020-09-04
Ubuntu allows you to have more than one user loaded and to switch between users/sessions. Since Linux is a a multi user OS are the both users active, even if they are not displayed. For example if I load two users and start an email program in both set it to download new messages will the user not currently displayed continue to receive new email or will it become inactive until I switch back to it?

---

### Post by TheFu on 2020-09-04
Seems a long way to go just to run a program under a different userid.
I'd just **su - otheruserid** in a terminal, then run the email program.

---

### Post by rsteinmetz70112 on 2020-09-07
You asked why I might want to do this here your go.

My wife and I share desktop Ubuntu computers when working from our other house. I can get her to "switch users". 

I'm not sure I can get her to open a terminal and type

```
$ su <userid> <cr>
$ Password: <password> <cr>
thunderbird & <cr>
```

just to get her email. 

If we switch users then she has access to the entire GUI including all of her apps.
Currently we log out and log back in as different users. That works well for most things.
Sometimes when we are absent for a while, which has become more common during the pandemic, updating the old email gets to be a problem. It takes awhile for the client to download new emails.

If could we have both users active and switch depending on who is using which computer and Thunderbird is actively checking for new messages the entire time it would eliminate that problem.

However I'm not sure what Gnome does when you "switch users". If it simply opens another display and that session is fully active if so the penalty will be using more memory. However, if it puts the session to sleep then its no help.
I[ found this article ]("https://embraceubuntu.com/2006/01/23/multiple-graphical-users-logged-in-at-the-same-time/#:~:text=menu%20%2D%3E%20lock%20screen%20%2D%3E,the%20screen%20to%20switch%20user.")which seems to say the second session stays active, but locked.  However it's from 2006 about 3 or 4 GUIs ago for Ubuntu :cool:

---

### Post by SeijiSensei on 2020-09-07
Both sessions will be active. Your wife will merely need to log in and run Thunderbird. Remember Unix was originally designed to support potentially hundreds of simultaneous users sharing a single machine.

---

### Post by TheFu on 2020-09-07
> **SeijiSensei said:**
> Both sessions will be active. Your wife will merely need to log in and run Thunderbird. Remember Unix was originally designed to support potentially hundreds of simultaneous users sharing a single machine.

Thousands of users.  I've seen systems with over 2K concurrent, unique, users logged in. About 500 of those had multiple connections, but none were using a GUI. They were all over ssh/rlogin.

It isn't that hard to have a window/terminal for your wife and launch 10 GUI programs, then have those minimize to a specific workspace.  Changing users would be as simple as changing the workspace. How that happens is depending on the virtual desktop controls for the window manager.  I typically run 6 workspaces under fvwm.  The list of running programs is segmented by workspace, so alt-tab stays inside the same workspace.  I was playing with this yesterday and remember using it in the 1990s.

But if you are stuck using a DE, I don't have any answer. Sorry.

---

### Post by rsteinmetz70112 on 2020-09-08
I aware of the history of Unix having worked with sever versions over the years including DEC SUN SCO AIX among others long before moving to Linux. I was wondering specifically how Gnome handled the sessions. Which I wasn't sure of.

---

