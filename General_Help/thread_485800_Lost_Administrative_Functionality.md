---
title: "Lost Administrative Functionality"
date: 2007-06-27
forum: General Help
---

### Post by dlebowski on 2007-06-27
Hello.  I have been using Ubuntu for a couple of months and recently ran into a situation where I lost most of my Administrative options.  I am not sure if something is broke, or if I did something to lose them.  The two biggies are Synaptic Package Manager and the Users/Groups option.  They just simply are not in the drop down any longer when I go into the "Administration".

The two things I did prior to losing those options.  I installed Wine and I assigned my user account to the "root" group.  Would anyone know if either one of those may have caused the problem?  Any help would be appreciated.  Thanks!

Ryan

---

### Post by dreadlord_chris on 2007-06-27
Honestly, I don't **know** why your admin stuff won't work, **but** you should **not** be part of the root group - only the *root* user account should be part of that group:
```

deluser NAME root

```
replace NAME with your user name. You might have to log off & back on for the changes to take effect.

btw... why **did** you add yourself to the root group? What were you trying to do?

---

### Post by dlebowski on 2007-06-27
Thanks for the quick response.  I am still learning Linux so you will have to forgive me.  

I was trying to run SQLyog using Wine.  I could only run it as Root from the command line.  I could not run it from my user account.  So in an attempt to fix the problem, I assigned my user account to the root group (apparently this was not a good idea).  What I later found out was that I should have installed SQLyog from my user account instead of root and that may fix my inability to run the program from my user account.  

I will do what you suggested and remove the root group and then log out and back in again to see if they return.  Thanks again.

-Ryan

---

### Post by dreadlord_chris on 2007-06-27
heh... no problem...
and, from now on - when you need to run something as root - use **sudo**
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dlebowski on 2007-06-27
Will do.  

One last question, can I create a launcher on the desktop in Ubuntu using sudo?  For example, I can run Wine apps from the command line using.  

```
wine ".wine/c_drive/Program Files/Sqlyog/Sqlyog.exe"
```

If I am logged in as root.  If I wanted to create a shortcut for that on the desktop in Ubuntu, how would I apply sudo to it?  Thanks again.

Ryan

---

### Post by dreadlord_chris on 2007-06-27
> **dlebowski said:**
> Will do.  

One last question, can I create a launcher on the desktop in Ubuntu using sudo?  For example, I can run Wine apps from the command line using.  

```
wine ".wine/c_drive/Program Files/Sqlyog/Sqlyog.exe"
```

If I am logged in as root.  If I wanted to create a shortcut for that on the desktop in Ubuntu, how would I apply sudo to it?  Thanks again.

Ryan

for graphical programs you should use **gksudo** (or kdesu if you are using KDE) rather then **sudo**
this explains the difference: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To creat a shortcut that runs with admin privilages - just add **gksudo** before the command name in the launcher properties.

---

### Post by dlebowski on 2007-06-27
OK.  I am still having a problem.  I completely removed the user that I assigned to the root group.  I added a new user all together that is NOT assigned root and i still only see Keyring Manger, Network Tools, Printing, System Lot, System Monitor, and Update Manger when I go into System>Administration.  Everything else is gone. Does anyone have any other suggestions for me?  Any help at all would be great.  Thanks.

Ryan

---

### Post by dlebowski on 2007-06-27
I hate to bump, but I am going to.   I have to rebuild this shortly if I can't figure this one out.

---

### Post by dreadlord_chris on 2007-06-27
> **dlebowski said:**
> OK.  I am still having a problem.  I completely removed the user that I assigned to the root group.  I added a new user all together that is NOT assigned root and i still only see Keyring Manger, Network Tools, Printing, System Lot, System Monitor, and Update Manger when I go into System>Administration.  Everything else is gone. Does anyone have any other suggestions for me?  Any help at all would be great.  Thanks.

Ryan

did you add the user to the admin group?
```

sudo usermod -a -G admin NAME

```
replace NAME with the login name

Actually, I'm really not sure that is going to add any more icons in your Admin menu.

Have you tried right-clicking the menu and choosing **Edit Menu**? From there you add the apps that have dissapeared.

---

### Post by dlebowski on 2007-06-27
That was it.  You have to be in the admin group.  Not only that, but you can also right click on the system menu to add them as well if you are assigned to the admin group.  Thanks for you help man.

Ryan

---

### Post by dreadlord_chris on 2007-06-28
No problem.... glad it got worked out...

---

### Post by estron on 2007-07-02
I have the same issue where the admin stuff doesn't show up under a logged in user.  There is a difference though.  This user is logged in via winbind using domain credentials.  They do show up as their user name under top as running processes however as root I am unable to add these users to admin.  What I'd like to do is add domain admins group to the admin group on the local machine.  I have got it set up so they can sudo but they cannot see most of the administration options under the system menu.

Example:
root@Ubuntu-01:~# usermod -g admin bpickhardt
usermod: bpickhardt not found in /etc/passwd

however I know that user is logged in because I can see they are running a shell.
root@Ubuntu-01:~# top -U bpickhardt | grep bash
 7298 bpickhar  22   0  5936 3500 1504 S    0  0.2   0:00.19 bash                                                                                            
 8204 bpickhar  15   0  5872 3384 1460 S    0  0.2   0:00.12 bash 

Any ideas?  the user bpickhardt is a member of the Domain Admins group.  This user can run sudo commands from this machine.

bpickhardt@Ubuntu-01:~$ sudo echo "I HAVE THE POWER"
Password:
I HAVE THE POWER

---

