---
title: "Can't save files with VS code and WSL2 - although there are sufficient permissions"
date: 2021-08-21
forum: General Help
---

### Post by stackerito on 2021-08-21
[SIZE=3][COLOR=#242729][FONT=-apple-system]Using Ubuntu 20.04 on WSL2, I'm having troubles saving files from VS code with the following error:
[/FONT][/COLOR][/SIZE]
> [INDENT][FONT=inherit]Failed to save 'index.php': Unable to write file 'vscode-remote://wsl+ubuntu-20.04/home/myuser/sites/mysite/pages/index.php' (NoPermissions (FileSystemError): Error: EACCES: permission denied, open '/home/myuser/sites/mysite/pages/index.php')[/FONT]
[/INDENT]


[SIZE=3][COLOR=#242729][FONT=-apple-system]Although the file on the Ubuntu OS inside WSL seem to have sufficient permissions:
[/FONT][/COLOR][/SIZE]
```
myuser@wsl:~/sites/mysite/pages$ ls -la
total 24
drwxr-xr-x  2 www-data www-data 4096 Aug 17 18:56 .
drwxr-xr-x 12 www-data www-data 4096 Aug 21 01:26 ..
-rw-r--r--  1 www-data www-data  684 Aug 21 02:10 index.php

```

[SIZE=3][COLOR=#242729][FONT=-apple-system]The user and group are www-data because I'm using Docker, and Docker will have its own permissions issues if I create the container with a different user other than www-data[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]But if www-data also has -rw permissions - why can't I save? Is it something related to permissions between Windows and WSL?[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]Because if I use sudo chown -R myuser ~/sites/ (with my wsl user and not www-data), I can save the files without permission issues, although the permissions are identical:
[/FONT][/COLOR][/SIZE]
```
myuser@wsl:~/sites/mysite/pages$ ls -la
total 24
drwxr-xr-x  2 myuser 82 4096 Aug 17 18:56 .
drwxr-xr-x 12 myuser 82 4096 Aug 21 01:26 ..
-rw-r--r--  1 myuser 82  684 Aug 21 02:10 index.php

```

[SIZE=3][COLOR=#242729][FONT=-apple-system]How can I make www-data be able to save files as well? And should I? Or I should go for a different approach (Maybe doing the opposite - changing the permissions of the Docker container user)[/FONT][/COLOR][/SIZE]

---

### Post by TheFu on 2021-08-21
I suspect there are some other very important details about this setup that haven't been shared.  

For example, most docker containers should only have files inside updated by rebuilding the container and placing new files desired into that build process, not by editing the files inside the containers.  Linux Containers are like paper airplanes.  They shouldn't be modified after created.  When a change is needed to an existing airplane, create a new paper airplane with any needed updates.

If you want to write files owned by www-data, then the userid doing the writing should be www-data.  Don't get confused by any settings outside the container.  It is what the container sees from "inside" that matters.

Php webapps really should be read-only for the userid that runs them. In this case, that is www-data.  It is a security thing and allowing writes is a good way to be hacked.

Linux is multi-user - in each environment.  That means the hostOS, any VM, and any containers. Each has different userid and groupids that are running processes. File permissions control the access that a process, run by a userid, can have to the file(s). It can take a bit to get used to switching userids and groupids in your brain.

---

