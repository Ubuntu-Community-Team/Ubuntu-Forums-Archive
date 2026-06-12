---
title: "Holy wow, something is REALLY messed up"
date: 2008-05-03
forum: General Help
---

### Post by Mateo on 2008-05-03
For no known reason, I wake up today and turn my computer on and nothing seems to be working.  Gnome is not showing any panels, or it's proper theme, nautilus is not showing a desktop background.  most of the normal gnome stuff, like shortcuts such as alt+f2 to open the application launch window, don't work.  i can only launch applications by going to one of the tty terminals and using --display :0 .  i get an error for almost every application I open.  here are the errors I get every time gnome starts:

```
An error occurred while loading or saving configuration information for Nautilus. Some of your configuration settings may not work properly.
```

```
GConf error: Configuration server couldn't be contacted: CORBA error: IDL:omg.org/CORBA/BAD_OPERATION:1.0
```

```
The application "gnome-panel" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.
```

```
An error occurred while loading or saving configuration information for gnome-session. Some of your configuration settings may not work properly.
```

```
An error occurred while loading or saving configuration information for Encryption Key Agent (Seahorse). Some of your configuration settings may not work properly.
```

```
The application "evolution-alarm-notify" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.
```

```
An error occurred while loading or saving configuration information for update-notifier. Some of your configuration settings may not work properly.
```

For an example of one when I launch an application, here's what it says when i start gedit:

```
An error occurred while loading or saving configuration information for Text Editor. Some of your configuration settings may not work properly.
```

obviously there has got to be some core problem here.  not sure what that could be.  i tried going into wmii instead of gnome and got some similar problems.  Could x11 be the culprit?

---

### Post by Mateo on 2008-05-03
heh.  Nevermind.  Seems all I had to do was restart my computer to make the problem go away. I guess some daemon didn't start properly.

---

### Post by zorblek on 2008-11-18
I am having this exact same problem in Intrepid. I have no idea what caused it. Unfortunately, restarting doesn't fix the problem. I've tried booting in recovery mode and using the older kernel; neither helped.

Another error I'm getting: "GConf error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))"

Also, Pidgin starts automatically but appears to have lost all my account data (it shows the "Welcome to Pidgin!" setup dialog).

Anybody know what could be causing this? I am stumped.

---

### Post by madmax1735 on 2009-01-14
hey i am having the same problem........... how to fix this 


help....

---

### Post by zorblek on 2009-01-14
I never did figure it out. I eventually just did a clean install. Sorry I can't be of more help... :(

---

### Post by sandyeggoboy on 2009-01-15
Hi guys, i am also having this problem. 

 
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Could not send message to gconf daemon: Connection was disconnected before a reply was received)
deric@debian:~$

---

### Post by voilsb on 2009-01-31
So I take it nobody's found a fix for this? Just wiped your system and installed again? Installed another version? Dealing with it, and not using half your applications?

I get this same error with every gnome application I use, including Firefox. I just upgraded from ubuntu 8.04 to 8.10, and it happened via this update. It sucks, and I don't have a clue how to fix it. I would rather not download an 8.04 installation cd and downgrade, just to fix this.

---

### Post by sandyeggoboy on 2009-01-31
yeah, i re-installed .

---

### Post by voilsb on 2009-02-01
I fixed it, without reinstalling.

Somehow, my ~/.dbus directory and it's contents were owned by root. I did a 'sudo chown -R me.me .dbus' and everything works fine now.

---

### Post by [ITA]ArgH on 2009-02-02
Same problems here, with GConf... It happened after an upgrade... Really there's no way to solve it??

---

### Post by voilsb on 2009-02-02
will it let you run it as root? Do you have similar problems with other gnome apps? If so, check your .dbus. Failing that, try deleting both your .dbus and your system /etc/dbus* directories, and mark it for reinstallation.

---

### Post by adebree on 2009-02-04
Having the same problem here. Reinstalling dbus didn't fix it.

Dmesg does share something interesting though:

metaticy[6953]: segfault at 0 ip 080abab3 sp bfd91cd0 error 4 in metacity[8048000+7a000]

---

### Post by voilsb on 2009-02-04
> **adebree said:**
> Having the same problem here. Reinstalling dbus didn't fix it.

Dmesg does share something interesting though:

metaticy[6953]: segfault at 0 ip 080abab3 sp bfd91cd0 error 4 in metacity[8048000+7a000]

