---
title: "Nautilus Crashes"
date: 2013-12-04
forum: General Help
---

### Post by partloer on 2013-12-04
Either after installing one of the latest updates or dropbox nautilus (GNOME nautilus 3.8.2) crashes.  Once I open my home folder after about three seconds it closes out.  Also none of my files saved on my desktop show up when viewing the desktop.  I have uninstalled dropbox and reinstalled dropbox with no changes.

---

### Post by ibjsb4 on 2013-12-05
Have you tried opening it in terminal and looking for errors?

---

### Post by partloer on 2013-12-05
Very little.  I am not the best at reading error messages but if you have any suggested commands let me know and I will try them.

---

### Post by ibjsb4 on 2013-12-05
I do not think I made myself clear.  What I meant was to open nautilus by using the terminal command:

```
nautilus
```

This will allow you to look for errors in the terminal window.

---

### Post by partloer on 2013-12-05
```
Initializing nautilus-dropbox 1.6.0


(nautilus:10266): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed


(nautilus:10266): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Segmentation fault
```

---

### Post by ibjsb4 on 2013-12-05
I found a possible fix here:

[http://askubuntu.com/questions/20854/how-to-enable-user-sharing-per-instructions](http://askubuntu.com/questions/20854/how-to-enable-user-sharing-per-instructions)

> I sort this problem creating a group call admin:

sudo groupadd admin

Check that the admin group is part of the sudoers:

sudo cat /etc/sudoers

Now you add your user to the admin group :

sudo usermod -aG admin username

you can check if your user is part of the group :

sudo cat /etc/group | grep '^admin'

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=cannot+open+usershare+directory+%2Fvar%2Flib%2Fsamba%2Fusershares&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=cannot+open+usershare+directory+%2Fvar%2Flib%2Fsamba%2Fusershares&sa=Search&cof=FORID:9)

[https://www.google.com/search?client=ubuntu&channel=fs&q=cannot+open+usershare+directory+%2Fvar%2Flib%2Fsamba%2Fusershares&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=cannot+open+usershare+directory+%2Fvar%2Flib%2Fsamba%2Fusershares&ie=utf-8&oe=utf-8)

---

### Post by partloer on 2013-12-18
In a recent update this has been updated.  I don't know which update over the last few days but this problem has been fixed.

---

