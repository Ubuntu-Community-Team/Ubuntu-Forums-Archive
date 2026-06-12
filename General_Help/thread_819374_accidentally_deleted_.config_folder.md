---
title: "accidentally deleted .config folder"
date: 2008-06-05
forum: General Help
---

### Post by opakedragon on 2008-06-05
So I was going into my hidden folders and deleting any uninstalled application configure folders and I realize that I accidentally deleted the .config folder which I now realize is important to be able to access my home folder(I came to this conclusion because when I had to restart my computer for some reason... I think it was after emptying the trash... when I try to open any folder the window pops up but there are no icons and its unresponsive). I dont know how to recreate it. Please help.


EDIT: I also don't intend to try to delete old app files anymore....

EDIT 2: Also it seems to only be affecting the home folder.... and a couple of times now the window popped back up in the same condition even after a forced quit....

---

### Post by erginemr on 2008-06-05
I am not sure but it might work if you create a new user and copy this virtual user's .config file to your home folder.

---

### Post by drs305 on 2008-06-05
Get to a terminal and see if the file is still in the trash (for Hardy):
```
ls -a /home/**username**/.local/share/Trash/files
```

Check to see if the .config folder is listed.

If you find it, this should work if a new config folder hasn't been created:
```
mv /home/**username**/.local/share/Trash/files/.config /home/username
```

---

### Post by opakedragon on 2008-06-05
> **erginemr said:**
> I am not sure but it might work if you create a new user and copy this virtual user's .config file to your home folder.

ok now I am not exactly a noob at Ubuntu (feisty) but I have never had any need to make a user since I am the only user so.... could you tell me how?

Thanks again.

I will try the trash can thing now

EDIT: it says:
```
~$ ls -a /home/mike732/.local/share/Trash/files
ls: /home/mike732/.local/share/Trash/files: No such file or directory
~$
```

EDIT 2: when i created the new user there was no .config folder....

---

### Post by opakedragon on 2008-06-05
I just wanted to mention that I also cannot right click or left click anything on the desktop when this happens

EDIT: also when I checked the home folder with the new user I saw that there was in fact a .config file....

---

### Post by drs305 on 2008-06-05
[QUOTE=opakedragon;5121251
EDIT: it says:
```
~$ ls -a /home/mike732/.local/share/Trash/files
ls: /home/mike732/.local/share/Trash/files: No such file or directory
~$
```[/QUOTE]

You could try a more globalized search just in case the deleted folder ended up somewhere else. Don't get excited if it finds */root/.config*, that's a normal system file. Get excited if you find .config in conjunction with a Trash folder. ;-)
```
sudo find / -type d -iname '.config'
```

---

### Post by opakedragon on 2008-06-05
```
~$sudo find / -type d -iname '.config'
Password:
/root/.config
/home/mike732/.config
~$
```

this is what I have so I supect that perhaps I did not delete it after all but that does not explain the strange behavior. It only happens when I try to open the my home folder....

Could it be nautilus? ...because when the folder force quits, nautilus disappears from the System Monitor.

---

### Post by sisco311 on 2008-06-05
> **opakedragon said:**
> So I was going into my hidden folders and deleting any uninstalled application configure folders and I realize that I accidentally deleted the .config folder which I now realize is important to be able to access my home folder(I came to this conclusion because when I had to restart my computer for some reason... I think it was after emptying the trash... when I try to open any folder the window pops up but there are no icons and its unresponsive). I dont know how to recreate it. Please help.


EDIT: I also don't intend to try to delete old app files anymore....

EDIT 2: Also it seems to only be affecting the home folder.... and a couple of times now the window popped back up in the same condition even after a forced quit....

This is very strange. Are you sure, you did not do any other changes on your system.

If you log out and log in, gnome should recreate your .config folder with the default config files.

---

### Post by opakedragon on 2008-06-05
ok Screw this do you guys know where to get a different file browser so I can access my files and uninstall Ubuntu so I can do a fresh install of 7.10?

---

### Post by yman on 2008-06-05
Did you try to completely remove the package that .config folder belongs to, then installing it?

---

### Post by harrykar on 2010-05-12
> **sisco311 said:**
> This is very strange. Are you sure, you did not do any other changes on your system.

If you log out and log in, gnome should recreate your .config folder with the default config files.

That was true for me. From liveCD i do ```
sudo nautilus
``` --without sudo you can't--
i rename .config folder i.e. .config_old and in the next restart all semms to be ok :) 
Tnx sisco

---

### Post by sisco311 on 2010-05-12
> **harrykar said:**
> That was true for me. From liveCD i do ```
sudo nautilus
``` --without sudo you can't--
i rename .config folder i.e. .config_old and in the next restart all semms to be ok :) 
Tnx sisco

You're welcome!

Yes, from the Live CD you must rename it as root because the home directory is not owned by the Live CD's default user. ;)


Oh, you should always use gksu to run GUI apps as root. See: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by harrykar on 2010-05-12
> **sisco311 said:**
> You're welcome!

Yes, from the Live CD you must rename it as root because the home directory is not owned by the Live CD's default user. ;)


Oh, you should always use gksu to run GUI apps as root. See: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

not really about gksudo Vs sudo. AFAIK gksudo popup a window to insert the pass instead with sudo you insert pass in bash that's all the difference

---

### Post by sisco311 on 2010-05-12
> **harrykar said:**
> not really about gksudo Vs sudo. AFAIK gksudo popup a window to insert the pass instead with sudo you insert pass in bash that's all the difference

By default, sudo doesn't reset the HOME environment variable, so it runs the application with root privileges but it uses the user's configuration files. Some files from the user's home may end up owned by root. If you really want to use sudo then run *sudo -i application*.

---

### Post by QLee on 2010-05-12
[QUOTE=sisco311]By default, sudo doesn't reset the HOME environment variable, so it runs the application with root privileges but it uses the user's configuration files. Some files from the user's home may end up owned by root. If you really want to use sudo then run *sudo -i application*.[/QUOTE]

+1

And, not understanding this significant difference has been the source of many troubles for new users.

---

### Post by harrykar on 2010-05-12
> **sisco311 said:**
> By default, sudo doesn't reset the HOME environment variable, so it runs the application with root privileges but it uses the user's configuration files. Some files from the user's home may end up owned by root. If you really want to use sudo then run *sudo -i application*.

good to know (that's some cmd internals) thank you :)

---

