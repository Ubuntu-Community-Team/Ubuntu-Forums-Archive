---
title: "Mtink utility for printers"
date: 2005-04-19
forum: General Help
---

### Post by SilvioTO on 2005-04-19
Hi; I tryed to install Mtink for monitor ink status on my Epson Stylus C84 printer.

During the installation of packages the follow message appear:

Warning! Mtink requires special permissions for the device file associated with the printer. You should check your permission to see if users that could run mtink should also access this file. If you have got a normal Debian installation, this group should be lp.

I verifyed in the permission setting and Printer is checked. I don't understand if the printer permission comprise "lp" permission.

 When I launch mtink an error about comunication problem with printer appears. If I launch it as root, a wizard for configure printer appear but at the end mtink freeze and I must use xkill to close. any idea?

Thanks.

---

### Post by bonjun on 2005-10-07
this is also appear on my installation on mtink...

> Warning! Mtink requires special permissions for the device file associated with the printer. You should check your permission to see if users that could run mtink should also access this file. If you have got a normal Debian installation, this group should be lp.


please help...

thanks

---

### Post by andoty_jazz on 2007-03-19
Good morning to all.

I got this message when openning "mtink."

[B]No access to printer device file.
Please make sure that mtink has enough right for accessing the device files.
[/B]

Please help.

BTW, mtink works fine if you have access rights, super user do (sudo)

1.) In the command line, just type, sudo mtink.

2.) I selected the **/dev/usblp0** for the **Port Choice**.

3.) my printer model is EPSON STYLUS C45.  I selected **Stylus C42UX** for the **Printer Choice** and it gave me all the functionalities I needed.

4.) firefox the documentation. file:///usr/share/doc/mtink-doc/html/mtink.html
What I wanted for help right now is how will I use "mtink" as a normal user without admin privileges/rights/permissions?

PLEASE. Help, help, help.

Thanks in advance.

---

### Post by rsay on 2007-05-20
The user needs to be added to the lp group. I don't know how to do this from the gui but from the command line.

open the file /etc/group with your editor of choice, I use nano but gedit is probably more user friendly

```
sudo gedit /etc/group
```

Look for a line like this

```
lp:x:7:cupsys
```

And change it to

```
lp:x:7:cupsys,myusername
```

Save, exit and enjoy. 

Now when you set up the menu item for mtink you won't need to use  "gksu mtink"  command  to start the program anymore, change the command to just "mtink"  so it won't prompt you for your admin password.

btw, I don't know if this causes any security risk or not. I just didn't like typing my password to check ink levels. More importantly, my parents don't need things to be any more difficult than absolutely necessary.

---

### Post by RedSquirrel on 2007-05-20
> **rsay said:**
> The user needs to be added to the lp group. I don't know how to do this from the gui but from the command line.

open the file /etc/group with your editor of choice, I use nano but gedit is probably more user friendly

```
sudo gedit /etc/group
```


```
 **gksudo** gedit /etc/group
```but it's easier to just do:

```
sudo adduser username lp
```

---

### Post by Mark Phelps on 2007-08-10
That's fine if your machine has an 'lp' group -- which mine does not.  Mine has an 'lpadmin' group -- of which my userid is already listed as a user.  And, I still have to use 'sudo' to run mtink!

When I do 'sudo mtink' in a terminal, it works fine; but when I create a menu entry on the Applications menu that has the same command, I get no output.

I was hoping this thread would answer the permissions question -- but it hasn't, at least, so far.

I've posted a different thread on the Beginners forum asking about how to fix the apparent permissions problem so I can launch mtink from a menu entry -- but haven't received any reply.

---

### Post by RedSquirrel on 2007-08-11
> **Mark Phelps said:**
> That's fine if your machine has an 'lp' group -- which mine does not.  Mine has an 'lpadmin' group -- of which my userid is already listed as a user.  And, I still have to use 'sudo' to run mtink!

When I do 'sudo mtink' in a terminal, it works fine; but when I create a menu entry on the Applications menu that has the same command, I get no output.

I was hoping this thread would answer the permissions question -- but it hasn't, at least, so far.

I've posted a different thread on the Beginners forum asking about how to fix the apparent permissions problem so I can launch mtink from a menu entry -- but haven't received any reply.

