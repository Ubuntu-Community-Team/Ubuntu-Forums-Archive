---
title: "How to login as root??"
date: 2007-10-07
forum: General Help
---

### Post by Emerican_360 on 2007-10-07
Ive just installed apache2 and php5 so to test it was working i wanted to create a file name index.php in /var/www but i couldn't because the folder is owned by root. So how do i log in as root? At the main login screen when you boot i typed root as the user name and put in the password but i got an error saying the root user cant login from here

So how do i become root so i can put files in that folder and change them?

THanks

---

### Post by Celegorm on 2007-10-07
Root is disabled by default in Ubuntu. Try putting 'sudo' at the front of whatever command you are using, or if you are using some graphical application, try ```
gksu app_name
``` in the terminal, substituting app_name for whatever application you are using. This will run just that one command, or application, as the case may be, as root.

---

### Post by Sef on 2007-10-07
[Root/Sudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Emerican_360 on 2007-10-07
Im not running an app im just in the file browser and i right click and the create document menu is grayed out and if i click properties then to to permisions only the root user and change and add files

---

### Post by Cannaregio on 2007-10-07
> Im not running an app im just in the file browser and i right click and the create document menu is grayed out and if i click properties then to to permisions only the root user and change and add files
Then you don't need to 'log in' as root.
Just get root on the fly.

```
sudo -i
```

---

### Post by Emerican_360 on 2007-10-07
I dont want to run everything from the terminal. Just like on windows i want to go into the directory and right click and create a new document

---

### Post by luisromangz on 2007-10-07
You don't have to run everything from the command line, but for your file browser to be able to get privileges to write to that folder, it needs to be launched from a privileged user.

You can press ALT+F2, and write "gksu nautilus", for example.

---

### Post by Celegorm on 2007-10-07
> **Emerican_360 said:**
> Im not running an app im just in the file browser and i right click and the create document menu is grayed out and if i click properties then to to permisions only the root user and change and add files

The file browser is actually an application called nautilus. Try ```
gksu nautilus
``` in the terminal.

---

### Post by leg on 2007-10-07
If you are using Nautilus can't you right click the directory and select open as administrator? Thats how I do it and my file browser is Nautilus. So browse into /var right click on the www directory and select open as administrator. Presto you have admin privilages on the www directory. What you will also need to do is change the permissions of the directory you create so that Apache can access it.

---

### Post by DagMan on 2007-10-07
You need a script set up for it.  Automatix installs this but I don't think it's out of the box in Ubuntu itself.  There's threads on nautilus-scripts and links in them out to a sourceforge page and probably some other pages.  They are easy to set up.
The link put up by Sef [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) was interesting with the drag and drop launcher.  Sounds very easy for someone wanting to just use the gui.

---

