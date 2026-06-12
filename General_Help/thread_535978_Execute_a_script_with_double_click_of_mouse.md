---
title: "Execute a script with double click of mouse?"
date: 2007-08-27
forum: General Help
---

### Post by hraposo on 2007-08-27
I made a scrip:
Fiz o seguinte script:
```
#!/bin/bash
echo -e "\033[32m
\033[34;1;7;5m AGORA VAI CONFIGURAR O READ-WRITE DOS DISCOS... Espere um momento!
\033[0m"
echo
apt-get update
apt-get install libfuse2 fuse-utils pmount
echo 'feito'
wget http://kent.dl.sourceforge.net/sourceforge/fuse/fuse-2.6.1.tar.gz
tar zxvf fuse-2.6.1.tar.gz
cd fuse-2.6.1
./configure --prefix=/usr --sysconfdir=/etc
make
make install
wget http://www.ntfs-3g.org/ntfs-3g-1.810.tgz
tar xzvf ntfs-3g-1.810.tgz
cd /home/user/Desktop/ntfs-3g-1.810
./configure --prefix=/usr --sysconfdir=/etc
make
make install
cd..
echo "fuse" >> /etc/modules
modprobe fuse
sed -i '/sda1/ s/^/#/' /etc/fstab
echo "/dev/sda1 /media/Windows ntfs-3g defaults,silent,user,auto,umask=0,locale=pt_PT.utf8 0 0" >> /etc/fstab
umount -a
mount -a
echo
echo -e "\033[32m
\033[34;1;7;5m TERMINOU A CONFIGURAÇÃO... AGUARDE UM POUCO!
\033[0m"
echo TERMINOU A CONFIGURAÇÃO... AGUARDE UM POUCO
sleep 10

```
[b]]What I want is that the script runs in console with only a double click, as an executable program. Whats the commands I must put in the begin of the script for it run with a double click of mouse?
[/b]

---

### Post by Steve1961 on 2007-08-27
> **hraposo said:**
> I made a scrip:
Fiz o seguinte script:
```
#!/bin/bash
echo -e "\033[32m
\033[34;1;7;5m AGORA VAI CONFIGURAR O READ-WRITE DOS DISCOS... Espere um momento!
\033[0m"
echo
apt-get update
apt-get install libfuse2 fuse-utils pmount
echo 'feito'
wget http://kent.dl.sourceforge.net/sourceforge/fuse/fuse-2.6.1.tar.gz
tar zxvf fuse-2.6.1.tar.gz
cd fuse-2.6.1
./configure --prefix=/usr --sysconfdir=/etc
make
make install
wget http://www.ntfs-3g.org/ntfs-3g-1.810.tgz
tar xzvf ntfs-3g-1.810.tgz
cd /home/user/Desktop/ntfs-3g-1.810
./configure --prefix=/usr --sysconfdir=/etc
make
make install
cd..
echo "fuse" >> /etc/modules
modprobe fuse
sed -i '/sda1/ s/^/#/' /etc/fstab
echo "/dev/sda1 /media/Windows ntfs-3g defaults,silent,user,auto,umask=0,locale=pt_PT.utf8 0 0" >> /etc/fstab
umount -a
mount -a
echo
echo -e "\033[32m
\033[34;1;7;5m TERMINOU A CONFIGURAÇÃO... AGUARDE UM POUCO!
\033[0m"
echo TERMINOU A CONFIGURAÇÃO... AGUARDE UM POUCO
sleep 10

```
[b]]What I want is that the script runs in console with only a double click, as an executable program. Whats the commands I must put in the begin of the script for it run with a double click of mouse?
[/b]

I could be wrong here but I think you just need to make the script executable:

chmod +x name_of_script

---

### Post by P4oL1n0 on 2007-08-27
You must render it executable with this command:
```
sudo chmod +x name.sh
```

---

### Post by hraposo on 2007-08-27
Is not this I mean. If I do chmod +x name-of-script, for I execute the script I must open an console and run ./name-of-script.
What I want is that the script begins with a double click of mouse on it.
I want thats when I do a double click with the mouse on script, it opens a console and the scripts runs automatically.

---

### Post by P4oL1n0 on 2007-08-27
> **hraposo said:**
> Is not this I mean. If I do chmod +x name-of-script, for I execute the script I must open an console and run ./name-of-script.
What I wnat is that the scrips begins with a double click of mouse on it.
I want thats when I do a double click with the mouse on script, it opens a console and the scripts runs automatically.

Is not true.
After the "chmod" command you can start your script with a double click.
Test it :D

---

### Post by KIAaze on 2007-08-27
And you don't need sudo unless it's not in your home directory. ;)

---

### Post by hraposo on 2007-08-27
I know, but, I must to choose between 4 options, and I must choose run as aplication or run in terminal. Is not that I want!!!!
I want that the scrip runs automatically like an aplication, lique a program, justo by click on it.

---

### Post by rich.bradshaw on 2007-08-27
You just choose run as application...

It won't work any other way - that's what scripts do...

---

### Post by hraposo on 2007-08-27
But is not possible that the script, itself, have a command thats make its run for itself by click with the mouse on it?

---

### Post by KIAaze on 2007-08-27
Try adding:
```
#! /bin/sh
```
or
```
#! /bin/bash
```
at the beginning of the script if it's an sh or bash script.

(if it's a python script, #! /usr/bin/python, etc)

If that doesn't work, place it in a directory mentioned in the PATH variable, i.e: /usr/bin or /usr/local/bin and then link to it.

You can also add your own directories to PATH by using:
```
export PATH=<dir>:$PATH
```

Place this line in your ~/.bashrc if you always want to have PATH set that way.

---

### Post by fimblo on 2007-10-18
> **hraposo said:**
> I know, but, I must to choose between 4 options, and I must choose run as aplication or run in terminal. Is not that I want!!!!
I want that the scrip runs automatically like an aplication, lique a program, justo by click on it.

1) save the script in some directory, say $HOME/bin/yourscript.sh.
2) make it executable using command: chmod u+x $HOME/bin/yourscript.sh
3) right-click on your desktop to create a launcher. fill in the blanks, and you'll have something you can double-click on, without being hassled with questions.

Good luck.

---

