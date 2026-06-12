---
title: "New user when logged in gives only '$' in console"
date: 2019-04-02
forum: General Help
---

### Post by ilaurens on 2019-04-02
When you login with a user you'd expect that it'll have a 'user@servername:~$' before you run the command. However when I create a user with the following command 'sudo useradd laurens -m' and try to login; 
it's give me the following prompt:
$

After that I can fill in a command, If everything worked fine it would not be a problem however it seems like it's rather bugged. I think the SSH client does not know where he is and that's causing issues; like using 'tab' to finish selecting a file does not work; when you apply multiple lines it sometimes become a mess/wrong input. etc etc. 

Anyone got a idea? I'm using ubuntu 18.10

---

### Post by deadflowr on 2019-04-02
Probably running /bin/sh instead of /bin/bash as the login shell.
(Or maybe even another shell?)

Look at what shell is listed in the passwd file
```
getent passwd | grep username
```
replace username with your user's name.

If not it, then have you been tweaking anything like the bashrc or skel or profile files anywhere?

---

### Post by SeijiSensei on 2019-04-02
The prompt is determined by the file /etc/profile which applies to every user.  New home directories are created by using the contents of /etc/skel.  Usually these are all configured in advance to provide the right prompt, etc. See what profile is created for new users.

---

### Post by ilaurens on 2019-04-02
@Deadflowr, Yes! that was exactly it; thank you :)

It was using '/bin/sh', by using 'sudo useradd laurens -m -s /bin/bash' I would generate the account with the correct SHELL. Thanks a lot :) Never knew there was ways to get another shell. 

@seijiSensei Thank you also, seems like it likes to use '/bin/sh' =P though, I wouldn't expect they'd do something like that.

---

