---
title: "Get too many errors while updating my repository!"
date: 2007-02-24
forum: General Help
---

### Post by MichaelLi on 2007-02-24
I got too many errors while updating my repository. After I issued the update command, it downloaded all the needed software packages, and then came downloading the bug reports which didn't run so well.

#sudo apt-get dist-upgrade
... ...
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... 0% [0/27] W: end of file reached: php5
 W: not in gzip format: python-pam
 W: not in gzip format: libapache2-mod-php5
 W: not in gzip format: mysql-common
 W: not in gzip format: mysql-client-5.0
 W: not in gzip format: libmagick9
 W: not in gzip format: postgresql-doc-8.1
 W: not in gzip format: mysql-server-5.0
 W: not in gzip format: apt-utils
 ... E: Too many errors while retrieving bug reports
E: Subprocess if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi   returned a error code (10)
E: Failure running script if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi

Well, it seems there are more than 10 errors so it stops running. But I'm not so familar with the shell script. How could I fix this problem? How could I stop receiving the bug reports when I update my repository?

Thanks in advance!

---

### Post by sam81 on 2007-02-24
I'm not sure why you get the errors. Are you trying to upgrade from dapper to edgy, or from edgy to feisty? The command you give is used for upgrading the entire distribution. If all you want to do is getting updated packages you should go

#sudo atp-get update
#sudo apt-get upgrade

not dist-upgrade. 

Best luck!

---

### Post by disturbedite on 2007-02-24
i wish i could tell exactly where to look, but i don't know, but hopefully this might roughly point you in the right direction...
i don't know how you got it to show bug reports in the first place, but its seems to me that you need to remove any references to /usr/sbin/apt-listbugs apt.  except i don't know where you'd do that.  maybe a config file of some kind.

wish i could be more helpful...

---

### Post by dr_d on 2007-02-24
I recently had a similar problem, but not while dist-upgrading, just reloading the package information.

While I don't know for sure, my theory is that it has to do with corrupted local files.

Here's a link to my thread... the error I was getting was that "subprocess gzip returned an error" so I think my solution might work for you aswell. Let me know if it does:

[http://ubuntuforums.org/showthread.php?t=369001&highlight=repo+problems](http://ubuntuforums.org/showthread.php?t=369001&highlight=repo+problems)

---

### Post by floogy on 2007-03-06
```
 E: Too many errors while retrieving bug reports
```

I got the same error with some archives while fetching bugreports.
I assume, that the Problem is in the bugreports themselves, because nothing which was advised in this forum helped me.

How to disable apt-listbugs temporairily with a commandline option or config line of aptitude?

EDIT: found it: ```
sudo vi /etc/apt/apt.conf.d/10apt-listbugs
```

---

