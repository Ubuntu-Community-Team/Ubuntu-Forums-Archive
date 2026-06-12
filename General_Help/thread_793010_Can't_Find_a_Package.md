---
title: "Can't Find a Package"
date: 2008-05-13
forum: General Help
---

### Post by don7777 on 2008-05-13
Hi,

I'm fairly new to Ubuntu and Linux administration.  I'm running Ubuntu 6.06 (Dapper). I'm trying to install a package (request tracker) and am following instructions here: [http://wiki.bestpractical.com/view/UbuntuInstallGuide2](http://wiki.bestpractical.com/view/UbuntuInstallGuide2)

The instructions indicate that rt3.6-apache2 must be installed with this command: 
apt-get install rt3.6-apache2

However, when I run the command, I get this message:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package rt3.6-apache2

Seems it can't find rt3.6-apache2.

How can I figure out how to get rt3.6-apache2? And, once I figure out where it is, how do I install it?

Thanks so much in advance,
Don

---

### Post by minaev on 2008-05-13
This package is in the `universe' repository, which you have to enable.

See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Vivaldi Gloria on 2008-05-13
You can find info on a package by searching it here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Here is your package:

[http://packages.ubuntu.com/dapper-backports/rt3.6-apache2](http://packages.ubuntu.com/dapper-backports/rt3.6-apache2)

Enable your universe repo (as suggested above) or download it manually from the above page.

---

### Post by don7777 on 2008-05-13
I have enabled the universe repository in /etc/apt/sources.list with the following line: 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

note: the line is uncommented in /etc/apt.sources.list.

However, I still get the same message indicating that apt-get could not find package rt3.6-apache2.

Any other thoughts?

Thanks,
Don


> **minaev said:**
> This package is in the `universe' repository, which you have to enable.

See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by don7777 on 2008-05-13
thanks for the reply and the pointers.

See my most recent post: apt-get still cannot find rt3.6-apache2.

What am I doing wrong? :)

By the way, how did you so quickly know to look in dapper-backports from packages.ubuntu.com?

Thanks,
Don

> **Vivaldi Gloria said:**
> You can find info on a package by searching it here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Here is your package:

[http://packages.ubuntu.com/dapper-backports/rt3.6-apache2](http://packages.ubuntu.com/dapper-backports/rt3.6-apache2)

Enable your universe repo (as suggested above) or download it manually from the above page.

---

### Post by Monicker on 2008-05-13
Did you do apt-get update after making the change?

---

### Post by don7777 on 2008-05-13
yep, did "sudo apt-get update" after changing sources.list.

> **Monicker said:**
> Did you do apt-get update after making the change?

---

### Post by Monicker on 2008-05-13
> **don7777 said:**
> yep, did "sudo apt-get update" after changing sources.list.

Hrmm. From searching packages.ubuntu.com, rt3.4-apache2 is available for Dapper, but not 3.6

[http://packages.ubuntu.com/search?keywords=rt3&searchon=names&suite=dapper&section=all]("http://packages.ubuntu.com/search?keywords=rt3&searchon=names&suite=dapper&section=all")

---

### Post by don7777 on 2008-05-13
yep, but from an earlier post you can find the "dapper-backports"  fo rt3.6 here: 
[http://packages.ubuntu.com/dapper-backports/misc/](http://packages.ubuntu.com/dapper-backports/misc/)

Is there some line I should have in sources.list in order to get at the backports?

Thanks,
Don

> **Monicker said:**
> Hrmm. From searching packages.ubuntu.com, rt3.6-apache2 should be available

[http://packages.ubuntu.com/search?keywords=rt3&searchon=names&suite=dapper&section=all]("http://packages.ubuntu.com/search?keywords=rt3&searchon=names&suite=dapper&section=all")

---

### Post by Monicker on 2008-05-13
Ahh. Add this.

[deb http://archive.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted]("deb http://archive.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted")

---

### Post by don7777 on 2008-05-13
that did it!!! (one of those "duh!" moments: when I went back to sources.list, I saw the backports section of the file with lines which needed to be uncommented.

Thanks for all the help!!!! Your folks are awesome!!



> **Monicker said:**
> Ahh. Add this.

[deb http://archive.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted]("deb http://archive.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted")

---

