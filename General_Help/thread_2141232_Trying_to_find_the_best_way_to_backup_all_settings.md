---
title: "Trying to find the best way to backup all settings and packages"
date: 2013-05-02
forum: General Help
---

### Post by icu12345 on 2013-05-02
So I'm new with ubuntu and so far I just love it :) I am now thinking how to perform full system backup, so that all my system settings, all my programs and packages and everything I've tweaked so far (desktop environment, window manager, etc.) is recoverable. 

I could use deja dup or any other backup origram to backup the /home folder. However, upon recovery all installed packages woule be lost..
I thought I could do this:
```
dpkg --get-selections > myfile #Write a list of all the installed packages
dpkg --set-selections < myfile #Read a list of all the packages to install
```

but this is dangerous because package names sometimes change across releases so it's no good when upgrading to new release...

So I thought maybe this would be better:
```


1. Do the following commands

dpkg --get-selections > ~/Package.list
sudo cp /etc/apt/sources.list ~/sources.list
sudo apt-key exportall > ~/Repo.keys
rsync --progress /home/`whoami` /backup folder

2. backup /home folder now
3. loose all data, change damaged HDD, format HDD, whatever..
4. reinstall ubuntu
5. recover /home folder
6. do the following

rsync --progress /backup folder /home/`whoami`
sudo apt-key add ~/Repo.keys
sudo cp ~/sources.list /etc/apt/sources.list 
sudo apt-get update
sudo apt-get install dselect
sudo dpkg --set-selections < ~/Package.list
sudo dselect

```

Do you think this would work? Or maybe there are some backup programs which backup automatically all settings and packages... Looking forward to your help...

---

### Post by Locus Kiesselbachi on 2013-05-02
I remember once I read article about writing your OS to DVD as it is installed with all packages on your PC. So when something hits the fan you can always recover it all from this DVD.

Uncle Google didnt understand me this time...sry

---

### Post by ibjsb4 on 2013-05-02
> but this is dangerous because package names sometimes change across releases so it's no good when upgrading to new release

Not so much dangerous, you may lose a package or two during a version upgrade.  I just log it up to collateral damage.  Backing up you home directory takes care of the bulk, but there are configuration files kept elsewhere.  Do a search on **.conf** and see all the files that pop up.

Nothing wrong with "dpkg --get-selections" to create a package list, works just fine.  I prefer [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9"), use it to create a "Markings List" which does the same thing.  Just find synaptic a better and more versatile package manager.

---

### Post by Mark Phelps on 2013-05-02
> **icu12345 said:**
> So I'm new with ubuntu and so far I just love it :) I am now thinking how to perform full system backup, so that all my system settings, all my programs and packages and everything I've tweaked so far (desktop environment, window manager, etc.) is recoverable.

Everyone has their own preferences, but for full system backups, it's hard to beat Clonezilla.  It will image off your installation in a form that is easily restored.

---

### Post by icu12345 on 2013-05-02
> **Mark Phelps said:**
> Everyone has their own preferences, but for full system backups, it's hard to beat Clonezilla. It will image off your installation in a form that is easily restored.

True, disk cloning is probably the safest but there is one major disadvantage: The destination partition must be equal or larger than the source one. This is why I am looking for an alternative to cloning the entire hard drive (or the partitions which ubuntu uses)... 

This is why I'd be happy to hear how you do your backup.. and eventually figure out how to do it myself :)

---

### Post by ibjsb4 on 2013-05-02
> This is why I'd be happy to hear how you do your backup.. and eventually figure out how to do it myself 

I clonezilla a copy just incase all else fails and have created a [data partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9") instead of a home partition where I stick everything important to me and then rsync my data with either [grsync]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=grsync&sa=Search&cof=FORID:9") or [luckybackup]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=luckybackup&sa=Search&cof=FORID:9").

And just incase a meteor hits the house I have on line backup (dropbox).

---

