---
title: "Create User"
date: 2006-07-26
forum: General Help
---

### Post by mathon on 2006-07-26
Hello,

I want to create a new user and therefore I tried it with useradd joe. But when I use this command no home-directory was created and I am not able to switch to the new user with su joe...?
However the user exists because a new entry was made in passwd joe:x:1002:100::/home/joe:/bin/sh, however I think it is a little bit strange that /bin/sh is used and not /bin/bash..? 
No new entry was made in group although I thought that a new group with the same name is created when I create a new user...?
The entry in the shadow file looks as follows: joe:!:13355:0:99999:7:::. 

I also tried it with useradd -d /home/joe joe but this does not help.

Has anybody answers for my questions?:confused:

---

### Post by Daniel15 on 2006-07-26
I believe you can use 'adduser' rather than 'useradd'. AFAIK, that will create the home directory :)

---

### Post by mathon on 2006-07-26
Regarding this I have three more questions:

*) Great now it works what is the difference of adduser to useradd I thought I can use both...?

*) When I created a new user with adduser and then switch to his home directory on the shell with su username and password - then I want to create a new directory but I always get a message that Permissions denied. But why? - I switched to the new user and also entered the password...?

*) When I use the su command to switch the user - this should then be recorded in the /var/log/messages file, but I can't find an entry. Can anybody tell me how this entry should look like?

Regards

---

### Post by mathon on 2006-07-26
It would be great if anybody could answer me the questions of my previous posting...:(

---

### Post by altarya on 2007-01-09
I'm not sure if this issue was ever solved, but...

I had an issue creating a user with the 'passwd *user*' command, and it was because I had not used the useradd command. It may be that both commands are necessary.

add the user:
useradd [-d /home/newuser, -G xxx,xxx] *newuser*
set the password:
passwd *newuser*

When I did those two it worked via the shell, rather than the GUI. I know its probably easier to use the GUI, but its nice to be able to do this via ssh when on a remote connection.

---

