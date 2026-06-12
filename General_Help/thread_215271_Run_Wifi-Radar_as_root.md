---
title: "Run Wifi-Radar as root"
date: 2006-07-13
forum: General Help
---

### Post by compwiz18 on 2006-07-13
Is there a way to make wifi-radar more like network manager in that you don't have to type in the sudo password everytime you want to open the program?  It gets kind of annoying...

Anyone?

thanks in advance

---

### Post by Ramses de Norre on 2006-07-13
You can add a line for it in /etc/sudoers, easiest way is to do ```
export EDITOR=gedit && sudo visudo
```
and add a line like this: ```
ramses ALL= NOPASSWD: /usr/sbin/firestarter
```
This line would give user ramses permissions to execute /usr/sbin/firestarter without a password, change username and application to your needs.

---

### Post by compwiz18 on 2006-07-13
Hm...that didn't work, it does something, but then it gives me a rather nasty little error.

```

me@computer:~/Desktop$ sudo wifi-radar
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1896, in ?
    import gtk, gobject
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 45, in ?    from _gtk import *
RuntimeError: could not open display

```

Also, I was wondering...once I add that, do I have to run sudo wifi-radar or just wifi-radar to give it root stuff?

Thanks in advance.

EDIT: I found the problem: instead of specifing the host name as "ALL", the host name must be specified as the actual host name.

I entered
```
username username = NOPASSWD: /usr/sbin/wifi-radar
```
in my /etc/sudoers file, but I still have to type the password every time I try to run it using **sudo wifi-radar**...any ideas?

If it matters, I am the admin person on my computer...

EDIT 2: I made it work; you can type **sudo wifi-radar** and it'll run wifi-radar.  BUT I get that error that I posted at the beginning of this message.  And I don't know how to fix it.  Anyone?  Thanks for your help.

EDIT 3: OK, I solved it: I had to run **xhost +** before I ran **sudo wifi-radar**.  The X Server didn't want to accept my connection, apparently.  I also added [B]adam ALL = (ALL) NOPASSWD:/usr/sbin/wifi-radar
[/B] to my /etc/sudoers file.  It lives!! :D

---

### Post by sledhead45 on 2007-02-08
ok this works for me in edgy. FYI what i did was:
add adam ALL = (ALL) NOPASSWD:/usr/sbin/wifi-radar
to my /etc/sudoers file (replace adam with your session username)
add a startup command: xhost +local:root in system -> preferences -> sessions -> startup programs tab. right click wifi-radar icon -> properties and change the command to: sudo wifi-radar
works like a charm. . thanks compwiz18 :)

---

### Post by dkerlee on 2007-03-04
I also had to:
 sudo chmod 777 /etc/wifi-radar.conf
to make it so that when I run wifi-radar as root, I still have access to the conf file that wifi-radar uses.

---

