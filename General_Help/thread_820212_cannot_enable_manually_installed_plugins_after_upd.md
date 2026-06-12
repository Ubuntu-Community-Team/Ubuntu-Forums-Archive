---
title: "cannot enable manually installed plugins after update"
date: 2008-06-06
forum: General Help
---

### Post by ramkumail on 2008-06-06
I installed 3d windows plugin and snow plugin long ago in gutsy.I upgraded to hardy and I cannot enable those two plugins. If i check them in ccsm it automatically gets unchecked. uninstalling and reinstalling compiz did not help.
I guess my plugins is in ~/.compiz because snow picture path in ccsm point to it and in ~/.compiz/plugins i see two files lib3d.so and libsnow and in ~/.compiz/metadata 3d.xml and snow.xml.
I see 3d.xml as well in /usr/share/compiz but not snow.xml. What should i do to correct this problem. I can as well live without these plugins if necessary. please  don't hesitate to ask for more info if necessary. Thanks in advance.

---

### Post by Gourgi on 2008-06-06
try reinstalling the plugins
[http://wiki.compiz-fusion.org/Install/PluginsFromGit](http://wiki.compiz-fusion.org/Install/PluginsFromGit)
```

sudo apt-get install git-core
git clone git://anongit.compiz-fusion.org/fusion/plugins/3d
cd 3d
make
make install
git clone git://anongit.compiz-fusion.org/fusion/plugins/snow
cd snow 
make 
make install

```

---

### Post by ramkumail on 2008-06-07
hi, thanks for the reply.  I got this error. what should i do.
> Initialized empty Git repository in /home/goal/snow/.git/
fatal: Unable to look up anongit.compiz-fusion.org (port 9418 ) (Name or service not known)
fetch-pack from 'git://anongit.compiz-fusion.org/fusion/plugins/snow' failed.

If i create a directory named snow and try it gives
> destination directory 'snow' already exists.

---

### Post by Gourgi on 2008-06-07
says that git servrice on server is down 
try again later
and remove the folder , it is created automatically

---

### Post by ramkumail on 2008-06-08
Thanks. May be the proxy I am behind is restricting. I went to [http://gitweb.compiz-fusion.org/?p=fusion/plugins/snow;a=summary](http://gitweb.compiz-fusion.org/?p=fusion/plugins/snow;a=summary) and downloaded the master snapshot and installed. It works fine now.

---

