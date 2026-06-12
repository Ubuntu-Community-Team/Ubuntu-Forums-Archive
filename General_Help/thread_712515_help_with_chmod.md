---
title: "help with chmod"
date: 2008-03-01
forum: General Help
---

### Post by Askalton on 2008-03-01
i need help using this command. My objective is giving full access to an HDD mounted on /media/Dados, so i can create folders, files and such there :P tahnks :)

---

### Post by Askalton on 2008-03-01
i know its a simple command :( i just dont remember it

---

### Post by Oldsoldier2003 on 2008-03-01
> **Askalton said:**
> i need help using this command. My objective is giving full access to an HDD mounted on /media/Dados, so i can create folders, files and such there :P tahnks :)

man chown:
 chown -hR root /u
              Change the owner of /u and subfiles to "root".
thus you could (not recommended because it might create other issues)
```

sudo Chown -hR <yourusername> /media/Dados
```

But if the media is mounted and you are the admin users you should already be able to write in that disk, if you try to access it through nautilus it should ask you for your admin password . After entering it you should be able to work in that disk just fine.... maybe create a user dir in there and do this:

```
sudo chown <username>:<usergroup>/media/Dados/<yourdir>
```

---

### Post by Askalton on 2008-03-01
i tried that and surprsingly now i cant even read the files from there O_o It says i dont have permissions to access the folder

---

### Post by Oldsoldier2003 on 2008-03-01
> **Askalton said:**
> i tried that and surprsingly now i cant even read the files from there O_o It says i dont have permissions to access the folder
post the output of ls -l and we can take a looksee :) its probably something real simple to fix

sudo -i
cd to the dir you created 
then ls -l

---

### Post by Askalton on 2008-03-01
ill try O_o Might take a while since im using the laptop atm. gonna look for a USB flash drive to copy it

---

### Post by Askalton on 2008-03-01
tiago@tiago-desktop:~$ sudo -i
[sudo] password for tiago:
root@tiago-desktop:~# cd /media/Dados
root@tiago-desktop:/media/Dados# ls -l
total 16
drwx------ 2 tiago root 16384 2008-03-01 22:50 lost+found
root@tiago-desktop:/media/Dados# 


this :P

---

### Post by Oldsoldier2003 on 2008-03-01
> **Askalton said:**
> tiago@tiago-desktop:~$ sudo -i
[sudo] password for tiago:
root@tiago-desktop:~# cd /media/Dados
root@tiago-desktop:/media/Dados# ls -l
total 16
drwx------ 2 tiago root 16384 2008-03-01 22:50 lost+found
root@tiago-desktop:/media/Dados# 


this :P
ok open a terminal and do this
```
sudo -i
cd /media/Dados
mkdir tiago
chown tiago:tiago /media/Dados/tiago
exit
```
then this to see if you can access the directory properly as a non root user.

```
cd /media/Dados/tiago
touch test.txt
```

---

### Post by Askalton on 2008-03-01
tiago@tiago-desktop:~$ sudo -i
[sudo] password for tiago:
root@tiago-desktop:~# cd media/Dados
-bash: cd: media/Dados: Ficheiro ou directoria inexistente
root@tiago-desktop:~# cd /media/Dados
root@tiago-desktop:/media/Dados# mkdir tiago
root@tiago-desktop:/media/Dados# chown tiago:tiago /media/Dados/tiago
root@tiago-desktop:/media/Dados# exit
logout
tiago@tiago-desktop:~$ cd /media/Dados/tiago
bash: cd: /media/Dados/tiago: Permissão negada
tiago@tiago-desktop:~$ 

permission denied :/

---

### Post by Askalton on 2008-03-01
Solved it through graphical interface :P went to the proprieties of the folder and gave writing permissions there. I just couldnt do that before cause i wasnt the owner of that folder :)

Thanks for the help ^^

---

