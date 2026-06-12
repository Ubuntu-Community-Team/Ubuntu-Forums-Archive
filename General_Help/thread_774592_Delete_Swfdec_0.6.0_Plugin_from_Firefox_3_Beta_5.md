---
title: "Delete Swfdec 0.6.0 Plugin from Firefox 3 Beta 5"
date: 2008-04-29
forum: General Help
---

### Post by Perastikos on 2008-04-29
Hello,

I installed Ubuntu 8.04 LTS yesterday. Next, I opened Mozilla Firefox 3 Beta 5 trying to watch videos @ youtube. Firefox asked me to choose between three flash players-plugins to install. By mistake, I chose Swfdec 0.6.0 Plugin. At the moment, I can't watch any video @ youtube. 
How can I reinstall/delete Swfdec 0.6.0 Plugin and install Adobe Flash Player?

Please help me!

---

### Post by sphinx64 on 2008-04-30
Run System>Administration>Synaptic Package Manager. 
Then search "swfdec", select "libswfdec-0.6-90" and "swfdec-mozilla" and remove them. 
Start up Firefox with a flash website and the flash plugin installation should pop up again.

---

### Post by acidrainy on 2008-04-30
> **sphinx64 said:**
> Run System>Administration>Synaptic Package Manager. 
Then search "swfdec", select "libswfdec-0.6-90" and "swfdec-mozilla" and remove them. 
Start up Firefox with a flash website and the flash plugin installation should pop up again.

Thankyou. This helped me too.


Through trying to install the non-free flash plugin, I had both the aforementioned and non-free installed. This meant that my browser defaulted to the Swfdec 0.6.0 plugin and I couldn't use a multitude of websites.  As I already had the correct plugin installed, as soon as I uninstalled the swfdec, the websites worked. :D

---

### Post by bvanaerde on 2008-05-06
Thanks for the help... I was in the same situation.

---

### Post by tim89 on 2008-08-05
Thanks for the help, I was also stuck with this.

---

### Post by Cazzj on 2008-08-18
Another Thanks!  That worked for me too.  That swfdec was very annoying.

---

### Post by feel the beat on 2008-08-25
[B][SIZE="6"]thanks a lot it was unbelievable browsing with Swfdec plugin  

With My Best Regards

 [/SIZE][/B]

---

### Post by ahuman on 2008-09-20
Thanks for the post and the answer!:guitar:

---

### Post by elvijs on 2009-04-24
You saved my sanity!

---

### Post by J.K on 2009-05-19
Thank you for the information, sphinx64. It was pretty disappointing with swfdec, particularly as I wasn't able to use Google Analytics reporting whatsoever.

---

### Post by Ray1618 on 2009-09-25
Thanx Sphinx64, this really helped me out a lot!

---

### Post by mckemie on 2009-10-09
As a regular user, this worked fine for me.  Thanks!

However, I configured gdm to allow root logins and flash playing is still broken for a root gdm login.

---

### Post by hysbyswr on 2009-11-16
Hello,

I am currently using Firefox 3.5.5 on Ubuntu Jaunty Jackalope.  I would like to uninstall swfdec (swfdec-gnome  2.26.0-1 and swfdec-mozilla  0.8.2-1ubuntu1) so that it will use the real adobe flash player.

Unfortunately, if I try to uninstall the swfdec stuff, it tries to uninstall tons of other stuff (including gnome).

In older versions, I was able to successfully uninstall swfdec, but for whatever reason in this version it won't uninstall without uninstalling all of the other stuff.

Does anyone have any ideas on how I can get around this?  Thanks!

---

### Post by hidinginthemountains on 2009-11-16
edit: nevermind...nothing to see hear folks...I don't have this problem after all

---

