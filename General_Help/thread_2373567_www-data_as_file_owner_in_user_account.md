---
title: "www-data as file owner in user account ?"
date: 2017-10-07
forum: General Help
---

### Post by rushyx on 2017-10-07
I've noticed that if I create a bunch of files www-data:www-data owner/group privs. in my user account then next time I login I am dumped out of the account back to the login prompt and cannot login anymore! Perhaps this is because the user www-data has "nologin" in the /etc/passwd file. I'm surprised that it can detect files exist of www-data user in my user account and dump me out? Is that normal behaviour? If I make them me:www-data I do not have any problem with my login. I am keeping a set of web files in my user account and have symlinks in my localserver pointing to these files. Makes it easier to edit them etc. that is the rationale for doing this. Anyway I just wonder if this is correct behaviour or if I have some strange bug? Previously I spent a hell of a lot of time rebuilding my system because I was sure there was a hardware error causing some corruption dumping me out of login... !

Paul

---

### Post by SeijiSensei on 2017-10-07
The www-data user is not allowed to log in as a security measure.  Most such "users" that own daemon processes have no login privileges.

One solution might be to add yourself to the www-data group.  Do not give www-data login privileges if the machine is exposed to the outside world.

---

### Post by steeldriver on 2017-10-07
AFAIK, simply creating files owned by www-data:www-data in a user's $HOME shouldn't have that effect - unless one or more of those is a file that the login process needs to write to (for example, a .Xauthority file, or possibly .xsession-errors) or there's something in your particular session setup that tries to write to them

---

### Post by rushyx on 2017-10-07
Thanks for the reply. I realise the security implications and I'm only developing on a local server at the moment. I doubt that having files with owner www-data in a user account should bump that user back out to the login prompt soon after successful login, but that is what is happening to me. When I have the same files with usual account ownership it does not happen. I am not even trying to access these files - the fact they reside in my user account causes this behaviour. I am still convinced something very odd is going on and would value your comments on the behaviour I am observing.

---

### Post by TheFu on 2017-10-07
All of these things come back to the basic UNIX security model.  HOME directories are meant for end-users, not daemons.

If you'd like more help, we'd need to see the passwd entries for the userids involved and the permissions for the directories and files involved.  Without more details, impossible to clearly understand what is really happening.

If you must, create a symbolic link FROM your HOME ----TO---- the location where the web files are stored.  Or use the cdpath variable. Home directories may not have the permissions necessary for a web-server to access those files.  Changing the permissions on a HOME directory, isn't usually smart.

---

### Post by oldos2er on 2017-10-07
Thread moved to General Help.

---

### Post by efflandt on 2017-10-08
You should do things the other way around with the links. It would be best if the actual files were in the web path, with symlink(s) in your home directory. And it is not even necessary that html files be owned by the user that the webserver runs as, as long as the files have read permission by "others" (like 644 or -rw-r--r--, but directories should also have x permission 755 or drwxr-xr-x, which for directories means access, not execute).

For example where user's web files are accessed with a URL like hostname.domain.tld/~username/, they would typically have a **public_html** symlink in their home directory to their username directory under web server files, and files would still be owned by the user. Or similarly on a NetBSD shell account I have where our web content is accessed by a URL starting with username.domain.tld (or some people have their own domain), they have an **html** symlink to our username directory in the web files owned by the user. For example:

```
$ ls -l html
lrwx------  1 efflandt  arpa  18 Sep 10  2015 html@ -> /www/af/e/efflandt
$ cd html
$ ls -l index.html
-rwxr-x--x  1 efflandt  nobody  1194 Oct  9  2008 index.html*
```

I don't see how just having files owned by another user in your home directory would be a login problem, unless your entire username directory is changed to a user with nologin, or you run something in X as another user that changes certain files related to X to some other user without specifically using that other user's environment. Then certain files related to X might not be owned by you which could break gui login.

---

