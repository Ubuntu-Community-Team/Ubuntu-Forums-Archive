---
title: "Update Manager Auto-Install ALL"
date: 2012-11-27
forum: General Help
---

### Post by jim_deadlock on 2012-11-27
In Update Manager settings it's possible to set security updates to install automatically in the background, is there any way to set it so that *ALL* updates install automatically?

---

### Post by jim_deadlock on 2012-11-28
Anyone?

---

### Post by raja.genupula on 2012-11-28
Hi i got this answer but its sounds like to be a way of terminal .
[http://askubuntu.com/questions/35053/how-do-i-enable-automatic-updates-of-all-packages](http://askubuntu.com/questions/35053/how-do-i-enable-automatic-updates-of-all-packages)

---

### Post by jim_deadlock on 2012-11-28
Thanks, this looks like just what I need, I'll try it and mark this solved when I can confirm.

---

### Post by Cheesemill on 2012-11-28
Or you could just add the following command to roots crontab:
```
apt-get update && apt-get -y dist-upgrade
```
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by jim_deadlock on 2012-11-28
I did try a cron job a while back but it didn't work so I may have been using the wrong code, I'll give yours a try if the other method fails, thanks.

---

### Post by raja.genupula on 2012-11-29
> **Cheesemill said:**
> Or you could just add the following command to roots crontab:
```
apt-get update && apt-get -y dist-upgrade
```[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)


I think 

> apt-get update ; apt-get -y upgrade ;apt-get -y dist-upgrade 

would be a good idea because i read this 

[http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade](http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade)

---

### Post by Cheesemill on 2012-11-29
No need for 'apt-get upgrade' of you are going to do 'apt-get dist-upgrade' straight afterwards, it won't make any difference to the end result.

---

### Post by raja.genupula on 2012-11-30
> **Cheesemill said:**
> No need for 'apt-get upgrade' of you are going to do 'apt-get dist-upgrade' straight afterwards, it won't make any difference to the end result.

Actually I am thinking about this .

> dist-upgrade in addition to performing the function of upgrade,        also intelligently handles changing dependencies with new versions        of packages; apt-get has a "smart" conflict resolution system, and        it will attempt to upgrade the most important packages at the        expense of less important ones if necessary. So, **dist-upgrade        command may remove some packages.**

---

### Post by jim_deadlock on 2012-12-15
I'm marking this solved as the link in post #3 above is working nicely. Here is a summary of the solution:

Edit this file:
```
/etc/apt/apt.conf.d/50unattended-upgrades
```
Uncomment this line:
```
"${distro_id}:${distro_codename}-updates";
```

3rd party repositories are excluded so you either need to update those by the normal method or else find out what extra line you need to add.

---

