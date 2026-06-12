---
title: "sshfs and suspend ubuntu 12.04"
date: 2012-11-01
forum: General Help
---

### Post by skyw33 on 2012-11-01
There's a known launchpad bug regarding sshfs and suspend so I'm posting my workaround since I haven't found any other complete solution.

Problem:  I use sshfs and when I try to suspend using ubuntu's default suspend function in (either via menu or closing lid), the screen goes blank for about 20 seconds and then an error appears "freezing of tasks failed".  Then the lock-screen appears and the computer never actually suspends.

Workaround: first create a new bash script file in /etc/NetworkManager/dispatcher.d

I named it trigger-sshfs-on-connect.sh

```
#!/bin/bash
#this goes in /etc/NetworkManager/dispatcher.d/

#change this to whatever ip address your remote machine is
IP_ADDRESS=192.168.1.100

#change this to whatever port you want
port=22

#change local_username to your username on local machine
#change remote_username to your username used to connect to remote machine
sudo -u local_username sshfs -o idmap=user -p $port remote_username@$IP_ADDRESS:/ho
me/remote_username /media/whateveryouwant

```

This will mount your sshfs each time you establish a wired or wireless connection.  You'll need this because we need to unmount sshfs in order to suspend.

The script lid.sh controlls the machine behaviour when the lid is closed/opened.  If you have your machine setup to suspend when the lid is closed, modify /etc/acpi/lid.sh and add the following line (code snippet provided for context):

```

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then

[COLOR="Red"]fusermount -u /media/whateveryouwant[/COLOR]

for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;


```


You may need to add this line to other scripts in the /etc/acpi folder depending on your setup/needs.

skyw33

---

