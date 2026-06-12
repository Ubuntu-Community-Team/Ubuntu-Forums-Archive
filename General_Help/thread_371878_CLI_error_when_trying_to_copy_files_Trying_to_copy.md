---
title: "CLI error when trying to copy files: Trying to copy VMWare files"
date: 2007-02-27
forum: General Help
---

### Post by caffienda on 2007-02-27
The following is what I get when I try to copy from my /var/lib/vmware/Virtual Machines/ directory to a newly created and mounted RAID array.  I have enven changed the owner and group to my user and the permissions are 777.  Why does it say that the target is not a directory?

:/media/raid$ [COLOR="Blue"]sudo mkdir vmware[/COLOR]
:/media/raid$ [COLOR="Blue"]cd vmware[/COLOR]
:/media/raid/vmware$ [COLOR="Blue"]sudo mkdir vms[/COLOR]
:/media/raid/vmware$ [COLOR="Blue"]cd vms[/COLOR]
:/media/raid/vmware/vms$ [COLOR="Blue"]cd /var/lib/vmware/[/COLOR]
:/var/lib/vmware$ [COLOR="Blue"]cd "Virtual Machines"[/COLOR]
:/var/lib/vmware/Virtual Machines$[COLOR="Blue"] ls -l[/COLOR]
total 12
drwxr-xr-x 2 caffiendo caffiendo 4096 2007-02-27 08:33 2003Web
drwxr-xr-x 2 caffiendo caffiendo 4096 2007-02-27 07:53 Kubuntu
drwxr-xr-x 2 caffiendo caffiendo 4096 2007-02-27 08:30 XP Pro
:/var/lib/vmware/Virtual Machines$ [COLOR="Blue"]sudo cp -rv Kubunt* /meida/raid/vmware/vms[/COLOR]
Password:
[COLOR="Red"]cp: cannot create directory `/meida/raid/vmware/vms': No such file or directory[/COLOR]
:/var/lib/vmware/Virtual Machines$ [COLOR="Blue"]sudo cp -rv Kubunt* /meida/raid/vmware/vms/[/COLOR]
[COLOR="Red"]cp: target `/meida/raid/vmware/vms/' is not a directory: No such file or directory[/COLOR]
:/var/lib/vmware/Virtual Machines$

Also, how can you change to a directory where one of the names has a space in it?

---

### Post by WW on 2007-02-27
Look again at what you typed.  You spelled 'media' incorrectly.

---

### Post by WW on 2007-02-27
> Also, how can you change to a directory where one of the names has a space in it?
Put quotes around the directory:
> $ cd "/var/lib/vmware/Virtual Machines"
or precede the space with a backslash:
> $ cd /var/lib/vmware/Virtual\ Machines

---

### Post by caffienda on 2007-02-27
Well, I'm a little embarrased:redface:   I guess the BASH memory can be a good and bad thing.  I was just pressing up and editing the previous line.  I'll make suer to check these small things from now on. 

Thank you!

---

### Post by Richard Kut on 2007-02-27
Hello caffienda! I think that you will also need a trailing slash on the copy command, like so:

> sudo cp -rv Kubunt* /media/raid/vmware/vms/

---

