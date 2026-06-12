---
title: "Cannot Launch Root GUIs"
date: 2021-04-06
forum: General Help
---

### Post by Quarkrad on 2021-04-06
Running mate 18.04.  For some reason I can no longer open apps owned by root. For example Synaptic or gparted.  The gui attempts to open and then crashes.  I can open them via the terminal like sudo synaptic (then have to put in the password) but cannot launch the gui. Any advice appreciated to correct this.

---

### Post by tea for one on 2021-04-06
You have described a similar (now repaired) situation where gparted and synaptic would only work in a X11 session.
If I remember correctly, Ubuntu 18.04 with Gnome exhibited this but it is OK in 20.04

Are you in a Wayland session at the moment?
```
echo $XDG_SESSION_TYPE

```

---

### Post by Quarkrad on 2021-04-06
Using your command I'm running X11

---

### Post by cmcanulty on 2021-04-06
That is a "feature" of the new Ubuntus here are 2 fixes

   For root access to graphical applications:  

  1)temporary fix without logging out:

 ```

  xhost  +SI:localuser:root
```

  2) permanent fix

  edit or create file in/home/cmcanulty 

  name it ./xinitrc and put in text below

```
   xhost   +localhost  &

```

---

### Post by TheFu on 2021-04-06
Really shouldn't run sudo with GUI programs without the -H option.  It will make some files in the non-root user's HOME incorrectly owned by root.  That's why we tell people new to Linux not to run GUI programs as root/using sudo.  It is possible to have some gnome settings owned by root and not be able to login anymore.

Try:
```
sudo -H synaptic
```

To fix the other, most likely problem, - that's files in HOME owned by root, just run
```
sudo chown -R $USER ~/
```
That should change all the owners to your userid and do no harm.  In theory.

---

### Post by Quarkrad on 2021-04-07
I have not explained myself clearly.  The default way the graphical synaptic application works, and always has worked, is you launch the app and are asked for the sudo password.  You enter the password and the gui form of synaptic opens.  It is the same process for gparted.  What has suddenly happened is that when I launch the gui, it attempts to open .... and then closes.  I _do not _want to be able to open these gui programs without being asked for the sudo password.  I just want them operate normally.

---

### Post by cmcanulty on 2021-04-07
That's exactly what my post  does

---

