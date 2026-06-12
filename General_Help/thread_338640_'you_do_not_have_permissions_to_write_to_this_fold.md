---
title: "'you do not have permissions to write to this folder'"
date: 2007-01-14
forum: General Help
---

### Post by ChrisE on 2007-01-14
I've been getting this error rather frequently while trying to move or edit files using the ubuntu graphical interface.

Is there an easy way to give myself permission to edit folders (it doesn't need to be permanent) without using sudo gedit 'filename' or something like that at the terminal?

thanks.

---

### Post by Nate53085 on 2007-01-14
you can type into a terminal:

> sudo nautilus

then you can do whatever you want to do in the window it opens

Make sure your careful though and close it when you are done.

---

### Post by taurus on 2007-01-14
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ardchoille42 on 2007-01-14
It's always a good idea to reserve "sudo" for command line apps and use gksudo for GUI apps like nautilus and gedit. Using sudo with graphical apps can cause problems. More information about this can be found here:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

You can do:

gksudo nautilus

and you'll have a nautilus running as root, which should allow you to do anything. But, be careful with that nautilus window. you can easily trash your system since it is running as root.

---

### Post by strabes on 2007-01-14
it depends on what folder you are trying to edit. If you're trying to do something to a folder in  your home directory, you should ```
sudo chmod 777 -R /home/username
```

but if you're trying to edit something else, you should always use the sudo command.

---

### Post by dreamerchawla on 2008-01-01
as told above u can do as follows......

give command

su
 
then it will ask for root password

after entering root password .....write 

nautilus

ur file system will open up which u can edit with full permissions

---

### Post by aysiu on 2008-01-01
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by nrichmond on 2008-01-13
Thanks for that. I did what I needed and it worked. Again, Thanks!

---

