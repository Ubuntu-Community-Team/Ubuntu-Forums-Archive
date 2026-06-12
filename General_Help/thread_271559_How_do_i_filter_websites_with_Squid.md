---
title: "How do i filter websites with Squid"
date: 2006-10-04
forum: General Help
---

### Post by CameronCalver on 2006-10-04
Hey i have just finished setting up squid and it is going fine i got cache working fine but i would like to block certain websites and block certain websites containing certain words i have tryed many how to's but none of them work

---

### Post by Abhi Kalyan on 2007-01-28
Check you previous thread have posted some thing theres
dansguardian is good try it.
It works for me, Hope it does for you

---

### Post by Abhi Kalyan on 2007-12-12
Dear CameronCalver,
you need dansguardian,
sudo apt-get install dansguardian
if you get some messing with clamav do the following instead:
sudo apt-get install clamav clamav-freshclam
then install dansguardian.
open
/etc/dansguardian/dansguardian.conf
and place # before UNCONFIGURED.
Now point all your traffic to 8080 instead of 3128.
Viola the blocking is done.

get to
/etc/dansguardian/
you will see loads of files , description of those and their role in the schemem of things is explained in 
/etc/dansguardian/dansguardian.conf itself.

You could some some thing else also,
install webmin.
it makes life way too simple
get it at:
[http://sourceforge.net/project/showfiles.php?group_id=17457&package_id=13391&release_id=552588](http://sourceforge.net/project/showfiles.php?group_id=17457&package_id=13391&release_id=552588)
use Gdebi to install it. (just right click pal)
once it is installed get dansguardian module from here:
[http://sourceforge.net/project/showfiles.php?group_id=51969](http://sourceforge.net/project/showfiles.php?group_id=51969)
go to 
[https://localhost:10000](https://localhost:10000)
login
and go to webmin administration, there select the dansguardian module for install. its a very simple process, you will figure it out.

---
There you are now you have
squid - proxy
dansguardian  - filter
clamav - antivirus
webmin - administration made easy package
noe go to webmin, networking, get to linux firewall and go to
NAT table.
set the tables to direct data to 8080 while destination port is  80.

Phew, should work as it works for me.

One thing thought:
if you want squid to do transparency please 

you need to work on certain file,
hold on bmathis has done a great work on this topic its available here
[http://ubuntuforums.org/showthread.php?t=320733&highlight=bmathis](http://ubuntuforums.org/showthread.php?t=320733&highlight=bmathis)

all the very best

---

### Post by HermanAB on 2007-12-12
SquidGuard:
[http://aeronetworks.ca/squidguard-howto.html](http://aeronetworks.ca/squidguard-howto.html)

Cheers,

Herman

---

