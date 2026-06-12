---
title: "since last week unable to get any updates !"
date: 2013-05-14
forum: General Help
---

### Post by creature1963 on 2013-05-14
Up till last week - updates were hapening as they should, then it stopped working ang all i get is the following error message :sad:

Can anyone advise please ?


"Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type ‘ain’ is not known on line 3 in source list /etc/apt/sources.list.d/aheck-ppa-precise.list' "

---

### Post by plucky on 2013-05-14
> **creature1963 said:**
> Up till last week - updates were hapening as they should, then it stopped working ang all i get is the following error message :sad:

Can anyone advise please ?


"Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

**'E:Type ‘ain’ is not known on line 3 in source list /etc/apt/sources.list.d/aheck-ppa-precise.list'** "

Post output for ```
cat /etc/apt/sources.list.d/aheck-ppa-precise.list
```

---

### Post by creature1963 on 2013-05-14
think this is what you want ? but not to clued up on ubuntu behind the scenes stuff

mr-creature@Bigdaddy:~$ cat /etc/apt/sources.list.d/aheck-ppa-precise.list
# deb [http://ppa.launchpad.net/aheck/ppa/ubuntu](http://ppa.launchpad.net/aheck/ppa/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/aheck/ppa/ubuntu](http://ppa.launchpad.net/aheck/ppa/ubuntu) precise main
ain
mr-creature@Bigdaddy:~$

---

### Post by lisati on 2013-05-14
You need to edit file /etc/apt/sources.list.d/aheck-ppa-precise.list, and remove line 3, which contains only the letters "ain".

---

### Post by creature1963 on 2013-05-14
ok silly question - how do i edit the file ?

---

### Post by plucky on 2013-05-14
> **creature1963 said:**
> think this is what you want ? but not to clued up on ubuntu behind the scenes stuff

mr-creature@Bigdaddy:~$ cat /etc/apt/sources.list.d/aheck-ppa-precise.list
# deb [http://ppa.launchpad.net/aheck/ppa/ubuntu](http://ppa.launchpad.net/aheck/ppa/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/aheck/ppa/ubuntu](http://ppa.launchpad.net/aheck/ppa/ubuntu) precise main
ain
mr-creature@Bigdaddy:~$

As the url lines are both commented out,you are not using the PPA,so it might be a good idea to delete it.

```
sudo rm /etc/apt/sources.list.d/aheck-ppa-precise.*
``` and then run ```
sudo apt-get update
``` and see if you still get the problem.

Good Luck

---

### Post by lisati on 2013-05-14
Here's how I would do it,  there are other ways:
[LIST=1]
[*]Open up a terminal
[*]Type in ```
sudo nano /etc/apt/sources.list.d/aheck-ppa-precise.list
``` You might be asked for your password: don't panic if nothing shows when you are typing, this is normal.
[*]Remove line 3
[*]Press Ctrl+x
[*]Done!
[*]
[/LIST]

---

### Post by creature1963 on 2013-05-14
> **lisati said:**
> Here's how I would do it,  there are other ways:
[LIST=1]
[*]Open up a terminal 
[*]Type in ```
sudo nano /etc/apt/sources.list.d/aheck-ppa-precise.list
``` You might be asked for your password: don't panic if nothing shows when you are typing, this is normal. 
[*]Remove line 3 
[*]Press Ctrl+x 
[*]Done! 
[/LIST]


the line came back - so i unticked the ppa in the update manager and is now downloading 12 days worth of updates - many thanks Lisati

---

### Post by creature1963 on 2013-05-14
Solved :)

---

