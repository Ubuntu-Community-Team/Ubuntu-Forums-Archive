---
title: "Wireless and bcmwl5.inf...."
date: 2007-01-04
forum: General Help
---

### Post by nfl2k2 on 2007-01-04
[http://www.ubuntuforums.org/showthread.php?t=117001](http://www.ubuntuforums.org/showthread.php?t=117001)

Using instructions from the above page to install my Wireless broadcom connection on my laptop, latest version of Ubuntu installed. Here are the instructions I'm working with:

```

1. Create a broadcom folder in your Home folder.
2. In the folder, add both the bcmwl5.inf and bcmwl5.sys files.
3. In Terminal type: cd /home/your user name/broadcom
3. Type: sudo ndiswrapper -i bcmwl5.inf
4. Type: sudo ndiswrapper -d 14e4:4318 bcmwl5
5. Type: sudo ndiswrapper -l and it should say -- bcmwl5 driver present, hardware present
6. Type: sudo depmod -a
7. Type: sudo modprobe ndiswrapper

```

As you can see below, step #7 gives me and error message. How can I fix this and get my wireless working properly?


```

user@user-laptop:~$ cd /home/user/broadcom
user@user-laptop:~/broadcom$ sudo ndiswrapper -i bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
user@user-laptop:~/broadcom$ sudo ndiswrapper -d 14e4:4318 bcmwl5
ln: creating symbolic link `/etc/ndiswrapper/bcmwl5/14E4:4318.5.conf' to `14E4:4318:1468:0311.5.conf': File exists
Driver 'bcmwl5' is used for '14E4:4318'
user@user-laptop:~/broadcom$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present 
user@user-laptop:~/broadcom$ sudo depmod -a
user@user-laptop:~/broadcom$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
user@user-laptop:~/broadcom$ 

```

---

### Post by maclenin on 2007-01-17
Try this...

sudo aptitude install ndiswrapper-utils-1.8
sudo rm /urs/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper

...and then repeat:

sudo depmod -a
sudo modprobe ndiswrapper

Try:

iwconfig

You should be good to go!

---

### Post by lukemack on 2007-01-17
i'm trying this and the packages cant be found on the CD (6.10 edgy)

have also tried:

sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils

can i download the pavkage from somewhere?

---

### Post by oracle5 on 2007-01-17
The way you described is the way I did it the first time I set it up back when I used dapper but when I did I clean in stall of edgy I found ndisgtk which makes the process so much easier and its a gui. I'm not afraid of the command line but when all i have to do is click install and tell it where the driver is without typing several commands it makes it easier. Then I made a launcher on the panel that is "gksu modprobe ndiswrapper" and I use wifi-radar to connect. Its good since I show linux to a lot of people and I don't want them thinking you have to go into the command line to connect to wireless internet.

oracle5

---

### Post by modsbyus on 2008-05-30
I am having some trouble at step 4 and was wondering if you had any suggestions. i have followed steps 1 - 3 successfuly. i hav e included a copy of my terminal with the errors.
thanks


gary@gary-laptop:~/broadcom$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
gary@gary-laptop:~/broadcom$ sudo ndiswrapper -d 14e4:4318 bcmwl5
couldn't create symlink for "14E4:4303.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4310.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4313.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:431A.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4321.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4328.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4329.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:432A.5.conf": File exists -
installation may be incomplete
driver 'bcmwl5' is not installed (properly)!
gary@gary-laptop:~/broadcom$ sudo ndiswrapper -e bcmwl5
gary@gary-laptop:~/broadcom$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
gary@gary-laptop:~/broadcom$ sudo ndiswrapper -d 14e4:4318 bcmwl5
couldn't create symlink for "14E4:4303.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4310.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4313.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:431A.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4321.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4328.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4329.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:432A.5.conf": File exists -
installation may be incomplete
driver 'bcmwl5' is not installed (properly)!

---

