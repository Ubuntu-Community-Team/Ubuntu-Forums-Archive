---
title: "[SOLVED] error in synaptic package installation"
date: 2008-07-09
forum: General Help
---

### Post by arturieto on 2008-07-09
in my laptop computer, whenever i downloaded an application for update or something else, an error occured that cut off proper installation.  I got this message "E: havp: subprocess post-installation script returned error exit status 1".  i could make any update anymore.  please help.

---

### Post by plucky on 2008-07-09
> in my laptop computer, whenever i downloaded an application for update or something else, an error occured that cut off proper installation. I got this message "E: havp: subprocess post-installation script returned error exit status 1". i could make any update anymore. please help.


Have you tried ```
sudo dpkg --reconfigure -a
```

If that doesn't work,can you post the output of the whole error.


Good Luck

---

### Post by arturieto on 2008-07-10
I tried this, but. . . . 

art@art-mpdc:/$ sudo dpkg --reconfigure -a
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
art@art-mpdc:/$ 


NOTHING HAPPENS, PLEASE HELP. WOULD IT BE GOOD IF I REINSTALL THE WHOLE UBUNTU OS.

---

### Post by L337_K3y5 on 2008-07-10
> **arturieto said:**
> NOTHING HAPPENS, PLEASE HELP. WOULD IT BE GOOD IF I REINSTALL THE WHOLE UBUNTU OS.

Whoah!  Take it easy, I had a similar problem, but with help I was able to fix it.  Turns out, mine was due to a faulty kernel syslink left behind...We can help...Have you installed a new kernel maybe recently?:-k  Sorry for my incompetence...maybe something I've ate...Its late, lol.

---

### Post by plucky on 2008-07-10
> art@art-mpdc:/$ sudo dpkg --reconfigure -a
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL)[*].

Options marked[*] produce a lot of output - pipe it through `less' or `more' !
art@art-mpdc:/$ 


SORRY that command should have been ```
sudo dpkg --configure -a
```

It was late at night,which shouldn't be an excuse.

---

### Post by Kevbert on 2008-07-10
It may also worth entering the following in terminal:
```
sudo apt-get install -f
```
to repair any damaged packages.

---

### Post by arturieto on 2008-07-10
I got this when i tried . . . 

art@art-mpdc:/$ sudo dpkg --configure -a
[sudo] password for art: 
art@art-mpdc:/$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgksu1.2-1 avast4workstation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up havp (0.86-1build1) ...
chown: cannot access `/var/run/havp': No such file or directory
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)

they don't work. please help. any other method to install this "havp"?

---

### Post by Malac on 2008-07-10
```
sudo dpkg-reconfigure -a
``` is the command to try. (-reconfigure is not a switch so no space)
Takes a while.

---

### Post by arturieto on 2008-07-10
still the process did not succeed. the problem is still there when I tried to install package.

---

### Post by plucky on 2008-07-10
> chown: cannot access `/var/run/havp': No such file or directory


This is just speculation but try to create an empty file with ```
gksudo gedit /var/run/havp
``` Save and exit.
 
And then ```
sudo apt-get install -f
``` and see what happens.


Good Luck

---

### Post by Malac on 2008-07-10
This is a long shot....
there was a bug with a package that left /tmp and /var as read-only a bit back. This would also cause these symptoms. I would check the permissions on these folders just in case.
 
I would expect lots more problems if this is the case but it is worth checking.
 
Hope this helps.

---

### Post by arturieto on 2008-07-16
i got this.

art@art-mpdc:/$ gksudo gedit /var/run/havp
art@art-mpdc:/$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
art@art-mpdc:/$ 


nothing happens.

---

### Post by plucky on 2008-07-17
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This usually means you have another package manager open,i.e Synaptic,Add/Remove etc.Make sure they are all closed and try the command again.

Also check the "processes" page in the System Monitor for any dpkg processes being open.

Good Luck

---

