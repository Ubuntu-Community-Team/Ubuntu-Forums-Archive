---
title: "giving a user root priveleges?"
date: 2012-10-22
forum: General Help
---

### Post by hotshot247 on 2012-10-22
their is this cli program but i need root privileges to do anything with it and what i was wanting to know is if it's possible to give my user root privileges to just that one program so i don't have to type in my password each time? thanks in advance for the help!

---

### Post by Gerie Langeveld on 2012-10-22
If the program is owned by root, you could use the following UNSAFE method:
```
$ sudo chmod +s /path/program
```
The s-flag will make the program run under the uid of the owner of the command.

---

### Post by angry_johnnie on 2012-10-22
You could edit the sudoers file by issuing

```
sudo visudo
```

Then add an entry at the end of the file.  something like this

```
%admin ALL=NOPASSWD: /path/to/program
```

This, of course, assuming your user is in the admin group.

You would then save the file and exit.  It shouldn't prompt for a password, after that.

---

### Post by rnerwein on 2012-10-23
> **Gerie Langeveld said:**
> If the program is owned by root, you could use:
```
$ sudo chmod +s /path/program
```The s-flag will make the program run under the uid of the owner of the command.

if you give your program the set-uid bit only the permissions, i think, will result in:

-r-sr-xr-x  1 root groupname .....

but this means that everybody else can run this program ( group other )
use chmod (you must be superuser): chmod 4550 your-program.
this results in: -r-sr-x---  only the owner and a goup member can run this program

ciao

---

### Post by Lars Noodén on 2012-10-23
suid is generally frowned upon and automatic security audit programs usually report it as an error to be fixed.  

sudo is definitely the way to grant privileges for just one program and not others.  This is the kind of thing that sudo was designed for.  angry_johnnie pointed to what you need to add to /etc/sudoers to make it work.  If you do not want to use the group 'admin' you can choose any group you want or even make a new one.  

Just be sure that when you have saved /etc/sudoers that it works before you quit.  You can check in another window or use visudo to edit.

---

