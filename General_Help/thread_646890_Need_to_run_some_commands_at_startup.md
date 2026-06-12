---
title: "Need to run some commands at startup"
date: 2007-12-21
forum: General Help
---

### Post by gheywood on 2007-12-21
Hello, 

I need to run the following when the system starts:

rm -rf /var/run/vmware/httpd 
mkdir /var/run/vmware/httpd 
chown www-data:nogroup /var/run/vmware/httpd 
chmod 755 /var/run/vmware/httpd 
/etc/init.d/httpd.vmware restart 

Most of those need SUDO when I run them manually. How do I do this in a script, and at startup? 

Or can I run them under a different context that does not need "sudo"? 

Thanks

---

### Post by nick_h on 2007-12-21
Put them in your /etc/rc.local file.  Commands in this file run as root at startup.

---

### Post by gheywood on 2007-12-21
Thanks.. How do I save changes though? 

I am running "sudo vim rc.local" but I can't save changes. I have tried every combination of !, w, and q, without any luck. 

Even tried a chmod 775 command but that doesn't work...

---

### Post by nick_h on 2007-12-21
I just edited mine with:
```
sudo vi /etc/rc.local
```
and saved it with a **:wq**

---

### Post by dcstar on 2007-12-21
> **nick_h said:**
> I just edited mine with:
```
sudo vi /etc/rc.local
```
and saved it with a **:wq**

If you editing in a terminal then use **nano**, otherwise use **gedit**.

---

