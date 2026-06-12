---
title: "Weird Proftpd problem"
date: 2007-01-17
forum: General Help
---

### Post by sakistakislakis on 2007-01-17
I'm having a very very weird proftpd problem that i've managed quite a bit to solve it but without success.The problem is that i have an upload section on the ftp in which i cannot upload a file (i get a 550 error).This is my conf file(the important part):

```

<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
                DenyAll
        </Limit>
</Directory>

<Directory /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
                DenyAll
        </Limit>

        <Limit STOR CWD MKD>
                AllowAll
        </Limit>
</Directory>

```


  Now,the most annoying thing is that MKD works fine ! This means that i can make a dir in the upload directory.And if i remove the STOR limitation from the first "Directory /home/ftp" i can also upload files!
  I really cannot find out why this happens.Any help would be greatly appreciated ;)

---

