---
title: "how to start an application at login time"
date: 2008-04-29
forum: General Help
---

### Post by keenboy on 2008-04-29
Hi Guys,

Can somebody tell me which file I need to edit to start an application at login time?

My problem is I have Kalarm installed for clients on an ubuntu 7.10 LTSP, and it has a bug where it doesn't start at login time there for the alarms don't go off!

So I thought I'd start it automagically at login.

Thanks

---

### Post by bijeeshvs on 2008-04-29
go to sessions manager and in the startup programs add a new launcher. In the command box type the name of the program u want to start,( if you are doubtful abt the program name type it in a terminal window to make sure the correct app is started) and close it u are done

---

### Post by forestpixie on 2008-04-29
Try adding it to sessions in System > Preferences

---

### Post by keenboy on 2008-04-30
Unfortunately I have locked down my users desktops so I don't have this function.

I was looking to do it on the command line if possible.

Hopefully there's a file in the users home dir that can be edited to achieve this?

---

### Post by Monicker on 2008-04-30
> **keenboy said:**
> Unfortunately I have locked down my users desktops so I don't have this function.

I was looking to do it on the command line if possible.

Hopefully there's a file in the users home dir that can be edited to achieve this?

You can put it in ~/.bashrc (per user) or /etc/bashrc (system wide), which executes every time a user logs in.

---

### Post by chunchengch on 2008-04-30
This command will open the "Sessions Preferences" window (screenshot attached)

[COLOR="Red"]$ gnome-session-properties[/COLOR]


[ATTACH]68129[/ATTACH]

---

### Post by keenboy on 2008-04-30
This is what I needed. I do tend to make my life a little complicated.....

Because I have locked down the LTSP clients they do not have this tool so I run it from the command prompt, no worries!

However I want to use the "remember currently running applications" so that the application(kalarm) stays running in the panel.

The problem I have is because I ran gnome-session-properties form the command prompt, a terminal is started at login time!

---

### Post by ryanhaigh on 2008-04-30
You should be able to use 
```

nohup gnome-session-properties

```
so that you can close the terminal and if I have remembered correctly the command will not be terminated.

---

### Post by tiggsy on 2008-05-09
I set up a session to start kalarm at startup and though it is listed as running in the current sessions, nothing shows up.

Before, i wasn't able to run kalarm without using "sudo kalarm" in terminal, so i changed the session command to that. Same results.

When i run kalarm without sudo, i get the error message: 

DCOPClient::attachInternal. Attach failed Could not open network socket

I also got some permission denied messages for
.kde          } I fixed these with 
.kde/share    } sudo chown
.kde/tmp-tiggsys-desktop/startkdeinitlockXXXXXX.tmp - this file and folder dont exist, so how do i chown them so that kalarm will run without sudo?

**update** I fixed this by running "kalarm" (not sudo kalarm) in terminal repeatedly, making a note of the folders that were Permission denied and then doing *sudo chown tiggsy* for each of them. In some cases, I had to make the folders first, so as to chown them. To do this i used Places to find the folder and work my way down to the level required.

I also had to chown .kde/share/apps/kalarm/calendar.ics to get it to store alarms.

---

