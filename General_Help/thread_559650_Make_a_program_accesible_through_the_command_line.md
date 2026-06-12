---
title: "Make a program accesible through the command line"
date: 2007-09-25
forum: General Help
---

### Post by Black Mage on 2007-09-25
I noticed that some programs like wine and eclipse are accessible just by typing that in the terminal. How do I make other programs, like VMserver Server Console accesible in the same way?

---

### Post by 505 on 2007-09-25
The application directory must be in $PATH. In a console type 'echo $PATH' to see which directories that are. You can either make a link in one of these directories to the application you want to start, or you can add a new directory to $PATH. Use:
```

PATH=$PATH:/new/dir
export PATH

```

---

### Post by nitro_n2o on 2007-09-25
you need to add this program executable to your PATH

echo $PATH 
will till you where you system should look for executable 
you should see something like this 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

you can also create a sym link to your program in one of these places 

Assume that VSmserver is located in /home/vmserver

then do this: 
sudo ln -s /home/vmserver /usr/bin/<WHAT_EVER_NAME_U_LIKE>

good luck

---

### Post by Black Mage on 2007-09-25
Ok, thnx a lot. But how do I find where the files are installed? I used search and nothing comes up, even when I do local file system. And I installed it using add/remove.

---

### Post by pointone on 2007-09-25
Every program is available on the command line; the problem is sometimes the names aren't quite what you'd expect. For example, the VMware Server executable might be VMserver, vmware, vmserver, VMWater_server, etc. Easiest way to find this out is to go to System > Prefereneces > Main Menu, then right click on the desired application and select Properties. The "Command" listed there is what you want to run.

---

