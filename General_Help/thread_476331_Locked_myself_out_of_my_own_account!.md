---
title: "Locked myself out of my own account!"
date: 2007-06-17
forum: General Help
---

### Post by DeeWox on 2007-06-17
Well... I thought my first post would be about something other than this... :p

As the title describe I have locked myself out of my own account by changing some permissions/rights. Luckily i have two accounts on this computer, so I'm not that screwed, but how do I fix this?

The error messages I get refers to the .ICEauthority file. The system can't read it because it don't have the rights to read it...

I have tried to get in with the failsafe function (if it's called that), but I still can't get into my account.

Please help me in a way I can understand. I'm very new to Linux! (I think you figured that out by now) ;)

---

### Post by marshall.robert on 2007-06-17
have you tired using your root account?

---

### Post by DeeWox on 2007-06-17
> **marshall.robert said:**
> have you tired using your root account?
Do you mean to change the permissions? No, I can't the command lines for that...
Please explain what I have to do, step by step.

As I said before: I'm new to Linux...

Sorry... :(

---

### Post by marshall.robert on 2007-06-17
well. the root account is the ulitmate account that can do everything and anything to the system, similar to the hidden administrator in windows xp, but much better. if you installed this from disc then the root password may be the same as the one for the account you set up at install time, but it doesnt do it sometimes. the catch is that you have to tell the logon screen to let the root account log on. this can be done like this:
1. go System -> Administration -> Users and Groups.
2. it should ask you for a password to do administrative tasks
3. on successfully entering the password you will see the User Settings window, this will list all; the users on your system
4. pick the account named 'root' and then click Properties
5. Where it has the headding 'Password' set the password by hand to somehting you desire
6. next go to System -> Administration -> Login Window (you may or may not be asked for a password)
7. go to the Security tab and tick the box labeled 'Allow local system administrator login'
8. close and logout and then you shout be able to log in as root

i hope that works for you, its the first thing i do when setting up a new install so if anything does go tits up i can fix it.

---

### Post by DeeWox on 2007-06-17
Okay, now I'm logged in as root. I can now access all the files on my messed up account. Is the solution to delete the .ICEauthority file, or...?

---

### Post by marshall.robert on 2007-06-17
sorry. this is where i become useless, for i am relatively new on linux, i have only just got it working so i can use it full time.

but ill give it a try. what exactly did you do?

i wouldnt delete that file, usually anything with a full stop infront of it is important.

---

### Post by DeeWox on 2007-06-17
What I did to mess it up? I think I changed some user rights or something. The error message I get says that it can't lock .ICEauthority... I can take a picture of the error message.

EDIT: The error message said it couldn't LOCK (not unlock) the .ICEauthority file.

---

### Post by miLl3niUm on 2007-06-17
Maybe backup your stuff and format?

---

### Post by marshall.robert on 2007-06-17
well, backup and format is the easiest option, also its a bit of a copout and you have to set everything up all over again, if you could post a picture that could be helpful, and ill see what i can think of.

---

### Post by DeeWox on 2007-06-17
Here is the picture!

---

### Post by DeeWox on 2007-06-17
> **marshall.robert said:**
> well, backup and format is the easiest option, also its a bit of a copout and you have to set everything up all over again, if you could post a picture that could be helpful, and ill see what i can think of.

I won't format because it's only my user account which is messed up. It's my mom computer and her user account is working fine, so it's not necessary to reformat the whole thing.

---

### Post by happy-and-lost on 2007-06-17
If it's a Gnome problem, press <Ctrl><Alt><F1> and log into a terminal. Now *rm -f .ICEauthority*. If that doesn't work try *sudo rm -f .ICEauthority*

I've never encountered any ill effects of deleting that file. Gnome will generate a new one on next login.

---

### Post by DeeWox on 2007-06-17
> **happy-and-lost said:**
> If it's a Gnome problem, press <Ctrl><Alt><F1> and log into a terminal. Now *rm -f .ICEauthority*. If that doesn't work try *sudo rm -f .ICEauthority*

I've never encountered any ill effects of deleting that file. Gnome will generate a new one on next login.
I'm sorry this didn't work, but I found the solution!

As you can see on the picture, I changed the rights on my home folder from "access files" to "Create and delete files". Then I was able to log into my account again!

This is was I did, step by step:
1. Logged into the root user
2. Went to "computer" -> "filesystem" -> "home"
3. Then I right clicked -> properties ->  permissions
4. Changed the permission of the home folder, so that my account can create and delete files instead of just accessing them.

Thank you all for your time and help!

---

### Post by Ocxic on 2007-06-17
remove the entry for th file it in "/var/run/lock"  that should get you goin again.

if that doesnpt work, delete the file from your home directory, gnome will make a new one

---

### Post by DeeWox on 2007-06-17
> **Ocxic said:**
> remove the entry for th file it in "/var/run/lock"  that should get you goin again.

if that doesnpt work, delete the file from your home directory, gnome will make a new one
No need to. I found a solution to my problem, see the post above yours!

---

