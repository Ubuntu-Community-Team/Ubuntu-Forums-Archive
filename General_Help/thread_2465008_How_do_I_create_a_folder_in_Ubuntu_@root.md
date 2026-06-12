---
title: "How do I create a folder in Ubuntu @root ?"
date: 2021-07-19
forum: General Help
---

### Post by tangara on 2021-07-19
I need move a pem file from Windows 10 to my WSL2 20.04 LTS with root@Desktop since I downloaded Jenkins also to root which is the only way it works, and I don't have time to find how to do it via a username@desktop.

Can someone advise me how it can be done?

And how do I create a folder at root@Desktop to move this pem file from Windows 10 C:\Users\folder\pemfile ?

Hope someone can advise me.

Tks.

---

### Post by scorp123 on 2021-07-19
You might want to read this then:
[https://ubuntuforums.org/showthread.php?t=1486138]("https://ubuntuforums.org/showthread.php?t=1486138")

You'd be better off to let go of your weird idea that you "need to do this as root" and learn the proper way of doing things.

---

### Post by grahammechanical on 2021-07-19
I have no experience of either Windows 10 or Windows Subsystem for Linux but if I understand things correctly when you installed WSL you created a user and a password. And as this Subsystem for Linux is command line you would need to use Linux commands and to work in the root directory you would need to prefix the commands with the word "sudo" and then enter your user password when requested.

In command line Linux folders are called "directories."

If the directory is off the user/home directory you may not need to prefix the command with "sudo."

You need to change directory to where you want to create the directory. The command to change directory is "cd"

```
cd Desktop
```

> graham@sdb1-sdb8:~$ cd Desktop
graham@sdb1-sdb8:~/Desktop$

```
mkdir pem
```

To get back to the root directory

```
 cd ..
```

Now, you can move the file with the "mv" command

[https://linuxize.com/post/how-to-move-files-in-linux-with-mv-command/](https://linuxize.com/post/how-to-move-files-in-linux-with-mv-command/)

Regards

---

