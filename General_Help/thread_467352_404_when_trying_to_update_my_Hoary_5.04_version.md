---
title: "404 when trying to update my Hoary 5.04 version"
date: 2007-06-07
forum: General Help
---

### Post by theQmaster on 2007-06-07
It looks that the repositories got moved or removed. Can you tell me how I update my box ?

Thanks,
Q

---

### Post by dagrump on 2007-06-07
I might be all wet here, but I'd say you would be better served to download a newer version as support for that has most likely been dropped. 6.06 (dapper) is long term support, 6.10 & 7.04 are also out there.

---

### Post by theQmaster on 2007-06-07
It looks that the repositories got moved or removed. Can you tell me how I update my box ?

Thanks,

---

### Post by theQmaster on 2007-06-07
When i use apt-get update all the links in the repository come backw with a 404...
This machine is used as server and if I upgrade I need a quick and smart way of doing it.


> **dagrump said:**
> I might be all wet here, but I'd say you would be better served to download a newer version as support for that has most likely been dropped. 6.06 (dapper) is long term support, 6.10 & 7.04 are also out there.

---

### Post by borahshadow on 2007-06-07
for a server probably go with 6.06 (dapper) it has LTS(long term support) as 5.04 I believe no longer has any updates

---

### Post by theQmaster on 2007-06-07
agree but how do I smoothly upgrade to 6.06 or later ?
Is there a magic bullet ?

---

### Post by DoctorMO on 2007-06-07
I think 5.04 is 25 months old, far older than the 18 months of support that you get. upgrade to dapper which has 5 years of support (LTS) or continue to not be updated.

---

### Post by bapoumba on 2007-06-08
Threads merged.

---

### Post by PatrickMay16 on 2007-06-08
> **theQmaster said:**
> It looks that the repositories got moved or removed. Can you tell me how I update my box ?

Thanks,

I think it might still be possible for you to use apt-get to upgrade your hoary to breezy (I don't think they've taken away breezy's repository yet), and then upgrade breezy to Dapper.

It's what I'd do.

These might help:

[https://help.ubuntu.com/community/BreezyUpgrade](https://help.ubuntu.com/community/BreezyUpgrade)
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by theQmaster on 2007-06-15
Thanks a lot Patrick! I will give it a shot!

:popcorn:

> **PatrickMay16 said:**
> I think it might still be possible for you to use apt-get to upgrade your hoary to breezy (I don't think they've taken away breezy's repository yet), and then upgrade breezy to Dapper.

It's what I'd do.

These might help:

[https://help.ubuntu.com/community/BreezyUpgrade](https://help.ubuntu.com/community/BreezyUpgrade)
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by bapoumba on 2007-06-15
Are the breezy repos still there? I gathered from other thread they were gone too. 
If you need to jump to dapper, a reinstall would be better. Do you have a separate /home ?

---

### Post by theQmaster on 2007-06-15
I will check tonight... As far as upgrading... I don't think I can, that will make my server unavailable plus I'd have to configure it for about 2-3 days - this is a production server. I hope I can do it the apt-get way...

My best!

---

### Post by bapoumba on 2007-06-15
Just an idea: if the breezy repos are not avalable, you can upgrade from a cd.
[http://old-releases.ubuntu.com/releases/5.10/]("http://old-releases.ubuntu.com/releases/5.10/")
(put the cd in the sources.list).

---

### Post by theQmaster on 2007-06-15
yeah it seems that there breezy is not available... I have to use the CD 
how do I put the cd in the source.list ?

---

### Post by theQmaster on 2007-06-16
Breezy's repos are not online. I created a CD from the ISO file and I managed to move from Hoary to Breezy pretty easy. The only thing troubled me was firefox initially won't update it and the scary part is I don't know what made it to work. Once that was installed i realised that the apache2 did not start and won't start issuing /etc/init.d/apache2 start - no message whatsoever!

So I moved along to Dapper, changed the sources.list and all was pretty smooth. I forced apache2 to reinstall and not all is good. But I get a strange error/warning when I start apache.

[B]mc@gsi:~$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of apache 2.0 web server...                                   WARNING: Require ThreadsPerChild > 0, setting to 1
WARNING: Require ThreadsPerChild > 0, setting to 1
                                                                         [ ok ][/B]

My ThreadsPerChild is greater and 1 in httpf.conf

My target is to move to 6.10, edgy, so I can install postgresql 8.2 - one more step. 

How do enable kdm remote access from command line or How do I change the default display manager ?


Thanks!
Q

---

