---
title: "Help with SFTP?"
date: 2014-08-12
forum: General Help
---

### Post by RocketPenguin on 2014-08-12
I am currently working on making a test server for Minecraft, using McMyAdmin. In order to transfer, view, and delete files under the directory it is installed in, i am using SFTP. I have gotten as far as getting access to the directory (/home/rocketpenguin/McMyAdmin) but currently am only able to view the files. I have not yet been able to grand myself permissions to write/execute/modify any of the directory's content. How would i go at doing so? All i find deals with websites and such, wrapping in with some www directory that i have no idea about. How would i give myself the permissions? 
I use ssh to communicate with the server, as it is semi headless. (It supports a monitor, but currently don't use it.)

EDIT: Figured it out. All i had to do was chmod -R 777 the /home/rocketpenguin directory. Thanks for anyone who posted, cheers!

---

### Post by nerdtron on 2014-08-12
What account do you use on sftp? Let's see what group it belongs so try:
```
id account_name
```

Then we need to see the permissions of the folder itself:
```
cd /home/rocketpenguin/
ls -lah
```


Better if you ran the above commands as root just to make sure about the permissions.

---

