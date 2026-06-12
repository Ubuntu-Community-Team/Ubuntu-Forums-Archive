---
title: "Recover data from broken Ubuntu system using a Live System"
date: 2013-08-20
forum: General Help
---

### Post by Sebastian_Plamauer on 2013-08-20
so, like 10 minutes ago i restarted my pc after the 3.2 kernel update and suddenly my system fails to boot. whatever. before i try to repair it or reinstall (yay) i need to get some data from the harddrive that wasn't backuped.

so, booting from the cd gives me a nice little live system - but it won't let me copy the files from the harddrive - permission denied.
what do i do now?

cp -avr doesn't work, still tells me 'operation not permitted'

thanks.

---

### Post by sudodus on 2013-08-20
If it is a problem with permissions, you can use superuser privileges.

```
sudo cp -avr source target
```

or more advanced

```
sudo rsync [options] source target
```
for example

```
sudo rsync -avn source/ target
```

n means 'dry run' to check what will be copied by the command. Remove the n

```
sudo rsync -av source/ target
```

to run the real copying process.

See ```
man cp
``` and ```
man rsync
``` for more details

---

