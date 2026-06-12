---
title: "gvpndialer"
date: 2005-09-18
forum: General Help
---

### Post by lee_connell on 2005-09-18
Trying to compile gvpndialer from source.  libpcre is installed w/ dev files however the configure doesn't find it.

how do i tell configure where to look?

---

### Post by lee_connell on 2005-09-22
anyone?

---

### Post by shadow07 on 2005-09-26
Well, I found that the download source has a problem.  The install.sh and other scripts are missing.  However, I was able to download the RPM package, use alien to convert it to a debian package.

It's installed, but I keep getting the following error:

> gvpndialer: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory

I checked to see if libpcre is installed, and it is.  Any ideas?

Oh, and I'm running v5.10 right now.

---

### Post by shadow07 on 2005-10-09
I was just able to fix my problem.  gvpndialer was looking for libpcre.so.0, which does not exist on Breezy.  So, I created a sim link to libpcre.so.3.11.0

```
 sudo ln -s /usr/lib/libpcre.so.3.11.0 /usr/lib/libpcre.so.0

```

I was able to finally start gvpndialer.  :cool:

---

### Post by logik-bomb on 2006-05-13
Its easy
You download the .rpm version of the gvpndialer.
you user alien [ sudo apt-get install alien ]
then  sudo alien -d  xxxxx.rpm
dpkg -i xxxxx.deb
done :)

---

### Post by hackmeister on 2008-06-09
Breathing live back into this thread. I've created an i386 package under Hardy for this:
[http://pdavila.homelinux.org:8080/blog/?p=291](http://pdavila.homelinux.org:8080/blog/?p=291)

---

### Post by Ordinary12 on 2008-06-25
Thanks for putting this out for people like me to use because I really hate using the command line.  I have a question for you.  I keep getting the following error in the command line:

(gvpndialer:9210): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

The gvpndialer gui says the following:

Could not attach to driver.  Is kernel module loaded?

Can you please tell me how to resolve this problem?  I'm running Ubuntu 8.04.

---

### Post by hackmeister on 2008-07-01
The first message is ok, ignore it:
(gvpndialer:15990): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

You still need to have the ciscovpn application installed and running. The second message says you don't have the cisco kernel module running. To get the kernel module running type the following from the commandline:
sudo /etc/init.d/vpnclient_init start

FYI, I didn't write the app. I just packaged it. In the future I'd like to setup the installer to automatically make an entry in the menu along with an icon. If I have time I'll try to get that done.

---

