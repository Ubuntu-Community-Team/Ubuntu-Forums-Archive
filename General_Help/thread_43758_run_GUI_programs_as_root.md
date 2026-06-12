---
title: "run GUI programs as root"
date: 2005-06-23
forum: General Help
---

### Post by billiejoex on 2005-06-23
Hi all. I'd like to be able to launch graphical programs from a root shell.
Every time I try to do it I encounter a message like this:
```

root@ubuntu:/etc/init.d # firefox

(firefox-bin:9537): Gtk-WARNING **: cannot open display:

```

---

### Post by nocturn on 2005-06-23
[QUOTE=billiejoex]Hi all. I'd like to be able to launch graphical programs from a root shell.
Every time I try to do it I encounter a message like this:
```

root@ubuntu:/etc/init.d # firefox

(firefox-bin:9537): Gtk-WARNING **: cannot open display:

```[/QUOTE]

How did you login as root?

Is you login as a user and type:
sudo firefox

It should work.

---

### Post by billiejoex on 2005-06-23
Yes but I would like to launch the GUI program _from the root shell_

---

### Post by nocturn on 2005-06-23
[QUOTE=billiejoex]Yes but I would like to launch the GUI program _from the root shell_[/QUOTE]

Then you need to do the following.
1 as the user
xhost +localhost  (or xhost + if the former does not work)

2 become root
export DISPLAY=:0
firefox

Note that setting ACL's on X is a security issue, make sure to run xhost - when no longer needed.

---

### Post by billiejoex on 2005-06-23
> 1 as the user
xhost +localhost (or xhost + if the former does not work)
??

---

### Post by desdinova on 2005-06-23
Running graphical programs as root is a Really Bad Idea - why not run them as the user as you are supposed to do?

---

### Post by Alexander Kirillov on 2005-06-23
[QUOTE=nocturn]Then you need to do the following.
1 as the user
xhost +localhost  (or xhost + if the former does not work)

2 become root
export DISPLAY=:0
firefox

Note that setting ACL's on X is a security issue, make sure to run xhost - when no longer needed.[/QUOTE]
 Instead of 1, you can type 
xhost +local:
(with the colon at the end!)

billiejoex: 
by default, X windows does not allow other users to create windows, etc on your display - for obvious reasons. In particular, it can also block user root from creating a window on a display owned by billijoex (or whatever your normal user name is).

The above command  allows other users logged on the same computer (in particular, root) to create windows and otherwise use the display.

---

