---
title: "Mythtv HELP!"
date: 2006-10-10
forum: General Help
---

### Post by drpepper on 2006-10-10
I've been following [THIS]("http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation") guide over at mythtv.org

Everything has been fine, up untill actually installing, Mythtv. When following the install guide from source in the mythtv documentation, I check for dependencies with

apt-get build-dep mythtv

and it says it can't find the libiec61883-dev package. I have googled it and searched the forums but can't find where to get it from.

Can anyone help, i really need this to work for a university project, and don't want to have to try another distro!
Edit/Delete Message

---

### Post by Naegling23 on 2006-10-10
try installing it through synaptic (or whatever the program you gnome users have)

---

### Post by drpepper on 2006-10-10
I'm doing it on a server install of ubuntu, so no gui! i don't want the gui because it uses alot of resources. Thanks for the idea tho. any one else with suggestions? 

Thanks

Nick

---

### Post by p4rogue on 2006-10-10
This should work for your server install to get that .deb file.

```
$ wget http://ubuntu.secs.oakland.edu/pool/main/libi/libiec61883/libiec61883-dev_1.0.0-0.2ubuntu1_i386.deb
$ dpkg -i libiec61883-dev_1.0.0-0.2ubuntu1_i386.deb
```

This should install that file in order for your MythTV to work. Good Luck Hope it helps.

---