### Post by lisati on 2008-07-17
> **Malac said:**
> ```
sudo dpkg-reconfigure -a
``` is the command to try. (-reconfigure is not a switch so no space)
Takes a while.
sure it's not ```
sudo dpkg --configure -a
```

---

### Post by arturieto on 2008-07-17
I got this again:

art@art-mpdc:/$ gksudo gedit /var/run/havp
art@art-mpdc:/$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up havp (0.86-1build1) ...
There is already /var/lib/havp/havp.loop, maybe from an earlier or custom installation, not building loopback-device
Starting havp: start-stop-daemon: open pidfile /var/run/havp/havp.pid: Not a directory (Not a directory)
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do i determine in the processes if it is dpkg?

---

### Post by plucky on 2008-07-17
Can you open "Synaptic Package Manager"?

If so it might be possible to fix the Havp package using the Broken Package filter.
Do you know why the "havp" package was being installed?
Was it part of another package?

Good Luck

---

### Post by arturieto on 2008-07-17
i tried broken filter but to no avail.  I doubt it, but havp is used in the installation of clamav.

I tried to remove havp in synaptic, but again error occured. even itself could be removed.

I reported this as a bug. it has been recorded, but i dont know what's next. i recorded it in forum.

would it be possible to make things simpler, do you recommend i will do formatting and re-install ubuntu? i hope i will not lost hope of the community team in helping me.  am new in ubuntu and trying hard to learn the nuts and bolts.

a lot of updates is on the line, but once it downloaded, the error on havp is registered. 

please keep always in touch with me.  i dont know where to look for help.

---

### Post by plucky on 2008-07-17
I don't know why that package is resistant to being fixed but you could try uninstalling and then reinstalling it in Synaptic.

Try ```
sudo apt-get remove havp
``` and see what happens,and then reinstall with ```
sudo apt-get install havp
```

Is ClamAv working for you?


I am getting to the point of running out of ideas on how to fix this.Maybe deinstalling ClamAv and reinstalling might help.

Good Luck

---

### Post by arturieto on 2008-08-03
to all my buddies

i tried everything but nothing happens.  there still the annoying pop up about havp.  anyway i still update my system through synaptic manager and inspite there is that annoying message i can detect that most of the updates and upgrades are done.

thanks for everything.

---

### Post by dexter.deepak on 2008-08-03
have you tried removing havp :
```
sudo apt-get remove --purge havp
```
then try installing it again..through command-line, and post the errors here.

---

### Post by dexter.deepak on 2008-08-03
> **arturieto said:**
> i got this.

art@art-mpdc:/$ gksudo gedit /var/run/havp
art@art-mpdc:/$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
art@art-mpdc:/$ 


nothing happens.

whenever you get this error, first of all see if there is another package-manager working..if so, then close it.
if you still get this error , try :
```
sudo rm -f /var/lib/dpkg/lock
```

---

### Post by arturieto on 2008-09-05
art@art-mpdc:/$ sudo apt-get remove --purge havp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto python-twisted-names libgsf-gnome-1-114 python-psyco
  libgfortran2 python-twisted-runner python-visual python-sqlobject python-dns
  python2.4-minimal python2.4 python-formencode libgoffice-0-6-common
  python-twisted-mail python-numpy python-twisted-lore python-twisted-conch
  python-twisted-news python-twisted-words python-twisted libgoffice-0-6
  libblas3gf python-wxversion liblapack3gf gtkglarea5 python-wxgtk2.6
  libestools1.2 libboost-python1.34.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  havp*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 979kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 195746 files and directories currently installed.)
Removing havp ...
Unmounting /var/spool/havp ...umount: /var/spool/havp: device is busy
umount: /var/spool/havp: device is busy
invoke-rc.d: initscript havp, action "stop" failed.
dpkg: error processing havp (--purge):
 subprocess pre-removal script returned error exit status 1
Starting havp: Starting HAVP Version: 0.86
Could not create server (already running?)
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)

what is this?

---

### Post by netanel_h on 2008-11-06
Sorry for the late bump, but I had the same problem, found this thread in search engine, and also found the way how to solve it.
I used htop (sudo apt-get install htop) to find the PID numbers of all the Havp processes (there are more than one!), and then I killed all the processes by using the kill command:

sudo kill 5635 5636 5637 5640 5641 5642 5643 5644 5645 5646 5647 5648 5649 5650 5651 5652 5653
(the numbers may be different in other systems, check it in htop)

Then I updated, and all worked fine, the update also started the Havp service itself during the update process.

---

