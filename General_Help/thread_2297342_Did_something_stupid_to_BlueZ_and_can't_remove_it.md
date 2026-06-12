---
title: "Did something stupid to BlueZ and can't remove it"
date: 2015-10-02
forum: General Help
---

### Post by Dukenukemx on 2015-10-02
Was trying to setup a PS3 controller with Ubuntu 14.04 and couldn't get it to work with Qtsixa so I thought I'd try updating Bluez with [this PPA](https://launchpad.net/~vidplace7/+archive/ubuntu/bluez5) and it stopped installing at some point.  Just stayed there doing nothing in terminal.  Reset the machine and tried to remove bluez and now it's stuck doing this.  
```

Removing bluez (5.35.0+upstream-201510021833~rev18288~pkg9~ubuntu14.04.1) ...

```

I've tried remove purge and Synaptic Manager and they all get stuck trying to remove this.  How can I fix this?

---

### Post by Dukenukemx on 2015-10-03
Nobody?  Nothing?

---

### Post by Dukenukemx on 2015-10-03
I fixed this by doing the following.

```

cd /var/lib/dpkg/info
sudo rm *bluez*

```

Then I installed PPA purge and purged the PPA and then I could fully remove Bluez.  Then I reinstalled Bluez.  Bluetooth works again.

---

