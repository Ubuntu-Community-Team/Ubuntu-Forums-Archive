---
title: "Application to lock an application"
date: 2015-11-06
forum: General Help
---

### Post by mayasl on 2015-11-06
Hi,

Is there any application that I can use to lock applications with a password?

---

### Post by TheFu on 2015-11-06
Normal file permissions?
Be careful doing this if you don't fully understand Unix users, groups and permissions. Lots of people come here for help after they've done something bad.

---

### Post by mayasl on 2015-11-07
> **TheFu said:**
> Normal file permissions?
Be careful doing this if you don't fully understand Unix users, groups and permissions. Lots of people come here for help after they've done something bad.

You haven't answered my question yet! ;)

I want some kind of application similar to App Lock for Windows. Is anything available?

---

### Post by TheFu on 2015-11-07
Don't know anything about App Lock. Sorry.  Maybe alternativeto.net will help?
If the description here: [https://alternativeto.net/software/applocker/](https://alternativeto.net/software/applocker/) is correct - applocker does things that are already part of Unix. Use the file system permissions.

Just because you don't like the answer doesn't mean it isn't correct. There are lots of different ways to solve any single issue on Unix. I can think of about 4 for this. If you don't understand something, ask. We'll try to provide links for learning.

Normal File permissions can restrict access to programs on a group or user-by-user basis. groups can require a password a password. If you want to get really fancy, you can use ACLs, but that quickly becomes a nightmare. There is also SELinux, which becomes a nightmare. Sudo controls is another - force users to *sudo -u app-userid run-program* to run these restricted programs. That gets old quickly. I setup one of those to solve a problem for 6K users at one company. It was ugly and a pain to maintain. It also used groups to manage access to programs.

Trying to prevent end-users from installing any software depends on how bullet-proof you want that to be. Unix is about power-to-the-users at the core. Anyone can install software into their HOME if they know how to override the default locations. End-users can copy files and programs are just files. The only ways I know to prevent that is to take away all write access to HOME (including settings control) and everywhere else on the system.  You can also overwrite/cleanup HOME with a script every 10 minutes to remove any files you don't approve. It won't stop a user from installing a program, but it will make her get smarter to figure out a way around the removal.

There are How-Tos about locking down the environment for end-users. Those systems become single-program machines to those users. I've created a menu system at one client who just wanted 5 options for users.
* program 1
* program 2
* program 3
* Change Password
* Logout
Caught all interrupt (cntl-c, etc.) and we had to prevent the allowed programs from accessing a "shell" - since that is built-in to many non-trivial programs. Pretty much every editor has a way to shell out, for example.
Think the Unix-way to solve this. Thinking the Windows-way will lead to unhappiness on a Unix system for many requirements. Out of the box, Unix is extremely flexible, provided you understand the subtle capabilities of common features.

There are many different solutions. None of them are "install any applications" and toggle some checkboxes, if that is what you want. Sorry. A thorough understanding of groups, users and permissions will be needed regardless.

---

### Post by mayasl on 2015-11-07
Thank you very much for the detailed explanation!

I think my question was incomplete, therefore you did not understand my requirement. Fault was mine. So, I apologise.

 My situation is a bit different. Two of us use the same machine and same user account. Now what I want is, to install an app on the system and hide it from the other person.

---

### Post by TheFu on 2015-11-07
Shared userid? These days? I cannot imagine that anywhere.   Heck, I create new userids all the time just to try out new things. User segregation is core to [The Unix Philosophy.]("https://en.wikipedia.org/wiki/Unix_philosophy")

If the other person isn't a sophisticated user, shouldn't be hard.   Create another userid, install the program for that userid only. Then  you can **su -** to the other userid to run it. I would do the install manually, don't use the package manager. There are important risks when doing this, but if the program isn't too tightly tied to the OS, shouldn't have bad impacts.

But for one well-versed in Unix, I think it is next to impossible. After all, the process table will show the program running. Plus it is trivial for the other person to ssh into the machine to monitor anything they like.

I'm becoming uncomfortable with where this is headed.

---

### Post by mayasl on 2015-11-09
Other user is not much friendly with Ubuntu. So, I have changed the file permission of the respective binary to 000. Now even if it shows in the dash, it is not executable. Whenever I need to use that app, I have to change the permission to the default value to run it. It's a temporary solution, till I find an "app" that locks the apps as in Windows.

Thank you @TheFu for the assistance. :)

---

### Post by TheFu on 2015-11-09
Standard Unix groups can do this.

---

### Post by mayasl on 2015-11-09
> **TheFu said:**
> Standard Unix groups can do this.

I am not supposed to move him to some other user group, according to a policy. ;)

---

