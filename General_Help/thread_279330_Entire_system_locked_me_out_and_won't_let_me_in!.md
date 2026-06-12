---
title: "Entire system locked me out and won't let me in!"
date: 2006-10-17
forum: General Help
---

### Post by pentium on 2006-10-17
The other evening I booted up the system and when I went to go check the device manager I discovered in the administration that most if not all of my tools were gone. I then loaded root terminal so I could try something and it rejected my password! I have lost all admin rights and this has effectively shut me down.  I tried booting in recovery mode and entering "passwd master" and then rebooting like someone told me to do and that did nothing.
The only thing I have done ery recently was create a new user for a short period so I could test a theory with appletalk and then later remove it.
I also recently installed a new nvidia driver that I was told "not to use if I have wireless" hich I don't have.
Either I screwed my user setup over or someone has locked me out.
I have work to be done and this is not good.
I need help!

---

### Post by Iowan on 2006-10-17
Can you boot from the LiveCD?

---

### Post by pentium on 2006-10-17
of course. Why?

---

### Post by RSL on 2006-10-17
Are/were you using Edgy? I know that a lot of very, very useful programs get autoremove'd sometimes. They get replaced but not right away sometimes. Can be trouble.

---

### Post by pentium on 2006-10-17
What's edgy?

---

### Post by pentium on 2006-10-17
UPDATE!
I can now get into my root account but only in command line.
How can I edit my graphical profile? that's the one I always use (including right now) and the one which had virtually all rights (I still had to enter a password for some programs though).

---

### Post by Iowan on 2006-10-17
> **pentium said:**
> of course. Why?
[http://www.ubuntuforums.org/showthread.php?t=149166&highlight=live+CD]("http://www.ubuntuforums.org/showthread.php?t=149166&highlight=live+CD")

---

### Post by pentium on 2006-10-17
okay.
I know my user password now and I know my root password now.
The thing is, the system is still rejecting the password for programs that need prompt for it.
even in terminal, going "sudo user-admin" and entering the password gives me nothing. I a also gettng ticked off on how it is taking forever to logout/shutdown.

---

### Post by pentium on 2006-10-17
hmmm...
The slow shutdown problem is gone.

also, root terminal gave me this:
```
Failed to run /usr/bin/x-terminal-emulator

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
```

---

### Post by pentium on 2006-10-18
I'm still locked out.

---

### Post by pentium on 2006-10-19
Anyone?

---

### Post by metalheart on 2006-10-19
Type ```
sudo -i
``` Now try to run your program again.

---

### Post by pentium on 2006-10-19
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

Again, it does nothing:

```
pentium@ubuntu:~$ sudo -i user-admin
pentium@ubuntu:~$

```
-no program
-no mesages
-nothing!
This is really ticking me off now.

What next? full reinstall?!

This is worse than windows!

---

### Post by metalheart on 2006-10-20
Just do

```
sudo -i
```

You get root prompt.

For changing password use

```
passwd *username*
```

For adding user use

```
useradd *username*
```

For removing user use

```
userdel *username*
```

What is what you want to do with the user?

---

### Post by pentium on 2006-10-20
> What is what you want to do with the user?
I assume you made a typo and you were actually asking what  wanted to do with the user.

Well, for some strange reason, I lost my admin rights. I m also the only user (excluding root) on this system and right now I just want to get unto he user editor control panel.

I don't need to change my passwords also, I know them and they work in command mode. I'll try creating a new user.

---

### Post by pentium on 2006-10-20
The system spews me errors that directories do not exist when I create a new user and log in has him.
Changing the password still has no effect outside of command line.

---

### Post by yota on 2006-10-20
> 
What next? full reinstall?!

This is worse than windows!


Hi, please be patient, this is much better than windows and we'll sort this thing out!
First: a user can elevate its privileges if he's part of the admin group, so let's state if your user is no more on the admin group.
Login as root and:
```

id *your_username*

```
if "admin" is not on the list, we have to add it with 'usermod -G' (we'll se later, eventually) or by manually editing /etc/groups

Second: if you create a new user the home directory is made only if you use 'useradd -m -k' and that explains why the system complains about non-existing paths; by the way a new user is not an admin by default and so it will not solve your problem.

Please look at 'id' output and let us know, we'll move to the solution soon, hopefully.

---

### Post by PittNsciGuy on 2006-10-20
Hey, sorry I won't be of much technical help, but I did have a very similar thing happen to me a few months back!  I lost all privilages, and the system refused to recognize my account at all!  I had to create a new user in terminal, give the new user full admin privilages, and then use the new user to restore all of my old privilages (all of my normal user files were present, just deactivated for some reason)  It was all very strange, nothing was working, and then suddenly everything seemed to fix itself!  Dunno if any of that is usefule, but either way, best of luck getting this thing worked out!!

---

### Post by pentium on 2006-10-20
This don't look right:
```
uid=1000(pentium) gid=1000(pentium) groups=1000(pentium)
```
I see no mention of root at all.:D

---

### Post by dannyboy79 on 2006-10-20
> **pentium said:**
> This don't look right:
```
uid=1000(pentium) gid=1000(pentium) groups=1000(pentium)
```
I see no mention of root at all.:D



1000 is the uid of the first user created. It looks perfectly correct to me. I don't know what root's uid is but I know for sure that the first user, which is what you use to log in to Ubuntu, is 1000. Have you tried doing "passwd root" THen you'll type in roots password twice, now that is root's password. I am not sure how you make it so you can log in as root though. I know it's off by default in Ubuntu. I wish I could help more. Good luck

---

### Post by pentium on 2006-10-20
> I don't know what root's uid is but I know for sure that the first user,
that would be 0

also... passwd root did nothing.

---

### Post by metalheart on 2006-10-20
Can you log in as root with

```
sudo -i
```

Give password and the prompt changes to

```
root@ubuntu:~#
```

---

### Post by yota on 2006-10-20
> 
This don't look right:
Code:
uid=1000(pentium) gid=1000(pentium) groups=1000(pentium)
I see no mention of root at all.


indeed this IS the problem: as said before you user is not an admin and so can not use sudo and run applications that need elevated privileges.

A standard right-after-install user woul look somethnig like this:
> 
yota@one:~$ id yota
uid=1000(yota) gid=1000(yota) gruppi=1000(yota),**4(adm)**,20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),60(games),106(lpadmin),110(scanner),**112(admin)**,1005(share)


to restore missing groups do this as root:
```

usermod -G adm,admin pentium

```
that's the minimum to regain sudoers ability, then add other groups as needed, eventually from users-admin's gui.

---

### Post by dannyboy79 on 2006-10-20
for a full recovery of sudo, check this out, it's the answer for sure.
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo).
you need to log into recovery mode and update 2 file, /etc/sudoers and /etc/groups. I think, it goes step by step at the link

---

### Post by pentium on 2006-10-20
> to restore missing groups do this as root:
Code:

usermod -G adm,admin pentium

that's the minimum to regain sudoers ability, then add other groups as needed, eventually from users-admin's gui.
Reply With Quote

I love you! it worked!

I have all my rights I needed back. Now how do I get all my control panels back. under the sdministartain tab I only have:
 
-device manager
-Networking tools
-printing
-system log
-system monitor

The menu editor says they are enabled but they ain't there.
once i can get them back, I can return to fixing another problem.

---

### Post by pentium on 2006-10-21
A restart repopulated my administration menu and my sound came back onnline, eliminating a need to get more help in another forum.
Thanks all.

---

