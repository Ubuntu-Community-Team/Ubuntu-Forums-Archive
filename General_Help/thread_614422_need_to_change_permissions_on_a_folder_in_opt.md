---
title: "need to change permissions on a folder in /opt"
date: 2007-11-15
forum: General Help
---

### Post by ridinglowest on 2007-11-15
This is my first time using ubuntu, I know nothing about linux so plesae bear with me. yesterday I was succeful in installing the os and installing xxamp and installing and setting up an ftp account and directory using gproftpd. All working nice I can ftp to it but i can not create folders in this directory it says that I dont have permissions. The directory is /opt/lamp/htdocs I amnot sure what it is called in linux but I created  (called in windws)a shortcut to the folder witch is located /home/user/public_html. That is the folder in gproftpd  that I have set up under the user as the directory. How do I change the permissions of this folder or is there another way to do it. I even tried to go in the file browser in bother folders and create a new folder and I cant. any suggestions?

One more question how do I set permissions that when someone goes to the ipaddress/folder(on a local network) that it prompts you for a username and password. Similar as u would on a web server. 

Thanks

---

### Post by Qwerty_ on 2007-11-16
I forget the terminal commands, but typing the following in the terminal will let you go to your /opt folder find what it is you need to change. Right click on it then select properties.

From that menu you will be able to set your permissions.

Command:

```
 sudo nautilus
```

---

### Post by kd7swh on 2007-11-16
you can also use:

```
sudo chmod
```

to change permissions.

for the manual entry on chmod type:

```
man chmod
```

---

### Post by ridinglowest on 2007-11-16
Thank You the first one worked.

---

### Post by por100pre1 on 2007-11-16
Next time use this:

```
gksudo nautilus
```

*sudo nautilus* can change ownership of files in your user folder and requires the "terminal window" to stay open.

---

