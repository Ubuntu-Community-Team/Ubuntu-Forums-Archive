---
title: "How can I convert a debian server install to Ubuntu server?"
date: 2006-08-15
forum: General Help
---

### Post by sclough on 2006-08-15
This is in the spirit of another thread I had posted where this question came up.  I'm leasing a new dedicated server, but the hosting provider will not install ubuntu because it's not part of their standard installs.  He doesn't care if I run it since I manage my own box, he just won't install it, which leads me to...

He will install debian.  So, just what does it take to "convert" a plain debian install to Ubuntu?

---

### Post by t3r0 on 2006-08-15
> **sclough said:**
> This is in the spirit of another thread I had posted where this question came up.  I'm leasing a new dedicated server, but the hosting provider will not install ubuntu because it's not part of their standard installs.  He doesn't care if I run it since I manage my own box, he just won't install it, which leads me to...

He will install debian.  So, just what does it take to "convert" a plain debian install to Ubuntu?



Hi!


There are many ways to install an different distribution to remote server, most likely many more that I know / can think of :D but here's few ways...  


**-** ask your host if they have KVM units available for rent and if they can help with the Ubuntu install cd.... if yes, then just connect thru the KVM and reboot & install ubuntu normally.... 




**-** Buy a second hd to your server, install ubuntu with your servers settings locally to a PC and then make an image of that installation (HD) to a file, upload it to the server and copy it to the second hd, modify the servers boot loader config to boot from the second HD and reboot ;) 



Well these are just examples, there are many ways to do this, but yes in deed, it's possible ;) 


- Tero

PS. ```
$ man dd
```


PPS. Shoud this be in server talk -section?

---

### Post by sclough on 2006-08-15
Well, the problem is that I have no physical access to the box and he won't install anything, including putting in a disk, that is not part of their standard installs (debian, Fedora, Centos, FreeBSD, RHEL).  There is the way of letting him install debian or Fedora on a small partition and then manually putting it on there, but it seems more intuitive to let him do a bare bones debian install and then "upgrade" that to ubuntu.  I'm assuming I could just change apt-get's sources files and then to apt-get update, apt-get upgrade or something similar.

The reason I didn't have it in the server section was because I figured it was more of a generic "how to I convert a debian install to ubuntu" question.  Apparently this is covered in the ubunutu hacks book, but I hate to buy a book for one chapter...

---

### Post by sclough on 2006-08-15
It looks like it's just:

1.  Basic debian install.
2.  Update sources.
3.  Run apt-get update, apt-get dist upgrade, then choose the right kernel.

Can anyone confirm?

---

### Post by David Corrales on 2006-08-16
If you're just running servers in a CLI environment why not just use Debian? Debian stable is not called stable just for marketing, it really is stable :)

Second, since Ubuntu is based on Debian the source updating might work since the required Ubuntu packages would just overwrite/add over the regular Debian ones but I'd try it first. Get Vmware Server [www.vmware.com](www.vmware.com) which is free, do a netinstall in a virtual machine and try the source change move to see if you have any trouble with services.

---

### Post by sclough on 2006-08-16
That's a good idea about trying it with VMWare.

I guess I wanted Ubuntu because of it's more frequent releases and it's overall polish.  I have noticed a lot more people running it on servers, so it must have an advantage to pure debian, right?

---

### Post by David Corrales on 2006-08-16
Personally, I'd go with Sarge for a regular server. It's been tried for some years now and it's stable. It also has a 2.6.x kernel if you need it, available through packages.
Actually, having a slower release cycle is good for servers. You don't want to keep squashing bugs every 6 months.

---

### Post by sclough on 2006-08-16
I agree about not wanting to change releases every 6 months.  In fact, my server now is still running FreeBSD 4.8 because I haven't wanted to fool with 5.X or 6.X just yet.  I just liked the polish of dapper and was thinking of installing dapper on the server since it does have long term support.  I wasn't going to update the server to edgy after 6 months.  In fact, after setup I prefer to pretty much stay with security patches until a compelling reason to upgrade comes along.  For example, my production server still runs MySQL 4.x, PHP 4.x, and Apache 1.3x.

---

### Post by David Corrales on 2006-08-16
Oh cool, then you know the drill :cool:
But yeah, server wise I think Debian stable is still better or equal than Ubuntu. Ubuntu's polish is more desktop oriented.

---

### Post by sclough on 2006-08-16
Ok, you may about have me convinced. :rolleyes: 

Are debian's repositories as up to date as ubuntus?  I'm thinking about apache, php, mysql, etc.  Since I'm going through the hassle of bringing up a new server now is the time for me to change to apache 2.0, php 5, mysql 5, etc.  And are their repositories as deep as ubuntus as far as server features?

I guess I figure I've "learned" ubuntu and don't feel like going through another learning curve having never fooled with debian and not knowing how different it is.  Ubuntu is the only deb based distro I've worked with.  Work uses RedHat and I've only used that plus Centos, Suse, Gentoo, and Mandrake (years ago).

---

### Post by David Corrales on 2006-08-17
Debian has 3 branches. Stable (sarge), testing (sid) and unstable (etch). Usually servers use the stable branch of course. You won't find the latest stuff here but it's stable. There's backports which might provide newer server/packages.

You could also try a sid server for newer stuff if you really need to get the latest although the latest will never be as rock solid compared more throughly tested base.

Ubuntu doesn't really have a lot more stuff than debian, and less so on the server side. Again, most of their work is desktop based. In fact I love the apt-get packaging style from debian, that's why I use ubuntu.

---

