---
title: "I am not allowed to shutdown my system in xubuntu gutsy"
date: 2007-10-20
forum: General Help
---

### Post by deformation on 2007-10-20
thats what is shows me (picture attached) :

[IMG]http://img.photobucket.com/albums/v225/DeforMatiOn/Screenshot0.png[/IMG]

i didnt shange anything with my account, and i am an admin in this laptop


please guys any help?

---

### Post by kerry_s on 2007-10-20
you got to->
in terminal

[B]sudo visudo

%shutdown ALL=(root) NOPASSWD: /usr/sbin/xfsm-shutdown-helper[/B]

then add yourself to the shutdown group->

**gksudo mousepad /etc/group**

---

### Post by deformation on 2007-10-20
i ran sudo visudo, but then i didnt know what to do :(
is this meant to add me to the shutdown group? i am already added there with admin rights. so whats the point?

---

### Post by kerry_s on 2007-10-20
> **deformation said:**
> i ran sudo visudo, but then i didnt know what to do :(
is this meant to add me to the shutdown group? i am already added there with admin rights. so whats the point?

add this->
**%shutdown ALL=(root) NOPASSWD: /usr/sbin/xfsm-shutdown-helper**

to visudo

here's the reason->
[http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfsm-shutdown](http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfsm-shutdown)

---

### Post by Page on 2007-10-20
Plan B:

If you can't shut down properly any other way, try running these:

sudo init 0 (shuts down the system)

or

sudo init 6 (reboots the system)

---

### Post by Compyx on 2007-10-20
> **deformation said:**
> i ran sudo visudo, but then i didnt know what to do :(
is this meant to add me to the shutdown group? i am already added there with admin rights. so whats the point?

Visudo launches Vim, so you'll have to press 'i' to start editing and once you're done you'll have to press <Esc>:wq<Enter> to save the file and exit.

---

### Post by deformation on 2007-10-20
> **kerry_s said:**
> add this->
**%shutdown ALL=(root) NOPASSWD: /usr/sbin/xfsm-shutdown-helper**

to visudo

here's the reason->
[http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfsm-shutdown](http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfsm-shutdown)

what i meant is that i didnt know how to add the line after the visudo, this is my first time using vi, i didnt know how to save and exit after adding the line,, sorry for the total noobness :)

---

### Post by deformation on 2007-10-20
its ok now, i edited it with sudo gedit /etc/sudoers.tmp

its still the same, i will hard shutdown the system and check it out again. brb

---

### Post by deformation on 2007-10-20
that did not help, its still the same :(

---

### Post by kerry_s on 2007-10-20
sudo visudo should launch nano.

you add the line on the bottom, make sure to leave a empty line on the bottom.

press ctrl+x and y and enter to save


you can not edit the sudoers with a regular editor, cause the file is set up for no write.

i'm not using xfce4 so mine looks different but it should give you a idea of what it looks like.->

(just in case yours is set to vi, you can change it by running> sudo update-alternatives --config editor <and pick nano by it's number or better yet mcedit if you have mc installed, i use mcedit on mine)

---

### Post by deformation on 2007-10-20
kerry_s

i did add the line, but i dont know how to save and exit

whats <Esc>:wq<Enter> ?

i am pressing Esc and enter at the same time with no responce!! how do i save and exit?

---

### Post by Compyx on 2007-10-20
<Esc>:wq<Enter> means you push Escape, then type :wq and push enter. This is when visudo launches Vi or Vim. If visudo launches Nano then you should be able to save and exit with Ctrl+O, Ctrl+X.

---

