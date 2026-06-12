---
title: "DrQueue setup"
date: 2006-11-24
forum: General Help
---

### Post by tempo500 on 2006-11-24
hi,

i will just give it a try...maybe someone stops by with knowledge of drqueue... i basically have a functioning setup on my workstation(server), which renders maya, as well shake files, just as expected. my render computer(slave) has problems finding the script file, written by drqueue. but there is no problem coping the actual render command out of the drqueue script file and exectuing it manually. no permission problem, renders the file onto the server without any problems... both slave and server have the same UID and GID (phil:phil). the actual error message from slave is,

```
Log started at Fri Nov 24 14:44:12 2006
Computer: render
Log filename: /usr/local/drqueue/logs/002.shake default/shake default.0002

sh: /home/phil/shake/projects/test/test.shk.4566F733: not found
Log started at Fri Nov 24 14:55:09 2006
Computer: render
Log filename: /usr/local/drqueue/logs/002.shake default/shake default.0002
```

i have written a howto for myself, i'll just post it, that one can see what i did... phil

ps: if i create the script within the gui - drqman - it writes out /home/phil/shake/projects/test//test.shk.4566F733 so i changed it to
/home/phil/shake/projects/test/test.shk.4566F733 

```
same user on all machines user phil / group phil
--------------------------------------------------------------------------------------MASTER
#compile
make INSTROOT=/usr/local/drqueue INSTUID=phil INSTGID=phil install
	(gedit Makefile	#change user to phil
	INSTUID ?= drqueue
	INSTGID ?= drqueue)
make install
#link master, slave, drqman
link files /usr/local/drqueue/bin to /usr/local/bin


#/etc/exports
	/home/phil      192.168.2.102(rw,async)
	/usr/local/drqueue 192.168.2.102(rw,sync)

#nfs restart
	/etc/etc/init.d/nfs-user-server restart

#/etc/hosts
	192.168.2.103	workstation	workstation.workgroup.local
	192.168.2.102	render 		render.workgroup.local

#/home/phil/.bashrc //Enviroment variables
##DRQUEUE
	export DRQUEUE_ROOT=/usr/local/drqueue
	export DRQUEUE_TMP=/usr/local/drqueue/tmp
	export DRQUEUE_MASTER=192.168.2.103


--------------------------------------------------------------------------------------SLAVE
#create dir
	sudo mkdir /usr/local/drqueue

#mount maya/shake project path / drqueue root directory
	sudo gedit /etc/fstab
	192.168.2.103:/home/phil/maya/projects /home/phil/maya/projets nfs defaults 0 0
	192.168.2.103:/home/phil/shake/projects /home/phil/shake/projets nfs defaults 0 0
	192.168.2.103:/usr/local/drqueue /usr/local/drqueue nfs defaults 0 0

#/home/phil/.bashrc //Enviroment variables
##DRQUEUE
	export DRQUEUE_ROOT=/usr/local/drqueue
	export DRQUEUE_TMP=/usr/local/drqueue/tmp
	export DRQUEUE_MASTER=192.168.2.103

#copy slave script to /usr/local/bin
	/usr/local/drqueue/bin/.slave

#/etc/hosts
	192.168.2.102 render render.workgroup.local
	192.168.2.103 workstation workstation.workgroup.local

--------------------------------------------------------------------------------------RENDER-COMANDS
	#project path permissions
cd /usr/local/drqueue
sudo chmod -R 777 tmp/
sudo chown phil:drqueue -R tmp/
-------------------------------------------check enviroment path
echo $DRQUEUE_TMP
set | grep DRQUEUE_TMP
```

---

### Post by tempo500 on 2006-12-02
just to complete this thread... my problem was that tcsh wasnt installed... my notes on setting up drqueue... ubuntu 6.10...

```
drQueue

packages
tcsh - on slave and master
same user on all machines user phil / group phil
--------------------------------------------------------------------------------------MASTER
#compile
make
sudo make INSTROOT=/usr/local/drqueue INSTUID=phil INSTGID=phil install
#link master, slave, drqman
link files /usr/local/drqueue/bin to /usr/local/bin

#/etc/exports
	/home/phil      192.168.2.102(rw,async)
	/usr/local/drqueue 192.168.2.102(rw,sync)

#/etc/hosts
	192.168.2.103	workstation	workstation.workgroup.local
	192.168.2.102	render 		render.workgroup.local

#/home/phil/.bashrc //Enviroment variables
##DRQUEUE
	export DRQUEUE_ROOT=/usr/local/drqueue
	export DRQUEUE_TMP=/usr/local/drqueue/tmp
	export DRQUEUE_MASTER=192.168.2.103

#edit drqueue/etc/shake.sg
from the render execution command 
"shake" to /opt/shake-v4.00.0607/bin/./shake

#edit /drqueue/etc/*.conf files
master.conf
logs=/usr/local/drqueue/logs

tmp=/usr/local/drqueue/tmp

db=/usr/local/drqueue/db

bin=/usr/local/drqueue/bin

etc=/usr/local/drqueue/etc

slave.conf
logs=/usr/local/drqueue/logs

tmp=/usr/local/drqueue/tmp

drqman.conf
logs=/usr/local/drqueue/logs

tmp=/usr/local/drqueue/tmp

db=/usr/local/drqueue/db


--------------------------------------------------------------------------------------SLAVE
#create dir
	sudo mkdir /usr/local/drqueue

#mount maya/shake project path / drqueue root directory
	sudo gedit /etc/fstab
	192.168.2.103:/home/phil/maya/projects /home/phil/maya/projets nfs defaults 0 0
	192.168.2.103:/home/phil/shake/projects /home/phil/shake/projets nfs defaults 0 0
	192.168.2.103:/usr/local/drqueue /usr/local/drqueue nfs defaults 0 0

#/home/phil/.bashrc //Enviroment variables
##DRQUEUE
	export DRQUEUE_ROOT=/usr/local/drqueue
	export DRQUEUE_TMP=/usr/local/drqueue/tmp
	export DRQUEUE_MASTER=192.168.2.103

#/etc/hosts
	192.168.2.102 render render.workgroup.local
	192.168.2.103 workstation workstation.workgroup.local

#copy slave script to /usr/local/bin
	/usr/local/drqueue/bin/.slave

--------------------------------------------------------------------------------------COMMANDS
-------------------------------------------project path permissions
cd /usr/local/drqueue
sudo chmod -R 777 tmp/
sudo chown -R phil:phil /usr/local/drqueue
chmod –R 777 /usr/local/drqueue
-------------------------------------------check enviroment path
echo $DRQUEUE_ROOT
set | grep DRQUEUE_TMP
-------------------------------------------nfs stuff
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -ra #/etc/exports
```

---

### Post by wizo on 2008-03-17
hey, did you compile drQueue from source or did you use packages from the repository? i find that installing from teh repositories puts the drQueue files in weird places..

---

