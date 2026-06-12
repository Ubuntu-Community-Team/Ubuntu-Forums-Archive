---
title: "Problems Uninstalling AVG"
date: 2007-04-08
forum: General Help
---

### Post by M$LOL on 2007-04-08
I installed AVG Free for Linux from the Grisoft website. It doesn't work properly, so I tried to uninstall it, but I can't. I tried this
[https://answers.launchpad.net/ubuntu/+ticket/4392]("https://answers.launchpad.net/ubuntu/+ticket/4392") but I still can't remove the thing. Help anyone?

---

### Post by zvacet on 2007-04-08
```
 sudo apt-get remove --purge correct_package_name
```

---

### Post by airxart on 2007-04-08
Well that was worth a shot.


[[IMG]http://img296.imageshack.us/img296/8091/screenshotfp4.th.png[/IMG]](http://img296.imageshack.us/my.php?image=screenshotfp4.png)




[[IMG]http://img458.imageshack.us/img458/2562/ubuntupkgedgy8pj0.th.png[/IMG]](http://img458.imageshack.us/my.php?image=ubuntupkgedgy8pj0.png)


[[IMG]http://img458.imageshack.us/img458/4711/ubuntupkgedgy9ez4.th.png[/IMG]](http://img458.imageshack.us/my.php?image=ubuntupkgedgy9ez4.png)



I have also tried sudo -query -l **avg*`

sudo dpkg -r

sudo dpkg-P avg75fld

sudo /etc/init.d/avg start
sudo dpkg --remove avg75fld

sudo dpkg --remove --force-all avg75fld

sudo gedit /var/lib/dpkg/info/avg75fld.prem
(with this I tried adding # to invoke & /etc/init.d....lines)

no luck yet

---

### Post by mikewhatever on 2007-04-08
Try booting into recovery mode, then type sudo dpkg -P avg75fld
Note there is a space between dpkg and -

---

### Post by M$LOL on 2007-04-09
OK, I have the solution.
[COLOR="Red"]
sudo gedit /var/lib/dpkg/info/avg75fld.prerm[/COLOR]

and comment out the two parts of the file that have "if, which, fi" - put a "[COLOR="Red"]#[/COLOR]" in front of every line between the if and the fi inclusive in both cases. Then run [COLOR="Red"]sudo dpkg --remove --force-all avg75fld[/COLOR]

---

### Post by airxart on 2007-04-10
This is an e-mail I recieved from Radek V. The .deb package maintainer. 
>Hello,
>> I use AVG on some of my win boxes so I thought I would try it on
>> my ubuntu boxes.
>> Problem 1) Install .deb not as root and it will not update, say I don't 
>> have permission.
>> AVG user login was created in user panel. Could not login to it

1)
To perform update, user must be a member of group avg created
automatically during installation of avg. When adding an user
to the group, it is necessary to log out and on again so that the
changes take effect.


>> Problem 2)          Will not reinstall.
>> Problem 3)         Will not un install
>>  There seems to be no way to uninstall by convetional means.
>>  sudo dpkg -r avg75fld          >returns whats in attached files


2) 3)
To reinstall or uninstall avg, running avg daemons must be stopped.
This should be done automatically, but there is an issue with
Ubuntu 6.10 which is using dash instead of bash as a default 
/bin/sh shell and as a consequence the initscripts which are used to
stop the daemons during the process of package removing 
don't work correctly. This should be fixed in next .deb package.
As a workaround, you can either stop the daemons manually (A),
or modify the initscript files to work correctly(B).

(A)
To stop the daemons, you can kill the daemons and remove their
lockfile by running commands

$ sudo killall avgscan
$ sudo rm /var/lock/avgd

Then the reinstall or uninstall by dpkg should work.

(B)
To modify the initscripts to work correctly, change the first line
of the file /opt/grisoft/avg7/etc/init.d/avgd.all

from:

#!/bin/sh

to:

#!/bin/bash

(If you want to use email scanning connected with sendmail
via milter daemon, change also the file
/opt/grisoft/avg7/etc/init.s/avgdmilter.all
in the same way)

After this change, initscripts will use bash and work correctly,
and re/uninstall with dpkg should also work without problems.


Radek V.

---

### Post by M$LOL on 2007-04-11
OK, that clears things up a bit, but it still doesn't explain why trying to access the Test function through the GUI doesn't work. Even doing it through sudo didn't help.

---

### Post by airxart on 2007-04-12
With the current installation of AVG , I login as root to the GUI and the whole program works.
The install creates a user name, but I could never get it to work, Password??
Well thats all I've figured out.

---

