---
title: "How to turn services on/off from the command line"
date: 2008-01-15
forum: General Help
---

### Post by garymansell on 2008-01-15
Hi,

I would like to know how to turn services on/off from the command line.

I come from the Redhat world and so I am used to the chkconfig command - you would do something like chkconfig ypbind on to turn on ypbind for the next reboot.

I would like to know how to do this in gutsy without the GUI tool.

Thanks in advance

Gary

---

### Post by lian1238 on 2008-01-15
You can start/stop services like this:
```
sudo /etc/init.d/<service_name> start/stop
```
:)

---

### Post by oldos2er on 2008-01-15
I like the tool sysv-rc-conf.

---

### Post by ~LoKe on 2008-01-15
> **oldos2er said:**
> I like the tool sysv-rc-conf.

That's what I use.

```
sudo apt-get install sysv-rc-conf
```
```
sudo sysv-rc-conf
```

---

### Post by lizzard on 2008-01-15
To start/stop services permanently you can use "update-rc.d". It changes the links for the init scripts. 
To start a script in the default run levels:
```
sudo update-rc.d *appname* defaults
```

To remove a script from all runlevels:
```
sudo update-rc.d -f *appname* remove 
```

---

