---
title: "File Transfers with VMware"
date: 2007-09-19
forum: General Help
---

### Post by Mongo5000 on 2007-09-19
Im using Vmware with windows xp and it works great.  Right now, i use ftp to get files from linux to my windows xp.  I know about winscp but can't get it to work, keep getting host not found errors.

Any tutorials on how to make this happen or tips someone can lend me?

---

### Post by JCorrea920 on 2007-09-19
You may want to install Cygwin on your Windows XP.

[http://www.cygwin.com/]("http://www.cygwin.com/")

Upon installation make sure you install these folowing packages:

SSH, RSYNC, SCP, etc.

When you start cygwin you will get a bash prompt where you can run your  bash commands. Then you can scp from linux to windows and vice-versa. If you want to copy entire directories use rsync this is a killer tool.

```
rsync -avz /path/to/directory/on/XP/ linuxusername@linuxhostname or IP:/path/to/directory/on/linux/

Example with linuxhost IP [COLOR="Red"]192.168.1.4[/COLOR], and  linux username [COLOR="red"]user[/COLOR]:

rsync -avz /path/to/My\ Documents/myfolder/ user@192.168.1.4:/home/user/myfolder/
```

This will copy myfolder on XP with all it contents to myfolder in linux. To do the opposite just switch the order of the /path/to/myfolder commands. You will need the linux user's password to start the proccess. Also make sure your user has permissions to copy files to the directory you choose otherwise this will fail. There are ways to run this command without having to enter the password but that is another topic.

Good Luck. Cheers

jcorrea920

---

### Post by fjgaude on 2007-09-19
You can use Samba and all works fine through your network connection. Remember each VM is like a piece of hardware. Use NAT for the VM connection and make sure you have Samba setup in your Linux box.

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

