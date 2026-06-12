---
title: "Could Use Some Help With Taking Over a Folder"
date: 2016-03-11
forum: General Help
---

### Post by mattig89ch on 2016-03-11
hidy ho all,

I started experimenting with setting up an apache server on a vm today, and am trying to take ownership of the /ect/apache2 folder.  I'm trying to take ownership of the folder, so I can edit the apropriate files through the UI.

But every time I enter the "sudo chown -R user:administrator apache2" command it says that its an invalid group.  yet the "groups user" command says I'm apart of the user, adm, cdrom, sudo, dip, plugdev, lpadmin, and sambashare groups.

Unless I'm misunderstanding (which is entirely possible), adm=administrator.

Also, I've tried substituting adm for adminitrators.  Same issue.

Any help would be apreciated

---

### Post by goofprog on 2016-03-11
You could try 
**sudo chmod 660** folder or **sudo chmod +660** folder.

---

### Post by mattig89ch on 2016-03-11
Whats that command do?

---

### Post by bab1 on 2016-03-11
> **mattig89ch said:**
> ... every time I enter the "sudo chown -R user:administrator apache2" command it says that its an invalid group.  yet the "groups user" command says I'm apart of the user, adm, cdrom, sudo, dip, plugdev, lpadmin, and sambashare groups.

There is no *administrator* group.  There used to be a *admin* group IIRC.  That group has been changed to *sudoers*.
> 
Unless I'm misunderstanding (which is entirely possible), adm=administrator.

Also, I've tried substituting adm for [s]adminitrators[/s] administrators.  Same issue.

The only user that can administrate the Linux system is the **_root user_**.  In Ubuntu this is via sudo (**S**witch **U**ser and **DO**).  With no argument the root user is expected.  The group adm is not a substitute for admin.  It is a group that allows a *_mortal_* users (human users) and the *_system_* user *syslog* to access logs at /var/log/.  See ```
ls -l /var/log/|grep adm
drwxr-x--- 2 root              adm        4096 Mar 11 08:18 apache2
-rw-r----- 1 root              adm           0 Feb 16 08:54 apport.log
-rw-r----- 1 root              adm        1576 Feb 15 13:49 apport.log.1
-rw-r----- 1 root              adm         430 Feb  8 13:08 apport.log.2.gz
-rw-r----- 1 root              adm         217 Feb  4 15:30 apport.log.3.gz
-rw-r----- 1 root              adm         220 Jan 22 01:26 apport.log.4.gz
-rw-r----- 1 root              adm         218 Dec 31 14:52 apport.log.5.gz
-rw-r----- 1 root              adm         252 Dec 30 10:01 apport.log.6.gz
-rw-r----- 1 root              adm         391 Dec 26 22:58 apport.log.7.gz
-rw-r----- 1 syslog            adm      104001 Mar 11 13:21 auth.log
-rw-r----- 1 syslog            adm      109358 Mar  6 10:33 auth.log.1
-rw-r----- 1 syslog            adm        8435 Feb 28 09:34 auth.log.2.gz
-rw-r----- 1 syslog            adm       12692 Feb 22 15:21 auth.log.3.gz
-rw-r----- 1 syslog            adm       10371 Feb 14 11:17 auth.log.4.gz
-rw-r----- 1 root              adm       60772 Mar 11 08:10 dmesg
-rw-r----- 1 root              adm       60929 Mar 10 23:15 dmesg.0
-rw-r----- 1 root              adm       16744 Mar 10 20:57 dmesg.1.gz
-rw-r----- 1 root              adm       16971 Mar 10 17:08 dmesg.2.gz
-rw-r----- 1 root              adm       16864 Mar 10 16:55 dmesg.3.gz
-rw-r----- 1 root              adm       16686 Mar 10 15:12 dmesg.4.gz
-rw-r----- 1 syslog            adm     2218450 Mar 11 13:15 kern.log
-rw-r----- 1 syslog            adm     2324177 Mar  6 10:50 kern.log.1
-rw-r----- 1 syslog            adm      378970 Feb 28 09:46 kern.log.2.gz
-rw-r----- 1 syslog            adm      665707 Feb 22 15:39 kern.log.3.gz
-rw-r----- 1 syslog            adm      496730 Feb 14 11:20 kern.log.4.gz
-rw-r----- 1 syslog            adm       35603 Mar 11 13:43 syslog
-rw-r----- 1 syslog            adm     1192402 Mar 11 08:18 syslog.1
-rw-r----- 1 syslog            adm      128905 Mar 10 00:35 syslog.2.gz
-rw-r----- 1 syslog            adm       79775 Mar  9 08:25 syslog.3.gz
-rw-r----- 1 syslog            adm       84591 Mar  8 07:08 syslog.4.gz
-rw-r----- 1 syslog            adm       64036 Mar  7 09:45 syslog.5.gz
-rw-r----- 1 syslog            adm       85757 Mar  6 10:55 syslog.6.gz
-rw-r----- 1 syslog            adm       60645 Mar  5 13:40 syslog.7.gz

```

---

### Post by mattig89ch on 2016-03-14
So, given that the admin group was replaced with sudoers, this command it should be "sudo chown -R user:sudo apache2"?

Just an fyi, I actually kept the username as "user".  I figured it would be best to keep it generic, as this is a virtual machine, on a work machine.

Edit: Yep, that did it!  I now have access to mess with the files inside the folder.  Danke all!

---

### Post by QIII on 2016-03-14
Hello!

Are you following a tutorial (and it would be nice to know what that is)?

