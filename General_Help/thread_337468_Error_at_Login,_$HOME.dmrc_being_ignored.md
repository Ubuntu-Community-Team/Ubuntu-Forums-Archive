---
title: "Error at Login, $HOME/.dmrc being ignored"
date: 2007-01-13
forum: General Help
---

### Post by abzolutxero on 2007-01-13
I was trying to adjust some file permissions on some direcotries that WINE installed, and now i recieve the following dialog box:

"User's $HOME/.dmrc fule is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writeable by other users"

i only have one user on my system, and as far as i can tell, the HOME directory is only owned and writable by the only user on the system.  I went back and tried to adjust permissions, but everything either seemed to be in place, or were not visible at first.

1) Do I / Is there a way to login as root in file browser to edit permissions? or how do i do so in terminal?

2) What do i need to do to resolve this issue?  i cant exactly tell what file is in the wrong....

Thanks so much,

Brad

---

### Post by netadptr0719 on 2007-01-13
when I had this problem I did 
```

sudo chmod 700 (home folder here)

```
and it solved the problem.

---

### Post by aidanr on 2007-01-13
> **abzolutxero said:**
> "User's $HOME/.dmrc fule is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writeable by other users"

in a terminal

sudo chown -R Brad /home/Brad
sudo chgrp -R Brad /home/Brad
sudo chmod -R 755 /home/Brad
sudo chmod 644 $HOME/.dmrc

if Brad isn't your username substitute whatever is

---

### Post by abzolutxero on 2007-01-13
actually,

sudo chmod 700 (home folder here)

did the trick, thanks for the help!!



edit--- oh, and why did that work?  i want to learn something from this, instead of just taking someone else's advice blindly.  The dialog to chmod the specific file to 644, yet, chmod 700 worked on the whole folder to fix the problem.

---

### Post by commonplace on 2007-01-16
sudo chmod 700 <home folder> worked for me, too, after I screwed up permissions on my wife's laptop. Thanks!

/Kevin

---

### Post by beanco on 2007-01-19
I too tried the chmod 700 option and it worked.

I have no idea why and I would love to know what it is i did...

please tell me..

robi

---

### Post by dhughes on 2007-01-21
I managed to get this message too whenever I would log into my account. I think I screwed up permissions when I tried to make my account unreadable to any other users, I have an account for my parents but I didn't want them to be able to see my files from their account.

 Anyway I did exactly what the error message told me to do, I had to make my home folder's .dmrc file have permission 644 (I can read and write, for others and group is read only): ```
sudo chmod 644 /home/dhughes/.dmrc
```

 Then also as root I changed my home folder's permission's so other's couldn't have write permission: ```
sudo chmod 744 /home/dhughes
```

 It was interesting when I changed my home folder to read and write but not execute and was kicked out after less than ten seconds, so I went into Recovery Mode and that's when I changed my home folder's permissions to 744.

---

### Post by ricardisimo on 2007-01-25
Same warning here, and hopefully the same solution (we'll see). Just curious: What do those numbers represent? 644, 700, 744, 755, and/or any others? Thanks.

---

### Post by Eternal_Nyt on 2007-01-30
***[FONT="Book Antiqua"]Same Issue Here[/FONT]***

Still Having Login Issiues
Was trying to fix two previous users to be able to access from GDM and Now i some how knocked out the Main User with same Error Message.

im getting can not access or not found.
when i have tried these commands

sudo chown -R me /home/me
sudo chgrp -R me /home/me
sudo chmod -R 755 /home/me
sudo chmod 644 $HOME/.dmrc

also have tried 
sudo chmod 700 home

and still same Error.

Im Using Edgy latest release.
any ideas or at least a walk though on getting a new user from terminal?
thanks

---

### Post by Maestro23 on 2007-01-30
> **ricardisimo said:**
> Same warning here, and hopefully the same solution (we'll see). Just curious: What do those numbers represent? 644, 700, 744, 755, and/or any others? Thanks.

This link explains linux file permissions: [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by carverj on 2007-02-06
These options will not work for myself as I managed to format /home partition.
Is there any way for me to change the configuration of my login to allow me to access Ubuntu ?
I hope someone comes to my aid quickly before I screw this up more
Thanks all

---

### Post by &amp;wi*m#~10+q on 2007-02-10
> **netadptr0719 said:**
> when I had this problem I did 
```

sudo chmod 700 (home folder here)

