---
title: "Feisty - can't loggin - only recognizes users in clp"
date: 2007-04-30
forum: General Help
---

### Post by outdoormonkey on 2007-04-30
Hi all,

I'm new to the forums and feisty is my first foray into ubuntu and linux (except for some darwin experience).

I just installed feisty fawn for the first time on an older "mystery" box.   I used the alternate cd (verified the check sum and the cd integrity) since I don't think there's much ram.

Install is complete and at the loggin screen it says my user name or password is incorrect.

After trying quite a few combinations I figured I really must have forgotten (like an idiot) the username/password I created during the installation.

I have reset the password (and set a root password) several times now using both recovery mode and the grub "trick" ([http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html)).  I still have the same problem at the GUI login screen.  In recovery mode I can login to root and, *IF* I'm logged in as root, I can "login <username>" into my account using the username/password that do not work at the GUI login screen. 

(Note: in recovery mode, the same username/password won't work if I pull up a login prompt - I have to be logged in as root first -- otherwise it gives a similar error saying the password in not correct).

This is my first ever post to a linux forum -- I've looked around and was unable to find anyone with a similar problem -- I'm not *just* a horrible typer!  I am really tired of pulling my hair out over this -- Please help!

Sincerely,
outdoormonkey

---

### Post by dcstar on 2007-05-01
> **outdoormonkey said:**
> Hi all,

I'm new to the forums and feisty is my first foray into ubuntu and linux (except for some darwin experience).

I just installed feisty fawn for the first time on an older "mystery" box.   I used the alternate cd (verified the check sum and the cd integrity) since I don't think there's much ram.

Install is complete and at the loggin screen it says my user name or password is incorrect.
.......

When logged in as root, try:

```
passwd "user"
``` to reset the user password, and then see what happens.

---

### Post by outdoormonkey on 2007-05-01
no, that didn't help (i had already tried it) I've changed the password a couple of times now

unless I should be doing it somewhere other that in recovery mode

I guess I can do another install

I did find that I can startx from root (or sudo) in recovery mode.  It does not behave correctly, however.  And I still can't login from the login screen.

~om

---

### Post by Turellius on 2007-05-01
I am assuming you only have the user that was created during installation and the root user.  Have you tried logging in as root and creating a different user account and then trying to log in with that user?

---

### Post by outdoormonkey on 2007-05-01
from the login screen, it won't let me log in as root (says root cannot log in here, or something to that effect)

how can i create a new user in recovery mode?

---

### Post by Turellius on 2007-05-01
I haven't done this from terminal in awhile I think it's something to the effect of
```
user *username* passwd *password*
```

---

### Post by outdoormonkey on 2007-05-01
The full command is "adduser <username>" -- it has solved my problem.  I'm still baffled as to what caused the initial issue but I can log in now!

The only issue now is that the new user doesn't seem to have access to all of the administrative applications that I know should be there (users/groups, date and time); there are only 6 items in system>administration.  Is this a permissions problem?

How can I fix this w/o doing a clean install?

Thanks,
~om

---

### Post by Turellius on 2007-05-24
I don't know if this is still an issue, but if you are using the user you created with the "adduser" command then it is a rights issue.  By default when you create a user they are placed in the group that has the least permissions same as "users" group in Windows.  all you have to is add your user to admin group and problem should be solved.

---

