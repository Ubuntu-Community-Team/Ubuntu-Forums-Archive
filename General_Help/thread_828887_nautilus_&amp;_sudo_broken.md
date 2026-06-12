---
title: "nautilus &amp; sudo broken"
date: 2008-06-14
forum: General Help
---

### Post by crazyfuturamanoob on 2008-06-14
I tried to run nautilus with sudo rights:
> timo@timo-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
timo@timo-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
timo@timo-desktop:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault
timo@timo-desktop:~$ 
But nautilus wont start!! Help!
And I got a folder and files in my home folder
that I can't delete. I don't have rights for
that. I accidentally messed up the file and folder
rights so now nobody has rights to delete or edit
them.

---

### Post by VMC on 2008-06-14
> **crazyfuturamanoob said:**
> I tried to run nautilus with sudo rights:

But nautilus wont start!! Help!
And I got a folder and files in my home folder
that I can't delete. I don't have rights for
that. I accidentally messed up the file and folder
rights so now nobody has rights to delete or edit
them.

Have you tried this fix launching Nautilus. There's a reported bug

```
gksudo dbus-launch nautilus
```

---

### Post by underdog512 on 2008-06-14
> **crazyfuturamanoob said:**
>  I accidentally messed up the file and folder
rights so now nobody has rights to delete or edit
them.

You could either try running as root in the terminal by runing

```
sudo su
``` 

or you can boot into recovery mode as root.

---

### Post by Joeb454 on 2008-06-14
Just use ```
sudo rm ~/file-to-delete
```

~/ is an alias for /home/USER/ :)

Edit: Also note, that you should *never* use ```
sudo nautilus
```

---

### Post by crazyfuturamanoob on 2008-06-16
Every poster here has given different instructions to fix this.
What should I do? Which command to run of all those?? Everything is
so confusing.. :confused::confused::confused:

---

### Post by crazyfuturamanoob on 2008-06-16
> **VMC said:**
> Have you tried this fix launching Nautilus. There's a reported bug

```
gksudo dbus-launch nautilus
```

I want a solid solution that 
will fix the problem permanently.

---

### Post by mssever on 2008-06-16
> **crazyfuturamanoob said:**
> I want a solid solution that 
will fix the problem permanently.
Joeb454 posted such a solid solution to being unable to delete those files. As far as your Nautilus problems go, try the various suggestions. True, they smell of workarounds, but we can't solve your nautilus problem until we know *why* gksudo nautilus doesn't work. Hopefully, someone with some skill in troubleshooting those problems will post here. Also, try searching around--sometimes putting the output (and maybe your command, too) into Google works wonders.

---

### Post by crazyfuturamanoob on 2008-06-17
> **mssever said:**
> Joeb454 posted such a solid solution to being unable to delete those files. As far as your Nautilus problems go, try the various suggestions. True, they smell of workarounds, but we can't solve your nautilus problem until we know *why* gksudo nautilus doesn't work. Hopefully, someone with some skill in troubleshooting those problems will post here. Also, try searching around--sometimes putting the output (and maybe your command, too) into Google works wonders.
I already figured out how to delete the files.
My problem is, how to get nautilus working again.
But this time I ran "gksudo nautilus", nautilus
succesfully launched. I didn't test does it work,
I just opened and then closed it. Here's the output:
> arho@timo-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: komento 'net usershare' palautti virheen 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6342): WARNING **: Unable to add monitor: Toiminto ei ole tuettu
seahorse nautilus module shutdown
arho@timo-desktop:~$ 


---

