---
title: "Samba installed but no windows networking options"
date: 2005-09-25
forum: General Help
---

### Post by Steve Smith on 2005-09-25
I've installed Samba, but when I go to system -> admin -> networking -> general I haven't got the windows settings that are described on the wiki ([https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)).

Could someone help me out please!

---

### Post by antariksh on 2005-09-25
Hi Steve,

I too don't get the options on the wiki you mentioned, however I managed to get samba Windows sharing to work.

Not sure whether the following omits steps or adds unnecessary ones, but here are the network and samba configuration that worked for me.

In Gnome Menu, go to System->Network settings.

In the General tab, my domain name is **mshome.net** (as far as I am aware, this is how Windows XP names it by default). The Hostname field contains my usual linux hostname.

In DNS tab, my DNS servers field contains **192.168.0.1** and search domains contains **mshome.net**.

Next in my **/etc/samba/smb.conf** file, I edited the following fields.

workgroup = **<workgroupname>** which must be the same name that your Windows network uses.

wins support = **yes**

Save and **reboot** your system.

Let us know how it goes.

---

