---
title: "Log-In Drama"
date: 2007-11-08
forum: General Help
---

### Post by ubuntist! on 2007-11-08
Ok, so I've never had much luck with Linux. Fortunately, Ubuntu has been an exception! It was relatively easy to install, and it's been working just fine up until today. But... SOMEHOW I've found a way to ruin it, haha!

I'm having a problem with logging in. It's self-inflicted, though. What I did was jump in and tamper with the User and Group settings, changing the username and directory of my only account:

home/[newusername]

But I forgot that the directory I specified doesn't exist yet. So now, when I try to log in using my new user name, I get an error telling me that I cannot login to my directory, and asking me if I would like to login using the root directory instead. I click yes; it logs me in; but instantaneously I get a dialogue box telling me that my session has lasted for less than ten seconds, before promptly bringing me back to the login screen. :(

I have tried logging in under the root account, but to no avail. 

Thankyou in advance for any help or advice.

---

### Post by vambo on 2007-11-08
Go into failsafe mode and create a directory that is your new user_name

```
mkdir /home/newusername
```

Then change the ownership to the new user
```
chown newusername /home/newusername
```

Note: This is assuming that you created the new user via users/groups or adduser

---

### Post by llamakc on 2007-11-08
EDIT: Tee hee. I'm slow. The post above works as well, but I hate rebooting.

Try this.

Press these keys:

```

ctrl-alt-F2

```Now login with your username. Any error it spits out, please post it here.

Next do this:

```

cd /home && ls

```From the /home directory (where you will be if you followed the directions) you can CREATE the directory you need to. But first let's figure out what you changed. So do this:

```

cat /etc/passwd | grep USERNAME

```You need to substitute YOUR username where I wrote USERNAME. For example if I do this, it looks like the below.

```

ken@llamakc 04:50:55:~$ cat /etc/passwd | grep ken
ken:x:1000:1000:Ken clark,,,:/home/ken:/bin/bash

```The field we are interested in is the one "/home/USERNAME" which in my case is /home/ken.

Before you screwed it up, it would have said /home/USERNAME instead of /home/WHATYOUCHANGED_IT_TO

So, one temporary fix to allow you to log back into X and GNOME is to do this:

```

sudo mkdir /home/WHATYOUCHANGED_IT_TO

sudo chown USERNAME:USERNAME /home/WHATYOUCHANGED_IT_TO


```Now either type "sudo reboot" or logout of the console.

```

logout

```If you've logged out, go back to the GDM login manager by pressing:

```

ctrl-alt-F7 (or F8. I forget what Ubuntu is using these days).

```If that doesn't work you can move horizontally along the consoles & F# keys to find the one with the login manager.

Try logging in again.

Next time just create a new user.

---

