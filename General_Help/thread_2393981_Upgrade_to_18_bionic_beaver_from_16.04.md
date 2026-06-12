---
title: "Upgrade to 18 bionic beaver from 16.04"
date: 2018-06-11
forum: General Help
---

### Post by cam17 on 2018-06-11
My 16.04 LTS has not notified me of any new upgrade even though I have 16.04LTS configured for "notifiy when a new ubuntu version" is set for "long term support versions". I have also tried the CLI "do-release-upgrade" and I get the result "no new release found". My 16.04 LTS is using  [http://fireball-public.phys.wvu.edu/mirror/ubuntu](http://fireball-public.phys.wvu.edu/mirror/ubuntu).

Any ideas as to what I should do to upgrade?

---

### Post by deadflowr on 2018-06-11
Notifications for long term release upgrades for 16.04 to 18.04 won't show until sometime in late July or Early August.
They don't open the channel, officially, until the first point release 18.04.1.

(Unofficially, you can upgrade now by invoking the development flag setting for update-manager
either run 
 press alt + F2 to open the command bar and run
```
update-manager -d
```
or
```
do-release-upgrade -d
```
either method should then show 18.04 as available to upgrade to.)

Note the -d, means development as this method may or may not still have kinks that need to be worked out as of yet.
So user's choice.

---

### Post by cam17 on 2018-06-11
Thanks. I will wait for the 18.041 version. No rush Just thought it would be available in June-2018.

---

### Post by cam17 on 2018-08-02
My Ubuntu 16.04 still has not seen an upgrade to bionic beaver? Why?

---

### Post by coffeefiend on 2018-08-02
> **deadflowr said:**
> Notifications for long term release upgrades for 16.04 to 18.04 won't show until sometime in late July or Early August.
They don't open the channel, officially, until the first point release 18.04.1.

(Unofficially, you can upgrade now by invoking the development flag setting for update-manager
either run 
 press alt + F2 to open the command bar and run
```
update-manager -d
```
or
```
do-release-upgrade -d
```
either method should then show 18.04 as available to upgrade to.)

Note the -d, means development as this method may or may not still have kinks that need to be worked out as of yet.
So user's choice.

Yep. That's what I had to do. No issues found yet.

---

### Post by Impavidus on 2018-08-03
I remember that I had to wait for two weeks after 18.04 was released before I could upgrade from 17.10. I was in no hurry, so I waited another month. People who use the LTS releases instead of the interim releases are supposed to be in no hurry to get the latest software.

---

### Post by cam17 on 2018-08-12
18.04.1 lts is available for download as of Aug-12-2018. Why is my 16 LTS version not receiving the update? Is there a way to determine ?

---

### Post by PaulW2U on 2018-08-12
> **cam17 said:**
> 18.04.1 lts is available for download as of Aug-12-2018. Why is my 16 LTS version not receiving the update?
See [https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html). The enabling of the upgrade notification hasn't been forgotten. :)

---

### Post by termibuntu on 2018-08-12
You should do:
```
sudo do-release-upgrade -d
```
to upgrade to 18.04. 18.04.1 is already available.
However, I wouldn&#8217;t do it if you use the nvidia-304 driver, as it has been removed from the repositories. If you do so, you will have to use the nouveau drivers.

---