I dunno, then. It didn't help me when I reinstalled dbus, myself ... because my .dbus directory was owned by root for some reason.


A big thing to check, though ... do your apps work when run as root? Try running your problem app with sudo. If it works, it's probably a permission issue somewhere along the line. If it doesn't, then maybe it's time to strace or set logging to a debug level.

---

### Post by ibharathy on 2009-02-05
logout the desktop by pressing alt+ctrl+backspace

press ctrl+alt+F1 to go the terminal 

if you remove the /tmp/gconfd-username/lock

as root
> 
cd /tmp/gconfd-username/

> rm lock



this solved the problem.

---

### Post by whiztec on 2009-12-06
Was having the same problem. But found the solution after a lot of trial n error. Try this;

**# locate saved_state**
 (will giv out 2 findings, in /home/username directory and in /root directory)
**# cd /home/username/.gconfd**
**# ls**
(will show a file by the name "saved_state")
**# rm -rf saved_state**
(this will delete the file)
**# reboot**
(when the machine reboot, a fresh copy of the saved_state file will be generated and this should solved the problem)

---

### Post by rlaynegreene on 2010-01-05
I got this error when launching an x-server into my oracle account on solaris 10 using both omni-x and reflection-x x-server programs.  After trial and error I su'ed into the root user on solaris 10 and removed all the files and directories in /var/tmp.  From my oracle account I then removed all .gnome* and .gconf* files.  The errors went away.

---

### Post by Richard1979 on 2010-02-04
> **whiztec said:**
> Was having the same problem. But found the solution after a lot of trial n error. Try this;

**# locate saved_state**
 (will giv out 2 findings, in /home/username directory and in /root directory)
**# cd /home/username/.gconfd**
**# ls**
(will show a file by the name "saved_state")
**# rm -rf saved_state**
(this will delete the file)
**# reboot**
(when the machine reboot, a fresh copy of the saved_state file will be generated and this should solved the problem)

Sorry to bump this old thread, but I found this while looking up the same error that I have been having.
Had to log in to say, can you NOT request that people use the -r flag when using the "rm" command to delete a single file - it's dangerous and irresponsible.

---

### Post by everytimeref on 2010-02-05
I had a similar problem yesterday. No gnome at all, luckily I still had Cairo-dock so was able to open firefox and JFGI the problem.

I did the following:


If you don’t have access to your graphical (GUI) desktop to delete these folders in Nautilus or you’re stuck at the login screen, drop to a terminal by hitting CTRL + ALT + F1, login to your account, and run this command:

    rm -rf .gnome .gnome2 .gconf .gconfd .metacity

which I found on Linux FUD.

Note this is fairly drastic as it totally resets gnome to ubuntu standard.

The one major problem I had (after making my computer pretty again) was Evolution.

Evolution reset thinking it was a fresh install and could not accept the .evolution folder as a "proper" backup in the end I had an idea, I found out that the Evolution backup folder is called evolution-backup.tar.gz. so I simply compressed my existing evolution folder using Nautilus renaming it us above. I then selected my compressed folder as an Evolution backup file that evolution asks for at launch and it worked!!!

---

### Post by Fitch on 2010-04-24
Exactly the same problem.
Did as whiztec said, but without the -rf

i.e [B]
cd .gconfd
sudo rm saved_state

[/B]Hey Presto!

---

### Post by chimaster_ca on 2010-06-04
Just in case the previous suggestion still didn't fix your problem (like me). I'm using CentOS 5.3 and had the exactly same problem. Here is the fix:

First ssh to your machine and check the message file under /var/log.

The last part of my messages file showed:
Jun  4 04:08:18 mboot-dell gconfd (root-10001): starting (version  2.14.0), pid 10001 user 'root'
Jun  4 04:08:18 mboot-dell gconfd (root-10001): Bad permissions 777 on  directory /tmp/gconfd-root
Jun  4 04:08:18 mboot-dell gconfd (root-10001): Failed to get lock for  daemon, exiting: Directory /tmp/gconfd-root has a problem, gconfd can't  use it

Change the permission to 700 for /tmp/gconf-xxxx directory where xxxx is the user name.

Hope it helps.

J

---

### Post by mayaofr on 2011-09-07
Do you use full screen when login.

I tried many times, with the same error:
```
An error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.

```

Even I can not login as <username>, I tried manyways, but suddenly there is no errors happens, I don't know why, I just login without full screen.

---

