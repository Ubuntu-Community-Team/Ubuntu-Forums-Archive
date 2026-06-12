---
title: "GUI for starting and stopping services"
date: 2004-10-29
forum: General Help
---

### Post by steffen on 2004-10-29
When I used Fedora there was a panel under the System Settings menu called 'Services' which listed an array of services on the computer, which were running, which were not, and which were automatically starting up with the computer. I could also define this in the monitor.

Anyone know if something similar exists for Ubuntu/Debian?

1) I installed Zope, and now it's running in the background all the time. How do I shut this down?

2) I would like to optimize performance by going through what is running and turning off/on.

Thanks!

---

### Post by cacofonix on 2004-10-29
I think there is something like that installed open the application menu go to system tools and then click on system monitor.

is that what your looking for?

---

### Post by steffen on 2004-10-29
I'm actually looking for a place where I can find Kudzu, httpd, irda, zopectl, and those kind of things...

The system monitor only shows things running in X it seems...

---

### Post by grj on 2004-10-29
I am not familiar with a tool that has a gui, but rcconf is a great tool and easy to use.

grj

---

### Post by FLeiXiuS on 2004-10-29
Im sure there is one out there for a debian system.  I don't know of any for Ubuntu.  Please check freshmeat.net for some projects.

---

### Post by macsaint on 2004-10-29
Maybe you can use webmin.. web based administration tool..

Good luck!

---

### Post by jdong on 2004-10-29
ksysv/ksysvedit??

---

### Post by kaput on 2004-10-30
I think what your looking for is part of the GNOME System Tools set. Take a look at the "Runlevel Editor."

[http://www.gnome.org/projects/gst/](http://www.gnome.org/projects/gst/)

I'm surprised that Ubuntu didn't include that particlular part of the tool set. 

[QUOTE=steffen]When I used Fedora there was a panel under the System Settings menu called 'Services' which listed an array of services on the computer, which were running, which were not, and which were automatically starting up with the computer. I could also define this in the monitor.

Anyone know if something similar exists for Ubuntu/Debian?

1) I installed Zope, and now it's running in the background all the time. How do I shut this down?

2) I would like to optimize performance by going through what is running and turning off/on.

Thanks![/QUOTE]

---

### Post by kamstrup on 2004-11-03
I am also missing the runlevel editor of the gnome system tools... I am not sure I dare to go about installing these from scratch...

---

### Post by ulrich on 2004-11-03
but the gnome system tools should be there...  somewhere...

```

root@myMachine ~ # apt-cache show gnome-system-tools
Package: gnome-system-tools
Priority: extra
Section: gnome
Installed-Size: 6972

Description: Cross-platform configuration utilities for GNOME
 The GNOME System Tools are a fully integrated set of tools aimed to make easy
 the job that means the computer administration on an UNIX or Linux system.
 They're thought to help from the new Linux or UNIX user to the system
 administrators.
 .
 Its main advantages are:
  * Full integration with the new GNOME Control Center.
  * An user-friendly interface to carry out the main administration tasks.
  * The use of a common user interface in every system.
  * A common structure that makes easy the development of new system tools.
 Nowadays there are tools for managing:
  - Users and groups
  - Date and time
  - Network configuration
  - Bootloaders
  - Runlevels
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop

```

---

### Post by kaput on 2004-11-03
[QUOTE=ulrich]but the gnome system tools should be there...  somewhere...[/QUOTE]

Some of the GST *are* included, but the runlevel editor seems to be missing.

---

### Post by JsPr on 2004-11-03
There are this already in Ubuntu:

sysv-rc-conf

It's CLI but looks OK I think.

---

### Post by tariq on 2004-11-03
i think the original poster is looking for something like **drakxservices **for mandrake. i know that redhat has somerthing similar.

a simeple text/gui tools that:
1. shows which of the registered services are running
2. shows which are set to start at boot (or other runlevel)
3. allows you to change (2)
4. allows you to manuall start/stop servoces

it would be very useful. i'm not familiar with debian but i doubnt its all on an /etc/rc.conf file as per BSD.

---

### Post by JsPr on 2004-11-03
[QUOTE=tariq]i think the original poster is looking for something like **drakxservices **for mandrake. i know that redhat has somerthing similar.

a simeple text/gui tools that:
1. shows which of the registered services are running
2. shows which are set to start at boot (or other runlevel)
3. allows you to change (2)
4. allows you to manuall start/stop servoces

it would be very useful. i'm not familiar with debian but i doubnt its all on an /etc/rc.conf file as per BSD.[/QUOTE]
 Well,
I believe sudo sysv-rc-conf will do most of what you are asking for.
It's kind of graphical but in a terminal. :-)

---

### Post by tariq on 2004-11-03
i must say the level of helpful support here is excellent. a pleasure. and i am feeling very confident about moving from mandrake (which i know enough to support myself) ontop ubuntu because i know that people like those here will be klind enough to make that transition easy.

good karma! 

*gods. cipher. love. divine. *

---

### Post by steffen on 2004-11-03
Yep, that's what I'm looking for - the GST Runlevel Editor!

[http://www.gnome.org/projects/gst/screenshots/runlevel.jpg](http://www.gnome.org/projects/gst/screenshots/runlevel.jpg)

That's what's missing!

Anyone know how to get it?

---

### Post by trico on 2004-11-03
[QUOTE=JsPr]Well,
I believe sudo sysv-rc-conf will do most of what you are asking for.
It's kind of graphical but in a terminal. :-)[/QUOTE]

I'm missing something - can't find sysv-rc-conf...
larry@trico:~ $ sudo sysv-rc-conf
Password:
sudo: sysv-rc-conf: command not found

Trico

---

### Post by JsPr on 2004-11-03
sysv-rc-conf is in a package with the same name. You might find it in synaptic (I did). Perhaps you will have to enable the universe repository (settings/repository) in synaptic.

---

### Post by steffen on 2004-11-03
The sysv-rc-conf did the trick

I would prefer the GST Runlevel Editor though - I'm very surprised Ubuntu - with the commitment to ease of use and GUI - haven't included it.

I'm expecting it in Hoary :)

---

### Post by trico on 2004-11-03
Ah yes - forgot to enable the universe. 

Thanks,
Trico

---

