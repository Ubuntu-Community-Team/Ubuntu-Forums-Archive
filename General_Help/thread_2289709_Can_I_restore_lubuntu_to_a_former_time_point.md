---
title: "Can I restore lubuntu to a former time point"
date: 2015-08-06
forum: General Help
---

### Post by Jonatan Formentera on 2015-08-06
Hi, I installed Lubuntu 15.04 a few days ago, but I must have done something bad and a strange line appears on the screen. I'd like to know if I can't restore the system to a former point. I tried to install TimeShift by using:
 sudo apt-add-repository -y ppa:teejee2008/ppa sudo apt-get update sudo apt-get install timeshift

But it says there is an error, just a repository is needed as an argument
Can anyone help me
Thanks

---

### Post by Rex Bouwense on 2015-08-06
Once you have done something to your system, it is a little late to install a program to restore it to a previous state.  However, in addition to Time Shift, there is Systemback [http://www.unixmen.com/systemback-restore-linux-system-previous-state/](http://www.unixmen.com/systemback-restore-linux-system-previous-state/)  These programs provide the capability that you desire but unfortunately I do not believe that they can restore to something that was not initially saved.

---

### Post by vasa1 on 2015-08-06
> **Jonatan Formentera said:**
> ... I tried to install TimeShift by using:
 sudo apt-add-repository -y ppa:teejee2008/ppa sudo apt-get update sudo apt-get install timeshift

But it says there is an error, just a repository is needed as an argument
Can anyone help me
Thanks
[The Launchpad page]("https://launchpad.net/timeshift") has this:```
sudo apt-add-repository -y ppa:teejee2008/ppa
sudo aptitude update
sudo aptitude install timeshift
```
Note these are three **separate** commands. And you can use *apt-get* instead of *aptitude*.

If you want to chain commands you need *&&* between commands. And I avoid using *-y*.

Oh, and it's unclear whether TimeShift works with 15.04.

---

### Post by howefield on 2015-08-06
> **Jonatan Formentera said:**
> Hi, I installed Lubuntu 15.04 a few days ago, but I must have done something bad and a strange line appears on the screen. I'd like to know if I can't restore the system to a former point. I tried to install TimeShift by using:
 sudo apt-add-repository -y ppa:teejee2008/ppa sudo apt-get update sudo apt-get install timeshift

But it says there is an error, just a repository is needed as an argument
Can anyone help me
Thanks

Timeshift won't allow you to go back to a point before you installed and set timeshift up, you probably don't think it will, but just in case :)

---

### Post by Jonatan Formentera on 2015-08-06
I used Vasa1's method and could install TimeShift. I would try it. Thank you to everyone

---

