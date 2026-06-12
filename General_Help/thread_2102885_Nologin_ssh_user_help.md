---
title: "Nologin ssh user help"
date: 2013-01-08
forum: General Help
---

### Post by albin2009 on 2013-01-08
Okey, so im really new to ubuntu 12.04 LTS and i just got my apache2,mysql,pure-ftp server working.

I just created a account called test to try allow it to ftp.
I also created a www map for the user with the command:

sudo -u username mkdir /home/username/www

And to this point everything works okey with logging in to the ftp and so on with the rest account.

So now i want to disable ssh for the "test" account.

I went in to the passwd config from root with nano /etc/passwd and here is how the user looks:

test:x:1003:1002:,,,:/home/test:/bin/bash

My friend recently helped me with an other account and here is how the account looks in the passwd file:

alexftp:x:1002:1001:,,,:/home/alexftp:/usr/sbin/nologin

Im not sure how to edit the test user so he get the nologin.
Do i just delete the test:/bin/bash and change it with test:/usr/sbin/nologin or do i creat a new line?

And every time a save i just get this:

^Gget help ^M-D DOS-Format ^M-A Creat ^M-Bsecurity copy

^C cancle M-M^MAC-format M-P^Pastate

and by the way, im using pure-ftpd 

So i only want the user to acces FTP and not SSH and FTP

What am i doing wrong?

EDIT: i now know how to set /nologin on user in passwd but now the problem is, when i set /nologin on user i cant acces the from ftp.
I do not want to be able to acces shh, only FTP

---

