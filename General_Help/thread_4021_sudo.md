---
title: "sudo"
date: 2004-11-11
forum: General Help
---

### Post by BlackFenix on 2004-11-11
any user can use sudo ?

---

### Post by Slovak on 2004-11-11
As far as I can tell, yes, any regular user.

---

### Post by HungSquirrel on 2004-11-11
[QUOTE=Slovak]As far as I can tell, yes, any regular user.[/QUOTE]
 The user you created during the install is given sudo rights by default.  Subsequent users aren't.  I just added an alternate account with adduser to check this.  Full output:


```
esheldon@sage ~ $ sudo adduser
Enter a username to add: hungsquirrel
Adding user hungsquirrel...
Adding new group hungsquirrel (1001).
Adding new user hungsquirrel (1001) with group hungsquirrel.
Creating home directory /home/hungsquirrel.
Copying files from /etc/skel
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for hungsquirrel
Enter the new value, or press ENTER for the default
Adding user hungsquirrel...
Adding new group hungsquirrel (1001).
Adding new user hungsquirrel (1001) with group hungsquirrel.
Creating home directory /home/hungsquirrel.
Copying files from /etc/skel
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for hungsquirrel
Enter the new value, or press ENTER for the default
        Full Name []: 
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [y/N] y
esheldon@sage ~ $ su hungsquirrel
Password: 
hungsquirrel@sage:/home/esheldon $ sudo vi /etc/fstab
Password:
hungsquirrel is not in the sudoers file.  This incident will be reported.
```


In other words, there must be an entry in the /etc/sudoers file (which, for security reasons, must be read by root, i.e. by someone who already has permission to sudo).


```
# sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets

# User privilege specification
root	ALL=(ALL) ALL

# Added by Ubuntu installer
esheldon	ALL=(ALL) ALL
Defaults:esheldon timestamp_timeout=3
```

(I changed my timeout.  Default is 15 minutes I believe.)

---

### Post by jollyjoice on 2004-11-11
so how do i add sudo to an existing user?
I was completely stuped by this when I first started, and what is my root passwd ne way when i su it asks for one!

---

### Post by Rancoras on 2004-11-11
[QUOTE=jollyjoice]so how do i add sudo to an existing user?
I was completely stuped by this when I first started, and what is my root passwd ne way when i su it asks for one![/QUOTE]

You add the user you want to be able to sudo to the /etc/sudoers file.

---

### Post by HungSquirrel on 2004-11-13
> and what is my root passwd ne way when i su it asks for one!
The root account is prevented from logging in by default.  If you really want to enable root logins, do *sudo passwd root*.

---

### Post by TravisNewman on 2004-11-13
And in the sudoers file, just basically copy the line for the user that the Ubuntu CD set up and add in your other username. Do this for as many users as you want to be able to sudo. Keep in mind, you probably don't want your little 7 year old brother to be able to sudo, so be careful.

---

### Post by medicin on 2004-11-15
[QUOTE=HungSquirrel]The root account is prevented from logging in by default.  If you really want to enable root logins, do *sudo passwd root*.[/QUOTE]

WHY?

I have never encountered this before...

I am a grown up and found this feature to be big pain in the butt...

I'm curious to know what the rationale is for locking out the root account.

---

### Post by TravisNewman on 2004-11-15
[QUOTE=medicin]WHY?

I have never encountered this before...

I am a grown up and found this feature to be big pain in the butt...

I'm curious to know what the rationale is for locking out the root account.[/QUOTE]
 This wikipage describes it adequately:

[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

The sheer security and stablility, basically.

---

### Post by medicin on 2004-11-15
[QUOTE=panickedthumb]This wikipage describes it adequately:

[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

The sheer security and stablility, basically.[/QUOTE]



Okay...I went and read it...I have already encountered several instances where sudo didn't allow enough access (mounting a fat32 partition and configuring K3B and installing some necessary software)...I disagree with it in principle...

Sounds very Microsnot - like...

---

### Post by HungSquirrel on 2004-11-15
> Sounds very Microsnot - like...
No, Microsnot-like would be giving Admin rights to every account you add by default, then *not* asking for a password when installing software.  :-p

I too was skeptical at first, but because the root account is prevented from logging in, it is actually a fairly secure setup.

---

### Post by TravisNewman on 2004-11-15
[quoute] Sounds very Microsnot - like...[/quote]
Lets keep it clean guys. Not many people like Microsoft on these boards, but they still deserve the respect of keeping their name the same. We're not in 2nd grade anymore now.

As far as mounting a fat32 partition, I've done that easily with "sudo mount -[options] /dev/hdxx" and I've configured and used K3B without using the root account as well. 

This is not to say that I haven't had problems but whenever I did, I enabled the root account, did whatever I needed to do, then disabled it. It's an added layer of security, so it's worth 5 seconds more work for me

---

### Post by medicin on 2004-11-15
[QUOTE=panickedthumb][quoute] Sounds very Microsnot - like...
Lets keep it clean guys. Not many people like Microsoft on these boards, but they still deserve the respect of keeping their name the same. We're not in 2nd grade anymore now.

As far as mounting a fat32 partition, I've done that easily with "sudo mount -[options] /dev/hdxx" and I've configured and used K3B without using the root account as well. 

This is not to say that I haven't had problems but whenever I did, I enabled the root account, did whatever I needed to do, then disabled it. It's an added layer of security, so it's worth 5 seconds more work for me[/QUOTE]


It's actualy more "Apple-Like"  I guess,  than it is like that other OS that shall remain nameless...

---

