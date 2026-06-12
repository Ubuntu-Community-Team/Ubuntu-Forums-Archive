---
title: "Can it cause any issues upgrading my Ubuntu Server from 12.04.1 to 14.04.1 LTS?"
date: 2016-05-31
forum: General Help
---

### Post by alka5eltzer on 2016-05-31
Hi All,

Being prompted when I login via SSH if I want to upgrade to 14.04.1 LTS.

I Very rarely login via SSH - I always use Webmin... so only seeing this now.

Is this recommended - is there a possibility things could go wrong and brick my system? Or is it normally OK?

Thanks

---

### Post by QDR06VV9 on 2016-05-31
There is no way to guarantee that a release upgrade won't cause issues with software or configurations. Backing up your data beforehand will make it much easier to recover in case of a problem resulting from the upgrade.
I usually use the method described here [https://www.digitalocean.com/community/tutorials/how-to-upgrade-ubuntu-12-04-lts-to-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-upgrade-ubuntu-12-04-lts-to-ubuntu-14-04-lts)
But the Golden rule for me has always been_** "Step One &#8212; Backing Up Existing Data" **_

---

### Post by mastablasta on 2016-06-01
> **alka5eltzer said:**
> 
I Very rarely login via SSH - I always use Webmin... so only seeing this now.

webmin is not supported. 

> 
Is this recommended - is there a possibility things could go wrong and brick my system? Or is it normally OK?

there is always a possibility things will go wrong. it also depends how well your services are supported by 14.04 and also how many ppas you have and such.

backup (e.g. clonezilla) and upgrade. 

or leave it - 12.04 is supported for another year and a half. plenty of time left to plan for the move.

---

### Post by mörgæs on 2016-06-01
> **mastablasta said:**
> 12.04 is supported for another year and a half. plenty of time left to plan for the move.

A little less than a year, to be correct, but I agree on the point of view: There is plenty of time, an option worth considering is a fresh install of 16.04.2 in February 2017.

---

