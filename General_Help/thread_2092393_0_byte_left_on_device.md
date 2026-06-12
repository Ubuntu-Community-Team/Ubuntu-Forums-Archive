---
title: "0 byte left on device"
date: 2012-12-07
forum: General Help
---

### Post by MacOsX74 on 2012-12-07
Hi!

I have a big problem that i cant get fixed by myself.
Something is eating my up my diskspace.

I have deleted some apps and empty the trashcan but every time i start up i get a messege saying 0 byte left on device. I dont get a gui when i start up but i can login via remote desktop and that swhere i see the messege.

I run ncdu and i only use 565,7mb.

I´m running 12.04 on an 60Gb ssd disk.


I have no idea of what to do so any help would be great.

I have found the folder thats eating my space. Its the /var/log/upstart
Its 32gb.

I have now found the file. Its the lightdm.log file. 31.6Gb
How can i fix this?

The error messege is this: (gnome-settings-deamon:6270): libappindicator-CRITICAL **: appindicator_set_label: assertion `IS_APP_INDICATOR (self)´ failed

---

### Post by Kirk Schnable on 2012-12-07
I have never noticed huge logs in that folder myself. I did find this page about what that folder is, and how to turn off the logs for certain programs:
[http://ifdeflinux.blogspot.com/2012/05/job-logging-in-upstart-big-upstart.html](http://ifdeflinux.blogspot.com/2012/05/job-logging-in-upstart-big-upstart.html)

That being said, I would expect log rotate to move the files and eliminate them before they get so large. 

I'd be curious to see the output of:
```
cd /var/log/upstart/
du -ch *
```

Do you have any reason to believe log rotate's default settings would have been modified on your system?  How frequently is this lightdm error recorded in the log file?  Is the error you pasted above the only significant one, and it is being repeated tons of times, or are there other obvious errors in the log file mentioned?

---

### Post by MacOsX74 on 2012-12-08
Here are the output.

```
xbmc@Xbmc-Server:~$ cd /var/log/upstart/
xbmc@Xbmc-Server:/var/log/upstart$ du -ch *
4,0K    alsa-restore.log.1.gz
4,0K    alsa-restore.log.2.gz
4,0K    console-setup.log.1.gz
4,0K    console-setup.log.2.gz
4,0K    console-setup.log.3.gz
4,0K    console-setup.log.4.gz
4,0K    console-setup.log.5.gz
4,0K    console-setup.log.6.gz
4,0K    console-setup.log.7.gz
4,0K    container-detect.log.1.gz
4,0K    container-detect.log.2.gz
4,0K    container-detect.log.3.gz
4,0K    container-detect.log.4.gz
4,0K    container-detect.log.5.gz
4,0K    container-detect.log.6.gz
4,0K    container-detect.log.7.gz
4,0K    cryptdisks-enable.log.1.gz
4,0K    cryptdisks-enable.log.2.gz
4,0K    cryptdisks-enable.log.3.gz
4,0K    cryptdisks-enable.log.4.gz
4,0K    cryptdisks-enable.log.5.gz
4,0K    cryptdisks-enable.log.6.gz
4,0K    cryptdisks-enable.log.7.gz
4,0K    cups.log.1.gz
4,0K    cups.log.2.gz
4,0K    cups.log.3.gz
4,0K    cups.log.4.gz
4,0K    cups.log.5.gz
4,0K    cups.log.6.gz
4,0K    cups.log.7.gz
4,0K    failsafe-x.log.1.gz
4,0K    failsafe-x.log.2.gz
4,0K    failsafe-x.log.3.gz
4,0K    failsafe-x.log.4.gz
4,0K    failsafe-x.log.5.gz
4,0K    gssd.log.1.gz
4,0K    gssd.log.2.gz
4,0K    gssd.log.3.gz
4,0K    gssd.log.4.gz
4,0K    gssd.log.5.gz
4,0K    gssd.log.6.gz
4,0K    gssd.log.7.gz
4,0K    hybrid-gfx.log.1.gz
4,0K    hybrid-gfx.log.2.gz
4,0K    hybrid-gfx.log.3.gz
4,0K    hybrid-gfx.log.4.gz
4,0K    hybrid-gfx.log.5.gz
4,0K    hybrid-gfx.log.6.gz
4,0K    hybrid-gfx.log.7.gz
104M    lightdm.log.1.gz
96M    lightdm.log.2.gz
60K    lightdm.log.3.gz
52K    lightdm.log.4.gz
52K    lightdm.log.5.gz
48K    lightdm.log.6.gz
12K    lightdm.log.7.gz
4,0K    modemmanager.log.1.gz
4,0K    modemmanager.log.2.gz
4,0K    modemmanager.log.3.gz
4,0K    modemmanager.log.4.gz
4,0K    modemmanager.log.5.gz
4,0K    modemmanager.log.6.gz
4,0K    modemmanager.log.7.gz
4,0K    module-init-tools.log.1.gz
4,0K    module-init-tools.log.2.gz
4,0K    module-init-tools.log.3.gz
4,0K    module-init-tools.log.4.gz
4,0K    module-init-tools.log.5.gz
4,0K    module-init-tools.log.6.gz
4,0K    module-init-tools.log.7.gz
4,0K    mysql.log.1.gz
4,0K    mysql.log.2.gz
4,0K    mysql.log.3.gz
4,0K    mysql.log.4.gz
4,0K    mysql.log.5.gz
4,0K    mysql.log.6.gz
4,0K    mysql.log.7.gz
4,0K    networking.log.1.gz
4,0K    networking.log.2.gz
4,0K    networking.log.3.gz
4,0K    networking.log.4.gz
4,0K    networking.log.5.gz
4,0K    networking.log.6.gz
4,0K    networking.log.7.gz
4,0K    network-interface-eth0.log.1.gz
4,0K    network-interface-eth0.log.2.gz
4,0K    network-interface-eth0.log.3.gz
4,0K    network-interface-eth0.log.4.gz
4,0K    network-interface-eth0.log.5.gz
4,0K    network-interface-eth0.log.6.gz
4,0K    network-interface-eth0.log.7.gz
4,0K    network-interface-tap0.log.1.gz
4,0K    procps-static-network-up.log.1.gz
4,0K    procps-static-network-up.log.2.gz
4,0K    procps-static-network-up.log.3.gz
4,0K    procps-static-network-up.log.4.gz
4,0K    procps-static-network-up.log.5.gz
4,0K    procps-static-network-up.log.6.gz
4,0K    procps-static-network-up.log.7.gz
4,0K    procps-virtual-filesystems.log.1.gz
4,0K    procps-virtual-filesystems.log.2.gz
4,0K    procps-virtual-filesystems.log.3.gz
4,0K    procps-virtual-filesystems.log.4.gz
4,0K    procps-virtual-filesystems.log.5.gz
4,0K    procps-virtual-filesystems.log.6.gz
4,0K    procps-virtual-filesystems.log.7.gz
4,0K    rsyslog.log.1.gz
4,0K    rsyslog.log.2.gz
4,0K    rsyslog.log.3.gz
4,0K    rsyslog.log.4.gz
4,0K    rsyslog.log.5.gz
4,0K    rsyslog.log.6.gz
4,0K    rsyslog.log.7.gz
4,0K    statd.log.1.gz
4,0K    statd.log.2.gz
4,0K    statd.log.3.gz
4,0K    statd.log.4.gz
4,0K    statd.log.5.gz
4,0K    statd.log.6.gz
4,0K    statd.log.7.gz
4,0K    udev-fallback-graphics.log.1.gz
4,0K    ureadahead.log.1.gz
8,0K    ureadahead.log.2.gz
4,0K    ureadahead.log.3.gz
4,0K    ureadahead.log.4.gz
4,0K    ureadahead.log.5.gz
4,0K    ureadahead.log.6.gz
8,0K    ureadahead.log.7.gz
4,0K    ureadahead-other.log.1.gz
4,0K    ureadahead-other.log.2.gz
4,0K    ureadahead-other.log.3.gz
4,0K    ureadahead-other.log.4.gz
4,0K    ureadahead-other.log.5.gz
4,0K    ureadahead-other.log.6.gz
4,0K    ureadahead-other.log.7.gz
4,0K    vsftpd.log.1.gz
4,0K    vsftpd.log.2.gz
200M    totalt
xbmc@Xbmc-Server:/var/log/upstart$ 
```The wierd thing is that now the 31,6 gb file is gone. I havent done anything.
Now there is only xxxxx.log.x.gz folders. before I had one of each xxxxxx.log.
How is that.

---

### Post by spec36 on 2012-12-08
Run this command to show your file system info and drive space USE%, Available, etc... What do you see?

```
df -h
```

---

### Post by spec36 on 2012-12-08
If you want to watch the filesize of the lightdm logs run this command.  It will show you any changes happening in realtime / near-realtime to those files.

```

