---
title: "Symbolic link to program in root folder"
date: 2013-02-11
forum: General Help
---

### Post by findingthebalance on 2013-02-11
I am a new Ubuntu user.

I just installed Komodo edit via Terminal and it says Komodo Edit 7 has been successfully installed to: /root/Komodo-Edit-7. It then tells me I should create a symbolic link to 'komodo', e.g.:

ln -s "/root/Komodo-Edit-7/bin/komodo" /usr/local/bin/komodo

I do not know how to do this and cannot fine clear instructions on how to proceed. Is there step by step instructions to assist me. Also, if I wanted to uninstall this program from the root folder how would one go about such a task? I cannot access the root folder.

---

### Post by Impavidus on 2013-02-11
As you saw, ordinary users don't have access to /root, so you won't be able to run a program installed there unless you're root, which is a bad idea. Even when you make a symlink from somewhere else. Therefore, programs like komodo edit shouldn't be installed in /root. How did you install it there in the first place?

---

### Post by findingthebalance on 2013-02-11
Thank you for your reply,

I followed some instructions I found on the web and it worked fine. I was given the opportunity to change the destination of the install or use the default location. being a new user I just accepted the default. So now what? How do uninstall it once it is there in the /root?

---

### Post by findingthebalance on 2013-02-11
One more thing, If I go to home and do a search, location-file system and search Komodo I find all the files installed and if I click the Komodo application icon the program starts, but there is no other way to start the program such as a desktop or launcher shortcut.

---

### Post by Impavidus on 2013-02-12
Where do you find all files installed? /root/Komodo-Edit-7? But you need root permission to search that directory.

The typical place for manual installation is /usr/local. Anything that has been installed with the package manager can be uninstalled with the package manager, things installed manually can be uninstalled by deleting all files and directories. Try something like
```

sudo rm -rf /root/Komodo-Edit-7

```Double check the command before you hit enter. One wrong character or space can destroy your system.

But you say you can start the program, which is not possible if it is installed in /root, unless you are root or you changed the permissions of /root. Or is this after you reinstalled somewhere else?

---

