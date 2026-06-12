---
title: "root"
date: 2006-11-06
forum: General Help
---

### Post by lamacama on 2006-11-06
why i cant log as _root_,please help.

---

### Post by kerry_s on 2006-11-06
root is diabled. ubuntu uses sudo.
example:
gksudo gedit /path/to/file
gksudo nautilus /

sudo (appname)

---

### Post by hikaricore on 2006-11-06
You can't login as root from a terminal or you can't login as root from the GDM login window?  You have to set the ability to login as root through GDM.  Login to a normal user account and goto the System Menu (assuming you're using gnome) Then chose Adminstration and finally Login Window.

A screen will come up prompting for your password (which should be the same as root by default) type in your password and the Login Window Preferences will popup.

Click on the Security tab and put a check in the box that says "Allow local system administrator login" in the middle of this box.  Then click close and logout of gnome.  You should now be able to login to GDM as root.  :)

If you're need root access in a terminal you'll need to use the command:

```
**sudo** *whatevercommandyouneedasroot*
```

or to make yourself root as long as you need:

```
**sudo -s**
```

good luck,

--aaron

---

### Post by aysiu on 2006-11-06
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by lamacama on 2006-11-06
thank you very much it worked.

---

