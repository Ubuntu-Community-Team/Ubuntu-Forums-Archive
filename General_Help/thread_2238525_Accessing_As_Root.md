---
title: "Accessing As Root:"
date: 2014-08-08
forum: General Help
---

### Post by staustelladam on 2014-08-08
Hi,

Having problems trying to work out how to log in as root. System settings won't (appear) to let me add a root user to the log in screen, so I am stuck with logging in as either myself or guest, or any other accounts I may need to add.

Even if I don't have root as one of the accounts as an option at log in, is there any straightforward way to log in as root? I need to access some files that are owned by root, to edit settings in a game, and as root is the owner there is nothing I can do to make changes to the files.

Thanks in advance,

Adam.

---

### Post by QIII on 2014-08-08
Hello!

There is no reason to log in to a desktop interface as root.  It is a safety feature of Ubuntu.

By default, the root account is not enabled in Ubuntu.

In fact, if anyone gives you instruction on how to log into a graphical interface as root, we will remove the post and likely close this thread.

Anything you would need to do as root can be done in the command line by invoking sudo (or su or gksudo or gksu ...) in the terminal to temporarily raise your privileges.

Please see [this]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Rob Sayer on 2014-08-08
Trust me, by the very nature of your question the *last* thing you want to have is root access.  

A buddy of mine who is a unix sysadmin has a cool t-shirt that says: "I am root.  Kneel before me".

Stick with sudo.

---

### Post by Lars Noodén on 2014-08-08
> **staustelladam said:**
> I need to access some files that are owned by root, to edit settings in a game, and as root is the owner there is nothing I can do to make changes to the files.

What files do you need to access?  We can help you find the safe way to get to them.

---

### Post by staustelladam on 2014-08-09
Hi all,

Thanks for all the answers. Okay, so no, I don't actually need to log in as root, but I still need root permissions for files owned by root.

My initial query came as a result of not being able to edit/save some game files in usr/share/application. As the game in question is editable what I wanted to do was simply change the folder properties to read/write rather than read only. My only options there seem to be right click/properties, with owner (root) being able to modify files whilst groups and others can only read the files.

So, after your responses I'll rephrase the question: using terminal how would I change the properties of a folder using sudo or any other command?

Thanks again,

Adam.

---

### Post by mooreted on 2014-08-09
Game files are usually stored in your home directory. /usr/share/applications contains desktop launchers to launch the game, not save game data. You can think of them like desktop shortcuts in Windows and as a rule you don't want to mess with them unless you know what you're doing. Game config files and game data may be in a hidden folder in your home directory. If you open the file manager and use "CTRL+H" on your keyboard you can see those hidden files. For instance, Steam saves it's data in your home directory in a hidden folder named ".steam". The dot in front of the name "steam" means it is a hidden folder.

What game is it and what are you trying to accomplish?

---

### Post by vasa1 on 2014-08-09
I suggest this thread be closed. OP can always start a new thread giving exact details of what help is required.

---

### Post by oldos2er on 2014-08-09
> **staustelladam said:**
> Thanks for all the answers. Okay, so no, I don't actually need to log in as root, but I still need root permissions for files owned by root.

Use ```
sudo -i
``` which will create a persistent root terminal. When you're done type ```
exit
``` I've found it good practice to create a backup copy of any file before editing it.

---

