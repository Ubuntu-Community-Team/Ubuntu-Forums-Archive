---
title: "running startup program as root"
date: 2006-10-22
forum: General Help
---

### Post by Azazel on 2006-10-22
im trying to get firestarter to run on startup.


i added this line to the end of my sudoers file

kory ALL= NOPASSWD: /usr/sbin/firestarter

but now firestarter doesnt work at all!


also without the added line in sudoers, i added the following command to my startup list, but that didnt work either

echo "password" | sudo -S firestarter


any ideas???

---

### Post by Jussi Kukkonen on 2006-10-23
That is starting to look like a real hack :) 

I have never installed firestarter, but I'm willing to bet that if it's a server program (daemon) it adds a file in /etc/init.d/ and the needed symlinks in e.g. /etc/rc2.d/ -- those take care of starting programs during startup. If it doesn't do that, the it doesn't need to be running all the time...

I'm not 100% sure of what you want to achieve, but I do have the feeling that what you are trying to do is probably not needed. I definitely suggest you do not do things like *echo "password" | sudo -S firestarter* in any script. That is a bigger security hole than running without a firewall could ever be...

---

### Post by kerry_s on 2006-10-23
Try changing this->
kory ALL= NOPASSWD: /usr/sbin/firestarter
 to be->
user ALL=(root) NOPASSWD: /usr/sbin/firestarter

---

### Post by 5-HT on 2006-10-23
> **Azazel said:**
> im trying to get firestarter to run on startup...any ideas???
It requires a bit of a hack on Dapper: [http://ubuntuforums.org/showthread.php?t=274611](http://ubuntuforums.org/showthread.php?t=274611)

---

### Post by Jussi Kukkonen on 2006-10-23
Ok, now I understand. You want to run a firewall GUI all the time. Is there a reason to do that?

---

### Post by 5-HT on 2006-10-24
> **Jussi Kukkonen said:**
> Ok, now I understand. You want to run a firewall GUI all the time. Is there a reason to do that?

Apart from wanting to monitor events, there is a possible issue with firewall persistence in Dapper unless one either 1) starts firestarter manually from the init.d script, 2) Runs the GUI.

[https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647](https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647)

---

