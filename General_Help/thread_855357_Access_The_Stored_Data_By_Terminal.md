---
title: "Access The Stored Data By Terminal"
date: 2008-07-10
forum: General Help
---

### Post by Uchiha_madara on 2008-07-10
Hi Every One >>>


I need to Ask How can I Open, Access , Make Directories , and delete inside the Hard disk to reach the Other Storage Media As Flash Disk, Or The NTFS Drive By Using the Terminal

Because there is Sometimes Folders I can't delete them Directly

and a message that :
> Access Denied you don't have a Privilege to Delete  

and I must to be Root to delete it :
and i know this Command to Connect as root in the Terminal:

> sudo su root

so I need how to Access The "Computer" and reach The Storage Media by Terminal

Thank u:guitar:

---

### Post by HalPomeranz on 2008-07-10
I think you'll be much happier just doing "sudo nautilus".  That will pop up a file browser running with root privileges, which should allow you do delete any folder you want to.

Obviously, you need to be VERY CAREFUL that you don't accidentally delete too much.

---

### Post by inevaexisted on 2008-07-10
if you must insist on using terminal though what Uchiha_madara said should work

change directory
```
cd <directory>
```

note you can navigate to your home directory(/home/username/) by entering 
```
cd
``` or ```
cd ~
```

make directory
```
mkdir <directory name>
```

delete directory
```
rmdir <directory name>
```

delete file
```
rm <file>
```

if you need to know more about those commands type
```
man <command>
```
and you'll get a description of how to use the command as well as its options

That should be enough to get you started.

-Ineva

---

### Post by bodhi.zazen on 2008-07-10
For root access :

```
sudo -i
```

For graphical apps use gksu (kdesu on KDE)

```
gksu natuilus
gksu gedit
```

For how to use the command line :

    [http://linuxcommand.org/](http://linuxcommand.org/)

---