You should be very circumspect about changing ownership/permissions of such directories/files.

bab1 provided the answer for gaining the appropriate *temporary* privileges for altering config files in a *non-graphical* environment.  Use "gksudo"/"pkexec" (as appropriate.  Sorry -- I use Ubuntu rarely.  Kubuntu still uses kdesudo) for graphical environments.

---

### Post by mattig89ch on 2016-03-14
I'm not following a tutorial, so much as a general idea of what I want to do.

I'm getting my info from [here]("https://help.ubuntu.com/lts/serverguide/httpd.html") and [here]("https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps").

Urls:
[https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)
[https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps](https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps)

---

### Post by QIII on 2016-03-14
Both good sources.  Digital Ocean has a great wealth of stuff.

So, do you see in either of those any case where you are instructed to change the ownership of directories/files?  If so, to what user?

If you are instructed to modify files, I suggest using 

```
sudo nano /path/to/your/file
```

to do so in the terminal environment -- you don't need to change the permissions of the files.  sudo will elevate you temporarily to the appropriate permission level.

Notice that the Digital Ocean instructions say just that:

```
sudo nano /etc/apache2/sites-available/default
```

You should follow that advice rather than striking out on your own and taking a chance on fouling things up.  When those packages are installed, they are set up with the appropriate permissions for them to run properly.  Changing permissions can, and proably will, keep them from working properly.

A note about "Sharing Write Permission" in the help.ubuntu.com reference:  KISS.  Keep it Simple ...

Unless you have a very good reason to have multiple users write to those directories, don't monkey with ownersip/permissions.

---

### Post by mattig89ch on 2016-03-14
They don't seem like step by step guides to me.  Just giving you what files do what.

though digital ocean does give the advice to change the ports file to listen on 127.0.0.1:80, while your editing the server.  Then changing it back to simply 80, once you've got everything how you like it.

Given how I'm very unfamiliar with using anything but an operating systems ui, I figured I'd go and change the text in the file.  Once I did, and tried to save it, I started getting errors about how I didn't have permission to change the file.  Which is what kicked off this whole thread.

I have no trouble changing it back.  Or removing, then re-installing apache from scratch.  All I need are read/write permissions to the files that folder.  Is there a command to revert any changes made to a folder?

---

### Post by QIII on 2016-03-14
Without knowing exactly which directories you modified the ownership/permissions on, whether you did so recursively, etc, it would be very difficult to tell you exactly how to put it all to rights.

If you have little invested in terms of setting up sites, then it may be just as easy to reinstall Apache and chalk this up to learning.

But if you do that and really want to use a GUI editor, I would suggest 

```
gksudo gedit /path/to/your/file
``` without modifying any directory ownerships/permissions.

Depending on your release, you may have to install gksudo, but you'll get a message with instructions on how to do that when you try to use it.

This is just a tip, and you can take it for what it's worth:  I reckon most of us do not have a GUI installed on our servers, in particular web-facing ones.  Servers should present only the least number of services required to provide what service you want out of them.  In the case of a web-facing server, every extra service (and a desktop with its GUIs runs a LOT of services) is an attack surface.  So the server needs to be cut back to bloody stumps as much as possible.  That being the case, it is really philosophically better to learn it that way than to develop bad habits based on dependence on GUI tools.  Neither my development server sitting next to me nor my live web server 200 miles away from me has any GUI components.  I administer them over SSH on a non-standard port, use public/private keys and run fail2ban.  I give the bad guys as small a target to shoot at as I can -- and put up as many roadblocks as possible on the parts that are exposed.

---

### Post by bab1 on 2016-03-14
> **mattig89ch said:**
> I have no trouble changing it back.  Or removing, then re-installing apache from scratch.  All I need are read/write permissions to the files that folder.  Is there a command to revert any changes made to a folder?
I think it is important that you do understand the basic Linux point of view re: permissions and ownership of file and directories before you start changing things.  I would be everything back to the original defaults and then ask the questions (e.g. how do I do this ... or What do I do to achieve this ...).

The /etc/apache2 directories should never need ownership and permissions changed.  You, as a member of the sudo group can easily edit the files as the root user.  Changing the ownership and permissions for your convenience only creates security risks down the road.  I'd follow @QIII's advice.  In any event*_ no file or directory should ever have the **sudo** group as the group-owner_*.  In a sense the sudo group is a system group to assist the **sudo** command only.

If you feel you just have to use a GUI interface to edit a simple text file the follow @QIII's advice on installing and using gksudo.  I would just learn how to use the command line text editor **nano** and use sudo as a prefix to the command when I needed to switch to root to edit a file.

---

### Post by mattig89ch on 2016-03-15
Fair enough.

My trouble is, I grew up using windows.  From 98, to xp, to 7, then 8, and now 10.  Every once in a while, I'll poke around with linux.  But, given that I'm a PC gamer, and I can't run 2/3 of my gaming library on linux, I always come back to windows.

So I only have very basic knowledge on how to use the command line.  I can barely navigate in it.  So I have no idea how to use the CLI to edit files.  I have no trouble learning, but I really don't even know where to start to learn about it.

oh, and (as far as I know) I only adjusted the "apache 2" folder.  If you look above, you'll see this command: "sudo chown -R user:sudo apache2".  I managed to get to the etc folder, and copied and pasted that command into the cli.

---

### Post by mattig89ch on 2016-03-15
Ok, so I'm going to start a new topic with questions for setting up an apache server.  Thanks for the help all!

---

