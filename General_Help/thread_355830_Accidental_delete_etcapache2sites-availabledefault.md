---
title: "Accidental delete /etc/apache2/sites-available/default"
date: 2007-02-07
forum: General Help
---

### Post by tiger.woods on 2007-02-07
I accidentally deleted my apache2 /default setting file for setting up a new virtual host can someone tell me where to get a copy of this file??

/etc/apache2/sites-available/default

Thanks,

---

### Post by llamakc on 2007-02-07
There's a copy of it at /usr/share/apache2/config/default I believe. 

Another cool way is to do:

```

cd /tmp && dpkg --fsys-tarfile /var/cache/apt/archive/apache2-common_2.0.55-4ubuntu4_i386.deb | tar -xf - default*

```That is if you still had the .deb in your archive.

---

### Post by shickey on 2007-02-07
otherwise, if you want to reconfigure everything apache....

dpkg -P apache2-common apache2
apt-get install apache2-common apache2

Keep in mind that the above will delete all of your apache configuration files.:guitar:

---

### Post by tiger.woods on 2007-02-07
Much appreciated.:)

---

### Post by tiger.woods on 2007-02-07
Things aren't going as planned.. I can't remove and can't re-install???

[I]dpkg: dependency problems prevent removal of apache2-common:
 apache2-mpm-worker depends on apache2-common (= 2.0.55-4ubuntu4).
dpkg: error processing apache2-common (--purge):
 dependency problems - not removing
(Reading database ... 100267 files and directories currently installed.)
Removing apache2 ...
Errors were encountered while processing:
 apache2-common[/I]

So, I tried rm the /apache2 dir and things went from bad to worse, I could use a little expert help...

Thanks,

---

### Post by llamakc on 2007-02-07
Why would you have done that in the first place? If all you did was delete the /etc/apache2/sites-available/default file, one exists right now on your file system as I pointed out above.

Please use the tools provided by Ubuntu to add/remove software. Open Synaptic and choose to reinstall the packages. That should do it for you.

---

### Post by tiger.woods on 2007-02-08
I will in the future use the utils in Ubuntu.... thanks.

Getting the following error when trying to restart apache

 * Forcing reload of apache 2.0 web server...                                   awk: cannot open /etc/apache2/apache2.conf (No such file or directory)
grep: /etc/apache2/apache2.conf: No such file or directory


It seems the file folders are created but the some of the contents within them are missing?

---

### Post by llamakc on 2007-02-08
`sudo apt-get install --reinstall apache2 apache2common`

---

### Post by tiger.woods on 2007-02-08
Thanks for suggestion I'll give it a shot when I get to the house later and post back.

I ran synaptic and selected those packages for reinstall as you had directed is that any different than running it from the command line?

TW,

---

### Post by tiger.woods on 2007-02-08
mythtv@myth:~$ sudo apt-get install --reinstall apache2 apache2-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 1 reinstalled, 0 to remove and 29 not upgraded.
Need to get 0B/843kB of archives.
After unpacking 81.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package apache2.
(Reading database ... 100442 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-common.
Preparing to replace apache2-common 2.0.55-4ubuntu4 (using .../apache2-common_2.0.55-4ubuntu4_i386.deb) ...
Unpacking replacement apache2-common ...
Setting up apache2 (2.0.55-4ubuntu4) ...
Setting up apache2-common (2.0.55-4ubuntu4) ...

Install seems to have been successful except that /sites-available doesn't have a 'default' site and /mods-available is blank? Still getting error when trying to restart apache

* Forcing reload of apache 2.0 web server... awk: cannot open /etc/apache2/apache2.conf (No such file or directory)
grep: /etc/apache2/apache2.conf: No such file or directory

---

### Post by llamakc on 2007-02-08
I guessed at what package would contain those files. If you KNOW which package you deleted, you can always check at [http://packages.ubuntu.com](http://packages.ubuntu.com)

That shows that the file apache2.conf is in the package apache2-common.

You may have to completely remove the packages and make sure that there is no contents inside /etc/apache2 (so back up anything you want elsewhere), and reinstall the packages.

---

### Post by tiger.woods on 2007-02-08
I removed the /etc/apache2 folder and that was it so all the default installed contents are what is missing.

#apt-get install apache2 apache2-common seems to recreate the folders but not the apache2.conf file.

> You may have to completely remove the packages and make sure that there is no contents inside /etc/apache2 (so back up anything you want elsewhere), and reinstall the packages.

So what your saying is delete everything from within the folder **/apache2** or should I just remove the folder **/apache2**? 

After which I should run, 

#apt-get remove apache2 apache2-common
#apt-get install --reinstall apache2 apache2-common

Thanks,

---

### Post by llamakc on 2007-02-08
I would do

`sudo aptitude purge apache2 apache2-common`


Next, 

cd /etc/apache2 && ls -a

to make sure there is nothing inside of that directory. Next, 

cd /etc && rmdir apache2

then reinstall.

sudo apt-get install apache2 apache2-common

---

### Post by tiger.woods on 2007-02-08
That seems to have gotten it.

Thanks for the assistance. :) 

TW,

---

