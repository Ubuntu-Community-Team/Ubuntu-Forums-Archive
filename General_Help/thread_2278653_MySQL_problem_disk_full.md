---
title: "MySQL problem disk full"
date: 2015-05-18
forum: General Help
---

### Post by yoran2 on 2015-05-18
Can someone help me with my server? I got a problem with a full disk and mysql. I am looking for a specialist. I am a total newbie with ubuntu. Looks like mysql is not working right. Can someone help me over Skype? Add me and i can give you server details.
SKYPE: yoran.elektrischefietsen.com

Thanks for help!

---

### Post by Elizine on 2015-05-18
Hi,

You will have to free your disk space then only MySQL will work.

---

### Post by Lars Noodén on 2015-05-18
To find out what is using your disk you have several options.  If you are in a graphical environment you can run the Disk Usage Analyzer (aka baobab) and that will give you a display over what is used where.  If you are using pure shell, then you can use [du](http://manpages.ubuntu.com/manpages/trusty/en/man1/du.1.html) to show you disk usage and [df](manpages.ubuntu.com/manpages/trusty/en/man1/df.1.html) to see overall capacity.  

```

df -h
sudo du -sh /var/
sudo du -sh /home/

```

---

### Post by yoran2 on 2015-05-18
I know i have to free my disk, but i dont know how and what i can delete. Offcourse i know what i have on the server but i use it for three things, two wordpress websites and openx (adserver). I don't know what i can delete?
I did your shell option:


Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       79G   74G  1.0G  99% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           393M  196K  393M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M     0  100M   0% /run/user
overflow        1.0M  1.0M     0 100% /tmp

sudo du -sh /var/ gives:
23G     /var/

sudo du -sh /home/ gives:
176K    /home/

---

### Post by yoran2 on 2015-05-18
I can put in some codes in shell , nothing more , i am a totally newbie . :P

---

### Post by Lars Noodén on 2015-05-18
> **yoran2 said:**
> 
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       79G   74G  1.0G  99% /

...

sudo du -sh /var/ gives:
23G     /var/

sudo du -sh /home/ gives:
176K    /home/

Ok.  /var and /home were likely culprits but turn out to be ok in this case.  /var is probably ok depending on what you have there.  We'll have to look elsewhere some other directory is eating up the space.   Try checking each top level directory individually:

```

sudo find / -type d -maxdepth 1 -exec du -sh "{}" \; 2>/dev/null 

```

The "du -sh", you know already, the "{}" means the output from [find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html) in this context.

The "/" means start looking in / aka the top level
"-type d" means find directories, AND
"-maxdepth 1" means don't go deeper than one level, AND
"-exec" means run the following, up to but not including the next "\;"

The "2>/dev/null" redirects > any errors or complaints from the preceding program(s) to the bitbucket aka /dev/null.  That's to make the output easier to read but you can leave it off if you like.

---

### Post by yoran2 on 2015-05-18
This is what i get:

> 

75G     /
4.0K    /dev
1.0M    /tmp
963M    /root
0       /sys
23G     /var
12K     /srv
19M     /opt
8.0K    /media
40G     /BACKUP
303M    /boot
4.0K    /mnt
0       /proc
16K     /lost+found
192K    /run
176K    /home
4.0K    /lib64
9.6M    /bin
2.1G    /lib
839M    /usr
11M     /sbin
8.4M    /etc
103M    /backup
root@vita01:~# sudo
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...




---

### Post by SeijiSensei on 2015-05-18
My guess is you have a lot of stale log files in /var/log. Take a look in /var/log/apache2 in particular.

---

### Post by yoran2 on 2015-05-18
Could be.. but what do i have to do in shell commands ? I totally dont know how to get there , or to delete files or .. ?

---

### Post by Lars Noodén on 2015-05-18
> **yoran2 said:**
> Could be.. but what do i have to do in shell commands ? I totally dont know how to get there , or to delete files or .. ?

To look into /var you can modify the above "find" like this, and maybe it would be good to look in /BACKUP also since it is using a lot of space too.

```

sudo find /var -type d -maxdepth 1 -exec du -sh "{}" \; 2>/dev/null

sudo find /BACKUP -type d -maxdepth 1 -exec du -sh "{}" \; 2>/dev/null

```

---

