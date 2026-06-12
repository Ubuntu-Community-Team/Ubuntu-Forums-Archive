---
title: "2 General Questions here in &quot;General Help&quot;"
date: 2007-06-21
forum: General Help
---

### Post by ghandi69_ on 2007-06-21
1.) My first question has to do with how linux is designed, and the idea of multiple users.  Whenever I install ubuntu, It asked me my name, and a password.  I get my own "home" folder, for which I can do anything in and not type a password.  My question is, if Linux is designed per say to allow for multiple users who do not have permissions to change the system... if I create another user, and give them a password... won't they just be able to type in "sudo blah blah" and be able to make any changes they want??  I guess... what is the difference between my login name vs any other account I make??

2.) My 2nd question has to do with "Force Quit" in KDE... in Gnome.. there is a "Kill" thing in the Menu, where you can just click on the program you want to kill, and it will shut down.. I havent found an equivalent in KDE... is there one??

---

### Post by dbott67 on 2007-06-21
By default, the first account you make is part of the 'admin' group --- meaning that you can make system changes.  Whenever you create new users, you can exclude them from this group and prevent them from installing software, changing system settings, etc.  If you take a look at the /etc/group file, you can see which groups that each user account belongs to:
```
dbott@feisty:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:dbott,nxadmin,david
[COLOR=Purple]...
[/COLOR][COLOR=Purple][I]<snip> edited for brevity </snip>
...
[/I][/COLOR]syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip,dbott,nxadmin,david
nvram:x:105:
messagebus:x:106:
ssl-cert:x:107:cupsys
crontab:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:dbott
lpadmin:x:113:dbott
haldaemon:x:114:
powerdev:x:115:haldaemon,dbott
slocate:x:116:
[COLOR=Red] admin:x:117:dbott,nxadmin,david[/COLOR]
gdm:x:118:
dbott:x:1000:
nx:x:1001:
nxadmin:x:1002:
david:x:1003:
winbindd_priv:x:119:
debian-tor:x:120:
mixmaster:x:121:

```Not sure about question #2 -- Gnome user here.

-Dave

---

### Post by Happy_Man on 2007-06-21
1. Only the user that was created upon installing (eg you) has the ability to type in their password and have sudo work. 

2. In KSysGuard, there is an option under the Process Table tab to kill a process. FYI, KSysGuard is like System Monitor in GNOME.

---

### Post by J@n on 2007-07-06
I worked with KDE for a short time and found the following key combination to be helpful:

CTRL+ALT+ESC

Then click the window / app you ant to "kill"

HTH

J@n

---