If you make it a menu item, I would try it with **gksudo**:

```
gksudo mtink
```

OR use **kdesu** if you're on KDE. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).


Here's an excerpt from /usr/share/doc/mtink/README.Debian:

> -----------------
* Setting mtink *
-----------------

1) User groups:
In order to use mtink you should have access to /dev/lpXX. Check 
your permission on this file. 

In a standard Debian install, this device is crw-rw---- and is 
own by root:lp. You should belong to lp group to have access to the 
device.
I have a USB printer and when I turn it on it shows up as /dev/usblp0. It allows users in the lp group to access it.

Can you post the output of:

```
ls -l /dev/lp*
```and (if it's a USB printer)

```
ls -l /dev/usblp*
```I would like to see what's going on. (or if you're content to just use gksudo, that's fine too :))


EDIT:

I just read your post in the [other]("http://ubuntuforums.org/showthread.php?t=521009") thread.

On my system, 'ls -l /dev/usblp0' shows:

```
 crw-rw---- 1 root lp 180, 0 2007-08-11 14:02 /dev/usblp0
```What does your system show?

---

### Post by Mark Phelps on 2007-08-11
Thanks for the response.  I tried gksudo, but since mtink needs some parameters to work right, the command fails.

Here's the output of the commands:

bill@bill-ubuntu:~$ ls -l /dev/lp*
crw-rw---- 1 root lp 6, 0 2007-08-11 22:20 /dev/lp0
bill@bill-ubuntu:~$ ls -l /dev/usblp*
crw-rw---- 1 root lp 180, 0 2007-08-11 22:20 /dev/usblp0
bill@bill-ubuntu:~$ ls -l /dev/usblp0
crw-rw---- 1 root lp 180, 0 2007-08-11 22:20 /dev/usblp0

Now, when I did this a couple of days ago, there was no "c" in front of the first "rw" -- but now, there is.

So, it looks just like your output.

---

### Post by RedSquirrel on 2007-08-12
> **Mark Phelps said:**
> Thanks for the response.  I tried gksudo, but since mtink needs some parameters to work right, the command fails.

Here's the output of the commands:

bill@bill-ubuntu:~$ ls -l /dev/lp*
crw-rw---- 1 root lp 6, 0 2007-08-11 22:20 /dev/lp0
bill@bill-ubuntu:~$ ls -l /dev/usblp*
crw-rw---- 1 root lp 180, 0 2007-08-11 22:20 /dev/usblp0
bill@bill-ubuntu:~$ ls -l /dev/usblp0
crw-rw---- 1 root lp 180, 0 2007-08-11 22:20 /dev/usblp0

Now, when I did this a couple of days ago, there was no "c" in front of the first "rw" -- but now, there is.

So, it looks just like your output.
So, does it work properly now? (i.e., by adding yourself to the lp group)

---

### Post by Mark Phelps on 2007-08-12
OK, I just tried it again and, yes, in fact, it DOES work properly now -- but I haven't done anything.  I just ran the commands you indicated and pasted the output into the post.

---

### Post by holdup on 2007-11-11
Here's how I got around the problem

1) Open up a terminal  type gksudo nautilus
2) Navigate to the /dev/usb directory
3) My printer in there is called lp0 I suspect yours will be too if it is the only usb printer.  Right click on the lp0 file and click ***Properties*** then click on the ***Permissions*** tab.  You will probably have Owner - root, Group lp, Others : None or Read only,  set the others tab to be Read and Write.
4) now run mtink from the command line as a user (i.e. without sudo) or from a shortcut in the menu/panel.

Hope this helps


Andyb

---

### Post by Pipps on 2008-07-06
@ holdup
Your suggestion worked for me - thanks.

However, I had to use terminal and be logged in as root using the command 'sudo -i' in order to be able to launch mtink and for it to work following your advice.

Just continuing trying to launch mtink from the icon that Synaptic Package Installer placed on my Accessories menu does not work.

---

### Post by RedSquirrel on 2008-07-07
/dev/usb/lp0 is created dynamically when you attach the printer. It should automatically have rw permissions for root and for members of the lp group. I think it's better to simply add your user to the lp group.

---

