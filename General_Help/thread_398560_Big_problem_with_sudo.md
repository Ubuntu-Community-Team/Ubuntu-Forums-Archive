---
title: "Big problem with sudo"
date: 2007-04-01
forum: General Help
---

### Post by Doomsword on 2007-04-01
Hi everybody, I've got a big problem with SUDO . My SO is edgy with root disabled, I'm using (was using...) sudo with user "xxxxx" that is the default installation user.
I've created a new group "usb" and I was trying to put my user "xxxxx" in that group, so i launched :

sudo usermod -G usb "xxxxx"

(it is correct to leave a space between "-G" and "usb" ???)
After that command I can't use sudo anymore. I think that my user "xxxxx" lost admin user rights. Launching anything as "sudo pon ..." doesn't give any result.
Thanks in advance to everyone who will help me

Fabio

---

### Post by teaker1s on 2007-04-01
ubuntu 

boot recovery and you will be in as root then example
```
visudo
```
then this is sudoers file, provided you are in admin group you should be okay
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

```
apt-get update
```
```
startx
``` to start root gui session
look at your user in users and groups-tick boxes and make sure your in admin group

logout
```
reboot
```

---

### Post by Doomsword on 2007-04-01
Thanxxxx, it worked !!! What I was doing wrong with "usermod" command?
-G switch allow to add user to a group leaving existing group appartenance, is it correct?
I'd like to put my user in "admin" group ... how can I do that?

Thank you very much, I was so sad :-/ (it's all my fault, I know !!!!)

---

### Post by teaker1s on 2007-04-01
being honest, I'm not sure as I use gui and as I'm the only one on my pc I've not played with users and groups.

All we did was basically repair any errors in either sudoers file or your user rights. I'd suggest reading the manual and it could either be a wrong command or something as simple as a typo that caused it

regards Daniel 

:guitar: :guitar: :guitar:

   >  -g, --gid GROUP
          The group name or number of the user&#8217;s new initial login group. The
          group name must exist. A group number must refer to an already
          existing group. The default group number is 1.

       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
          A list of supplementary groups which the user is also a member of.
          Each group is separated from the next by a comma, with no
          intervening whitespace. The groups are subject to the same
          restrictions as the group given with the -g option. If the user is
          currently a member of a group which is not listed, the user will be
          removed from the group. This behaviour can be changed via -a option,
          which appends user to the current supplementary group list.



---

### Post by zvacet on 2007-04-01
Your first user(administrator) is in admin group wich gives him sudo privileges.Adduser is for everyday work and puting him in admin group in redundant.In that case you have two administrators.But if you wish to do i anyway here it is
```
sudo adduser username group
```

---

