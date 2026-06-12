---
title: "Useradd doesn't work"
date: 2007-06-20
forum: General Help
---

### Post by cefn on 2007-06-20
Surely this should be impossible?

$ sudo /usr/sbin/useradd -m david
$ passwd david
passwd: unknown user david
$ grep david /etc/passwd
$

Seems that useradd doesn't do anything at all. Perhaps I'm confused somehow how to use it, but I think it's just busted.

I'm running Ubuntu Feisty Fawn and there's no feedback from useradd at all, and it does nothing. Passwd contains no reference to the new user created. I don't believe there's anything strange about my user account.

As a workaround, perhaps someone can point out how Ubuntu's desktop user management tool get's launched if that's really the only way to set up users now. All the helpful guides say - go to the menu and click on...I don't have access to the desktop - it's a server.

Taken in concert with [this kind of error]("http://cefn.com/blog/ubuntutomcat.html") which is very similar - a fundamentally broken package in a stable branch, Im seriously considering going back to debian for server builds, although I've found Ubuntu to be great for multimedia desktops.

Cefn
[http://cefn.com/blog/](http://cefn.com/blog/)

---

### Post by itsalmostreal on 2007-06-20
try:

sudo useradd -m david

im pretty sure you dont need the path you had in there...

---

### Post by cefn on 2007-06-20
The path's not required, but doesn't make any difference either way.

---

### Post by itsalmostreal on 2007-06-20
well something is messed up with your sytem then. im running 7.04 server as well, and useradd works perfectly.

check your passwd file to see if the user you tried to add is there: sudo nano /etc/passwd

i wouldnt edit that file tho...

---

### Post by cefn on 2007-06-20
I've worked out what the issue is.I tried to set my membership of a new user group...

usermod -G thegroupname myusername

...which should have been...

usermod -Ga thegroupname myusername

...otherwise it doesn't add a group, but replaces all my groups with the specified list, resetting all my group memberships.

The result, I have lost my membership of the admin group.

Why this fails silently, rather than telling me I'm not a member of sudoers I don't know. I speculated about something around group membership as that's the only thing I changed when setting up my user account. I dismissed this theory since it seemed that sudo commands were executing fine

Note to programmers of future ubuntu installers, please add the main user to the sudoers file, rather than using group membership.

I'm now completely locked out of a remote server from a single missing character on usermod, removing my admin privileges. If I'd known group membership was the way sudoers membership was managed, or indeed that usermod has such dumb defaults, I'd have been more careful I suppose.

---

### Post by Rui Pais on 2007-06-20
Hi, try:
```
sudo adduser
```
it's easier and more configurable.

---

### Post by cefn on 2007-06-20
I identified the problem as described in my post above.

However, if there's an  'easier and more configurable' tool for doing things like adding groups to users, that would be useful.

---

### Post by Rui Pais on 2007-06-20
well adduser it's a script that ask question one by one about how to config the user acount.
Here an example:
```
$ sudo adduser david
Password:
Adding user `david' ...
Adding new group `david' (1004) ...
Adding new user `david' (1004) with group `david' ...
Creating home directory `/home/david' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for david
Enter the new value, or press ENTER for the default
        Full Name []: David LeBon
        Room Number []: 21212121
        Work Phone []: 946946946 
        Home Phone []: 353535353
        Other []: 
Is the information correct? [y/N] y
```

Another way, if you have gnome is users-admin.
It's a gui, allow change group, specific permissions, among others.

---

### Post by cefn on 2007-06-21
Still getting useless behaviour from the user*** tools. Now I can't add a home directory for an existing user.

$ sudo /usr/sbin/usermod -d /home/simon -m simon
$ ls /home/
btok  cefn

---

### Post by r0ydster on 2007-06-24
I believe that the useradd script is broken on 6.10 server as well.

I'm getting similar results - creates the entry in the password file, but that's it - it's not interactive as it should be.

/usr/sbin/useradd

-rwxr-xr-x 1 root root 60388 2006-10-19 17:52 /usr/sbin/useradd

Update:

I found that if I logged in as root, instead of using sudo, it works as it is supposed to - i.e.prompt for the info.  

This is on 2.6.17-10-server.

---