cd /var/log/upstart
sudo watch -d "du -ch * | grep -i lightdm" 
```

---

### Post by MacOsX74 on 2012-12-08
> **spec36 said:**
> Run this command to show your file system info and drive space USE%, Available, etc... What do you see?

```
df -h
```

Output of df -h:
```
xbmc@Xbmc-Server:~$ df -h
Filsystem                     Storlek Använt Ledigt Anv% Monterat på
/dev/mapper/Xbmc--Server-root     40G   9,5G    28G  26% /
udev                             7,9G   4,0K   7,9G   1% /dev
tmpfs                            3,2G   1,2M   3,2G   1% /run
none                             5,0M      0   5,0M   0% /run/lock
none                             7,9G    80K   7,9G   1% /run/shm
/dev/sde1                        228M   153M    64M  71% /boot
overflow                         1,0M    56K   968K   6% /tmp
/dev/md0                          11T   7,0T   3,3T  69% /media
xbmc@Xbmc-Server:~$ 
```

---

### Post by spec36 on 2012-12-08
Based off the USE% (Anv%) of your partitions you do not appear to have maxed out any of the partitions. Are you still getting the error?

---

### Post by MacOsX74 on 2012-12-09
> **spec36 said:**
> Based off the USE% (Anv%) of your partitions you do not appear to have maxed out any of the partitions. Are you still getting the error?

No. The error is gone. Lets see if it comes back.

---

### Post by Pjotr123 on 2012-12-09
As it concerns an SSD, I would issue a manual trim command, to make sure you regain as much space as possible:
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-How-to-execute-TRIM-manually](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-How-to-execute-TRIM-manually)

---

### Post by TheFu on 2012-12-09
> **spec36 said:**
> Run this command to show your file system info and drive space USE%, Available, etc... What do you see?

```
df -h
```

There is another type of file system storage that can prevent new files from being stored - an inode. Use 
```
df -i
```
to see the available inodes on each file system.  I haven't had that issue for a few years, but back in the EXT2 days, running out of inodes was much more common especially on systems with many, many, many tiny files.

---

### Post by MacOsX74 on 2013-03-17
Now the problem is back. Same lightdm log. I removed the file but i dont get back the space on the harddrive. I cant even start firefox so that i can copy the output from terminal. 
If i run df -h it says 100% used.  40gb total and 39 gb used. 
If i run
Code:

[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]cd /var/log/upstart/[/FONT]
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]du -ch *[/FONT]
Then it says 23m total. I dont have any big files there anymore. Before i removed the file i had one that was 32 gb. 


Why dosent i get my space back when i removed the file.
The file was locked so i used sudo nautilus  when i removed it. 

[COLOR=#000000][FONT=Ubuntubeta][/FONT][/COLOR]

---

### Post by coffeecat on 2013-03-17
> **MacOsX74 said:**
> 

Why dosent i get my space back when i removed the file.
The file was locked so i used sudo nautilus  when i removed it. 


If you opened a sudo nautilus file browser and simply used the delete key, then you moved the file to root's trash. That is why you are not getting any space back. If you need to use a root nautilus (and you would be advised to use "gksudo nautilus" not sudo nautilus) then you need to hard delete with shift+delete. Alternatively, use "sudo rm" from the terminal.

The "deleted" file(s) will be sitting in /root/.local/share/Trash.

---

### Post by TheFu on 2013-03-17
There are 2 types of areas that can be "out of storage."   
* df -h
* df -i

If you have lots of small files, it is possible to run out  of inodes.  A few weeks ago, I ran out again on a server. The default inode reservations for small HDD partitions are often not enough - at least for people who use separate development environments for perl or ruby (perlbrew/rvm/rbenv) solutions.

Anyway, check both types - inodes will cause storage to run out even with TBs of storage available. [https://en.wikipedia.org/wiki/Inode](https://en.wikipedia.org/wiki/Inode) explains.

---

### Post by MacOsX74 on 2013-03-18
> **coffeecat said:**
> If you opened a sudo nautilus file browser and simply used the delete key, then you moved the file to root's trash. That is why you are not getting any space back. If you need to use a root nautilus (and you would be advised to use "gksudo nautilus" not sudo nautilus) then you need to hard delete with shift+delete. Alternatively, use "sudo rm" from the terminal.

The "deleted" file(s) will be sitting in /root/.local/share/Trash.

Thanks! This worked fine. The file is gone and my space is back. 
Time to find out whats causing the huge log file. 
What is the different between sudo nautilus and gksudo nautilus?

---

### Post by schragge on 2013-03-18
As upstart runs when you boot the system, */var/log/upstart* will grow with each reboot. So, you can reboot and watch the difference.
> [COLOR=#000000]What is the different between sudo nautilus and gksudo nautilus?[/COLOR]
See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by rnerwein on 2013-03-19
hi macos
the big file isn't gone. look here:

4,0K    hybrid-gfx.log.6.gz 4,0K    hybrid-gfx.log.7.gz [COLOR=#ff0000]104M    lightdm.log.1.gz 96M    lightdm.log.2.gz[/COLOR] 60K    lightdm.log.3.gz 52K    lightdm.log.4.gz 52K    lightdm.log.5.gz 48K    lightdm.log.6.gz 12K    lightdm.log.7.gz 4,0K    modemmanager.log.1.gz

as you see the size - there is a run-away logging - the file was rotated and ziped.
have a look at the contens of the logfile to see whats make lightdm so confused.
ciao

---

### Post by MacOsX74 on 2013-03-22
Now its back with an 33Gb log file after a few restarts. Can´t open the  file so i´m gonna try to copy the file to another computer to see what  it says. Not that I understand much but you guys do.

---

### Post by MacOsX74 on 2013-03-23
this is the errormessage in the lightdm.log

23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 
23/03/2013 14:46:16 Authentication deferred - ignoring client message 

think it has something to do with remote desktop.
23/03/2013 14:46:16 Authentication deferred - ignoring client message

---

### Post by MacOsX74 on 2013-03-23
> **rnerwein said:**
> hi macos
the big file isn't gone. look here:

4,0K    hybrid-gfx.log.6.gz 4,0K    hybrid-gfx.log.7.gz [COLOR=#ff0000]104M    lightdm.log.1.gz 96M    lightdm.log.2.gz[/COLOR] 60K    lightdm.log.3.gz 52K    lightdm.log.4.gz 52K    lightdm.log.5.gz 48K    lightdm.log.6.gz 12K    lightdm.log.7.gz 4,0K    modemmanager.log.1.gz

as you see the size - there is a run-away logging - the file was rotated and ziped.
have a look at the contens of the logfile to see whats make lightdm so confused.
ciao

Thats nothing compared to 33Gb.

---

