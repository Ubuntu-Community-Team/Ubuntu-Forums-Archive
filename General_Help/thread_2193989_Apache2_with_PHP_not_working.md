---
title: "Apache2 with PHP not working"
date: 2013-12-15
forum: General Help
---

### Post by waltm on 2013-12-15
Hi folks, I'm trying to set up an apache2 server with PHP for use by mythweb and I'm running into some problems.  If I install Apache2 on it's own I can connec to to [http://localhost](http://localhost) and get the "it works" default page. Once I install libapache2-mod-php5 things start to fail.  trying to access the same page at [http://localhost](http://localhost) or [http://localhost/test.php](http://localhost/test.php) (single line of <?php phpinfo(); ?> ) only gets a "waiting for localhost" status in the browser.  The same happens if trying to connect with the actual ip address of the machine.  

The apache error.log has this:

```

(process:17494): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:17494): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:17494): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

```

I can not stop apache when this is happening and must killall to exit.  stopping and re-starting works normally without libapache2-mod-php5 installed.


Would anyone have any suggestions on what I should be looking for or what other into I should provide for further guidance?

---

### Post by mkmanifesto on 2013-12-15
I would install it with taskel. After you install taskel just select LAMP. It should install everything automatically for you.

```
sudo apt-get install tasksel
```

once that is installed just type:
```
taskel
```

and hit enter. Select LAMP and you should be good to go.

---

### Post by waltm on 2013-12-15
Thanks for the tip.  Before I give that a shot would it conflict with an already functioning MySQL database or just ignore what is already there?

---

### Post by mkmanifesto on 2013-12-15
Ah good question I don't know. I would certainly back up any databases you have just to be safe.

---

### Post by waltm on 2013-12-19
So, I tried to remove all apache2 and related php packages with 

```
sudo apt-get purge libapache2-mod-php5
```
and
```
sudo apt-get remove --purge $(dpkg -l apache* | grep ii | awk '{print $2}')
```

backed up mysql and mythtv and ran tasksel to install lamp server.

Same issue, error message for apache is 
```
[Thu Dec 19 11:54:36 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Thu Dec 19 11:54:38 2013] [notice] caught SIGTERM, shutting down

(process:4954): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:4954): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:4954): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
```

if I remove libapache2-mod-php5 I get back basic web server functionality.



Any other ideas on what I could try or what might give a clue to the problem?

---

### Post by mkmanifesto on 2013-12-20
I'm assuming something has to be messed up in the apache config file or php.ini. I'm going to do some research.

---

