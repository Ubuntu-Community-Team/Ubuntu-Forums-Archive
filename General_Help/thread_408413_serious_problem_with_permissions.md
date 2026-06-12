---
title: "serious problem with permissions"
date: 2007-04-13
forum: General Help
---

### Post by b4nsh33 on 2007-04-13
Hi, i was trying to change permissions on some files in /etc/ and accidentally changed and messed up the file and directory permissions, now i got strange errors like this when i logon:

login as: mmiranda
mmiranda@192.168.10.56's password:
Last login: Fri Apr 13 09:00:01 2007
-bash: /etc/profile: Permission denied
-bash: /etc/bash_completion: Permission denied
I have no name!@ambepdc:~$


look at the permission denied and something about a name, this are users in ldap btw
how can i check what are the default permissions?

---

### Post by kidders on 2007-04-13
Hi there,

Getting the permissions in /etc exactly right is _critical_, both for security & stability. The two files you mention are "chmod 644" and "chown root:root", but we really should check that everything else in there is okay too.

If you post the result of **sudo ls -RAl /etc > ~/attachment.txt** (that's a lower case 'L', not an upper case 'I' in "-RAl"), and say what OS you're using, I can run a quick comparison with a safe configuration for you, and post back any differences.

I know now is the wrong time to say this, but you really do need to be careful with sudo!

---

### Post by b4nsh33 on 2007-04-13
Ok, this is the file

[http://200.13.161.20/attachment.txt](http://200.13.161.20/attachment.txt)

This is a amd64 ubuntu 6.10
Thanks i

---

### Post by kidders on 2007-04-13
Hey again,

I ran a quick check against a 6.10 of my own ... the results are attached.

Many of the files you listed failed the check (because they didn't exist on my own filesystem), so you'll have to use your own judgement with those. Of the files I *could* verify, there seem to be two main sorts of errors:

[LIST]
[*]Files whose access privileges got overwritten "chmod 0600" ... there seem to be a lot of those!
[*]Files that should be heavily restricted are too accessible (eg /etc/ssl/private) ... these are security holes.
[/LIST]

Hopefully my comparison will give you a place to start ... perhaps you could use it to create a list of "chmod" commands or something.

---

### Post by b4nsh33 on 2007-04-13
That is awesome, is all what i need  :guitar: 

man i owe a beer :-)
, happy weekend to all

---

