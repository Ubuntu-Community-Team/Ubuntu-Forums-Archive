---
title: "Running networking configurator stops graphic apps launching"
date: 2004-10-26
forum: General Help
---

### Post by ricardo on 2004-10-26
In the live CD, whenever I use the networking configurator I lose the ability to
launch applications that use X, either through Gnome or via a terminal.  With
Gnome I get a spinning wheel for a while and then nothing happens.  When I try
to launch the application from a console I get the message "Unable to connect to
X server".

There is an open bug report about this, in [https://bugzilla.ubuntu.com/show_bug.cgi?id=2631](https://bugzilla.ubuntu.com/show_bug.cgi?id=2631)

---

### Post by oohlaf on 2004-10-26
That happens when you change the hostname. X doesn't allow you to connect to the server anymore because of the X security model. The following commands aren't restricted to the live CD, use them to change the hostname without restarting a running X server.

You must add the current magic cookie with the new hostname to your Xauthorization list:

```

$ xauth -list
oldhostname/unix:0 MIT-MAGIC-COOKIE-1 cookie

$ xauth add newhostname/unix:0 MIT-MAGIC-COOKIE-1 cookie

```
Replace newhostname with the new hostname and copy-paste the cookie from the first output in the second command. The cookie is a MD5 encoded string.

Make sure /etc/hostname has the new hostname
and /etc/hosts has an alias for the new name to 127.0.0.1

When I tried the live CD I also ran across this problem,
I then chose to not change the hostname, just the dhclient config like this:
Fisrt I edited the /etc/network/interfaces file by hand with 'iface eth0 inet dhcp'
and enabled 'send host-name "blabla";' in /etc/dhcp3/dhclient.conf.
After 'ifup eth0' the cable modem was up and running.

---

