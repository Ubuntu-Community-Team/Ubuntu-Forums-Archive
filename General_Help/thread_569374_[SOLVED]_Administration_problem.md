---
title: "[SOLVED] Administration problem"
date: 2007-10-07
forum: General Help
---

### Post by Niniel on 2007-10-07
Hello,

After I installed the last Ubuntu 7.10 beta from the live CD, I took a look at the users and saw that the user I had created during installation, the one I intend to log in as, had all the rights. So I took admin rights away and gave them to the root user, who was listed as not having any rights at all (which I found weird, I thought root was the admin)
Now however, I have the problem that some admin tasks require a password. The password that I enter is being rejected though. I am certain I've been entering the password I set for root, but it just isn't working. When I change user and try to log in as root, that password gives me the error message that root cannot log in that way (funny too - how *is* root supposed to log in???) so I know it's correct. 

Is there a way to fix this?

---

### Post by taurus on 2007-10-07
Not sure exact why you would change anything on your machine because root account is locked as a default.  And by the why, root doesn't have to belong to groups adm and admin to access /!  

You need to boot into recovery mode from GRUB menu and edit /etc/group

```
nano -B /etc/group
```
and add your username to groups adm and admin.  Save it with <Ctrl>o and exit with <Ctrl>x.  

Then reboot.

```
shutdown -r now
```

---

### Post by Niniel on 2007-10-07
That editor looks like the good old Pine... :)
Anyway, thank you, that worked.

So what's the difference between "root" and admin-enabled desktop user? 

This was also pretty strange - even with my freshly re-enabled account I am asked to put in a password for some administration task. But the system won't accept the password of the "root" user, it only likes the one for my account.

---

### Post by anaconda on 2007-10-07
well.. I wouldn't have edited the group file manually.. just using adduser -command would have been simpler, (but whatever works..)

adduser your_username admin

and the difference. admin-enabled user is constantly asked for the sudo password. Root doesnt have to do that.

and if you want to really enable root user you have to give root a password, and then enable graphical root login from System>Administration>login window

and sudo uses your password, because it is you who has the right to use sudo. IF you have given root a password then su would ask that password (same result as sudo su would give.)

---

### Post by Niniel on 2007-10-07
Hm, I had been under the impression that normal users shouldn't be able to administer the system, that one should use "root" for that. Or is that admin vs. user concept just a Windows thing? Maybe this question is better suited for the "Absolute Beginners" section... :)

Apart from being asked the password all the time, is there any other difference between admin user and root? 
And I still don't understand why the root password wouldn't' work (I set one, but didn't enable graphical login). I thought "root" can do anything and everything.

---

### Post by anaconda on 2007-10-07
Normal users cant administer the system. But users who belong to admin group are administrators.. And the first user you make belongs to admin automatically.

Does the root password work if you type (in terminal)
su

That changes the current user to root. (if root has a password)

And this is not the linux way.. Most linuxes have root user. it is more like ubuntus way. And it is like this for improved security. If you dont like it you can enable root -user, just by giving root a password and enabling graphical root logins..

---

### Post by Niniel on 2007-10-07
Security? How is this more secure? 
I guess it all comes back to the difference between root and admin. There must be something more, or else I don't see how making the first user admin is going to help much.

So if I understand you correctly, root's password won't do anything until I also enable the graphical login?

---

### Post by Celegorm on 2007-10-07
Basically, if you log in as root, everything you do is done as root. If you are logged in as an administrator, you have to specifically ask to run something as root by typing your password in a popup window or using sudo. Running as an administrator is much safer.

For example, if you forget you are in the root directory and execute a command in the terminal which removes everything in the current directory, if you are root you just borked you entire system and will have to reinstall. If you are running as an administrator, you will probably just kill your home directory, which is quite bad, but if you are not the only user on the system or have important files in other locations than your home directory, it is quite a lot less bad than if you had been root. Well, bit of a clunky example, but I can't think of anything better at the moment.

---

### Post by Niniel on 2007-10-07
Ok, thanks, that makes some sense.

Do I have to be in the admin group for this to work, or will any user be able to execute "sudo" commands?

---

### Post by anaconda on 2007-10-07
Yes, you have to be in the admin group for it to work..

---

### Post by Niniel on 2007-10-07
Excellent. Thank you for explaining this to me.

---

