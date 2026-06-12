---
title: "Root password does not match"
date: 2014-01-18
forum: General Help
---

### Post by danny7 on 2014-01-18
I have a clean install of Ubuntu 13.latest on my moms system. I created a single account on it with one password as far as I can remember.
I'm now trying to install a few programs for her and I;m unable to do so. The system promps me to enter the root password which apparently I'm entering wrong. 

To log in to the system as the user, I am able to log in using the password I thought I had set as also the root password. 

I found [this ]("http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password")post but this looks like it would change the password for the user, not the root. I'm not sure if this is one in the same but if so, they I would be able to use the same password I used to log in to the desktop. 

I can I reset the password for root, would the post mentioned be my ticket?

---

### Post by deadflowr on 2014-01-18
There is no root password, or at least one enabled.
The first user you made should have the rights to run root tasks, if needed, using sudo.
The link you have is pretty much the right idea.

It would be a good idea to know if you belong to the admin/sudo groups, which allow you to run sudo commands.
you run
```
id usernamehere
```
and see if sudo or admin(NOT adm, that is a different group; it's for reading logfiles).

The link also has mention of running the mount command.
if the mount command in the first part doesn't work try the one later on
```
mount -o remount,rw /
```

Basically, though, follow the guide and you should be fine.

---

### Post by steeldriver on 2014-01-18
If you are being asked for root's password instead of your own (sudo) password, it may be because the gksu utility is not properly configured - run

```
gksu-properties
```

in a terminal and make sure the mode is set to **sudo **not **su**

---

### Post by tfrue on 2014-01-18
Read this article, this is the solution I know. Just be sure to follow it closely as you can really mess up your system.
[https://wiki.archlinux.org/index.php/Change_Root](https://wiki.archlinux.org/index.php/Change_Root)

---

### Post by deadflowr on 2014-01-18
Something else also, did you make the single account during the install, or after?

---

### Post by spencer the great on 2014-01-19
```
$ sudo passwd
[sudo] password for USERNAME:
Enter new UNIX password:
Retype new UNIX password:
```

The first line is asking to run the [FONT=courier new]passwd [/FONT]utility as root, which changes the password of the specified user (or, if no user is specified, like in this case, it changes your own password).  It normally asks for your current password before changing it, but this restriction doesn't apply to the root user.  That said, NEVER leave root logged in while you are away! root is the main admin account of the system and can change pretty much everything!

The second line is prompting you to enter your own password to gain root privileges in order to do this.
The third and fourth lines are for you to enter the new ROOT password.  
None of these passwords will show as you type them, not even in asterisks.

If you just want the graphical GUI to stop asking you for a root password, you want to follow steeldriver's solution.

> **tfrue said:**
> Read this article, this is the solution I know. Just be sure to follow it closely as you can really mess up your system.
[https://wiki.archlinux.org/index.php/Change_Root](https://wiki.archlinux.org/index.php/Change_Root)
No, not THAT root. You're thinking about the root directory. This has nothing to do with that.

---

### Post by lisati on 2014-01-19
You might also like to take a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by danny7 on 2014-01-30
Been a bit busy but I thank you guys for all the input. 

Ok so here's what I got so far: I restarted the system and dropped in to the terminal, then:

```
[COLOR=#404040][FONT=arial]mount -rw -o remount /[/FONT][/COLOR]
```

then I looked up the user name

```
ls /home
helena
```

finally

```
passwd helena
```

the password was successfully changed.  

Booted into the desktop, tried to install and app, entered the password and still not allowing me to make changes. 

Opened the terminal and

```
gksu-properties
[FONT=arial][COLOR=#404040]The program 'gksu-propersties' is not currently installed. You can install it using the following command(...)[/COLOR][/FONT]
```[FONT=arial][COLOR=#404040]
[/COLOR][/FONT]
Which I enter but cannot execute
```
 sudo apt-get install libgksu-0 
(...)
helena is not in the sudoers file. This incident will be reported.
```

---

### Post by mayagrafix on 2014-01-30
> helena is not in the sudoers file. [B]This incident will be reported.
[/B]
sounds like one of those snarky OpenSuse OS remarks...

---

### Post by danny7 on 2014-01-30
Thank for ruining it, I will forever read that in Hals voice now.

---

### Post by steeldriver on 2014-01-30
have a look here --> [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by jeanjd63 on 2014-01-30
Hello 
You do as in the post #8 then you do :
[B]adduser [COLOR=#000000][FONT=Ubuntu Mono]helena sudo
[/FONT][/COLOR]**adduser **[COLOR=#000000][FONT=Ubuntu Mono]helena[/FONT][/COLOR][B]  adm
adduser [/B][COLOR=#000000][FONT=Ubuntu Mono]helena[/FONT][/COLOR][B]  lpadmin
adduser [/B][COLOR=#000000][FONT=Ubuntu Mono]helena[/FONT][/COLOR][B]  sambashare
[/B][/B]Then you reboot

---

### Post by danny7 on 2014-01-30
adduser:  /usrbin/gpasswd -a helena sudo' returned error code 1. Exixting.

The group 'adm' already exists 

'helena' is already a member of 'lpadmin'

'helena' is already a member of 'sambashare'

:|

---

### Post by danny7 on 2014-01-30
Thank you stelldriver

I entered
```
adduser helena admin
``` 

rebooted and voila, installing packages as we speak :)

And thank you everyone who posted.

---

