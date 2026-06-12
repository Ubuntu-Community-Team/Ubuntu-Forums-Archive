---
title: "window xp machine wont access ubuntu share?"
date: 2007-05-23
forum: General Help
---

### Post by klgsx on 2007-05-23
Laptop #1) windows xp

Laptop #2) ubuntu desktop

whenever i tried to access the ubuntu share from the xp using:

\\ubuntu-pc\share-name

I get prompted for user name and password.  I enter the user name that i have in my ubuntu, I enter my password and I am unable to log in.

What am i doing wrong?

Help

---

### Post by cantormath on 2007-05-23
> **klgsx said:**
> Laptop #1) windows xp

Laptop #2) ubuntu desktop

whenever i tried to access the ubuntu share from the xp using:

\\ubuntu-pc\share-name

I get prompted for user name and password.  I enter the user name that i have in my ubuntu, I enter my password and I am unable to log in.

What am i doing wrong?

Help

I think you have to set the samba password
```
:~$ smbpasswd
```

Hope that works.

---

### Post by dekeman18 on 2007-06-03
I am having the same problem. I have ubuntu 7.06 installed on my laptop, and a mac desktop running mac os 10.3.9. I set up a folder to be shared and the mac can see it but when I try to connect it asks me for a username and password. When I tried smbpasswd I got this message "Old SMB password:
New SMB password:
Retype new SMB password:
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE
Failed to change password for derrick"

I don't have an old password so I left it blank. I also found out about having to create a samba user and the command for that is: "smbpasswd -a <username>

When I did that I got this message "bash: syntax error near unexpected token `newline'

How do I fix this? I really need to get this file sharing setup asap. 


Thanks for any help.

PS: I just installed ubuntu 7.04. I did a clean install and reformatted the hard drive this morning.

Another thing I did fix the user thing. To create a user type in sudo smbpasswd -a username (where username is the new accounts username. For example if I wanted to create a user with the username dscholz I would type dscholz where the username is). 

But now my new problem is that when I try to connect to the shared folder I get an error code -43 and it says " The operation can not be completed because one or more of the required items can not be found." I don't know what to do now.

---

### Post by christowl on 2008-03-02
Hi All!

I'm having the exact same problem this guy had when I use smbpasswd I get 

Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE

Anybody know how to remedy this as i'm quite new to using Linux and finding it a very steep learning curve!

Thanks everyone

---

### Post by brabo on 2008-03-02
hi,

this may be a *very* stupid thing to ask, but are you guys using SMB or NFS for those shares?

brabo.

---

### Post by christowl on 2008-03-02
smb, any ideas?

---

### Post by darksidedude on 2008-03-02
i think you have to install something on windows, because windows cant nativly read ext3 partitions?
i watched a youtube video about this, but I cant rember the address, try going to youtube and looking for ubuntu shares, the guy is really annoying but it is really helpful:guitar:

---