```
and it solved the problem.

thanx :)

---

### Post by cybrkup on 2007-02-14
Thank GOD for this command! I just locked my wife out of her account and I couldn't access the files myself. I was really beginning to sweat.

:)

---

### Post by Eriksmits596 on 2007-09-09
But it didn't works for me:( Do I need to log in as root when I do this?

---

### Post by Eriksmits596 on 2007-09-09
NOW IT WORKS!!! Thanks everybody:)

---

### Post by quantboy on 2007-11-24
Thanks- these types of non-sensical problems really turn off newbies.

---

### Post by BoardDWorld on 2007-11-29
> **aidanr said:**
> in a terminal

sudo chown -R Brad /home/Brad
sudo chgrp -R Brad /home/Brad
sudo chmod -R 755 /home/Brad
sudo chmod 644 $HOME/.dmrc

if Brad isn't your username substitute whatever is

Thank you for your detailed fix, it's actually close to being the most correct on Ubuntu. The reason many weren't able to make use of it is because you forgot to put Brad between $HOME/ and .dmrc

---

### Post by bobdebouwer on 2008-01-20
> **netadptr0719 said:**
> when I had this problem I did 
```

sudo chmod 700 (home folder here)

```
and it solved the problem.

this actually fixed my problem too. Not sure what version everyone else is using but im on gutsy (7.10)

all I did was "sudo chmod 700 $home"

thanks guys was a bit annoying after a few days of installing programs. Still kinda new back to linux after a few years absence.

---

### Post by steveneddy on 2008-01-20
You know, this happened to me this weekend and I noticed an over abundance of these types of posts on the forums today.

Wonder what may be going on?

Mine came about as a result of trying to get WINE running.

I finally un-installed it and ran into this issue.

strange.....

---

### Post by bobdebouwer on 2008-01-21
thats pretty similar to what i was experiencing. had been messing around with wine and installing ntfs-3g for my windows drives then that happened.

---

### Post by bconover on 2008-06-07
I did this.

Now, when I try to log in, it says my home directory isn't there. When I try to then log in as root, my session ends after 10 seconds.

Tried fixing this in Recovery mode, did the everyting here, nothing worked.

Perfect, now I cant use my computer.

---

### Post by bconover on 2008-06-07
Seriously, I need t oknow what t odo, so please, any help at all. I really need my computer and the files on it.

---

### Post by carlosprite on 2008-06-09
try opening up a text based session. the way you can do this is by (at the login screen) pressing <ctrl>+<alt>+<F1>. 

Login as root

rerun the commands listed in previous posts :)

to get back to the GUI use <ctrl>+<alt>+<F7>

---

### Post by mlnease on 2008-06-13
AidanR,

Thanks a million!

mike

---

### Post by mlnease on 2008-06-13
> **bconover said:**
> Seriously, I need t oknow what t odo, so please, any help at all. I really need my computer and the files on it.

See [http://ubuntuforums.org/showpost.php?p=2006381&postcount=3](http://ubuntuforums.org/showpost.php?p=2006381&postcount=3)
It worked for me.  Good luck!

---

### Post by raydar on 2008-06-14
I got this error a completely different way, and resolved it a different way too:

I have one drive with UbuntuStudio 7.10 and one with UbuntuStudio 8.04 in the same machine.  There's stuff I left on the desktop of my 7.10 drive and want to access from 8.04, so for convenience, in 8.04 I tried making a shortcut to my Desktop folder on the 7.10 drive, but I can't open that folder with it unless I first navigate there through the Places menu--permissions thing, right?  

So while running 8.04, I changed the permissions on the 7.10 drive's Desktop folder so others could read & write to it. I then logged out & back in, got the error message that's the subject of this thread, and rebooted & got the same message. Then I found this thread.

I held off on executing the suggested chmod commands, because it seemed fishy that I changed permissions on a non-active partition's *Desktop* folder but got an error message mentioning the active partition's *home* folder (unless there's something to the fact the name of the account is the same on both drives). 

I finally noticed the last part of the error message this thread is about, where it says a home folder shouldn't be read/write-able by anyone but the user. I tried booting into 7.10 to see what would happen, and I got no error message at all (even though that's the drive whose permissions I'd changed).

So instead of issuing the chmod command, I booted the 8.04 drive and changed the 7.10 drive Desktop folder's permissions back to Access Files for all but the user.  I logged out & back in, got a different error saying something was wrong with bonobo & nautilus, and then rebooted, and now no longer get the error this thread is about.

Anyone interested enough to speculate why I got, this way, the same error message you all got?  

Maybe folks who the chmod commands haven't worked for could try changing permissions in the gui instead . . . ?

---

