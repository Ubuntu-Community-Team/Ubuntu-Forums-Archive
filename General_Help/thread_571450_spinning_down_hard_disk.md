---
title: "spinning down hard disk"
date: 2007-10-09
forum: General Help
---

### Post by sulekha on 2007-10-09
Hi all,

I was reading the book "Beginning Ubuntu Linux" by thomas keir. In this book there
is a tip given to spin down the hard disk. the author says that it will help a lot in power savings.

he gives the tip as follows

all modern hard disks come with the ability to spin down their motors to save energy.Then,when data is requested,the motors spin up again. There may be a slight delay while this happens, and some people dislike using disk spin-down because of this. However on a notebook, it can lead to a substantial increase in battery life.On a desktop system ,it's worth considering.because over the lifetime of a
computer, it can save a lot of electricity.

on terminal type
gksu gedit /etc/hdparm.conf

spindown_time=24

you can alter the value to anything you want.each time unit is 5 seconds,so 24 equates to 120 seconds or 2 minutes

when u are finished,save the file.

Reboot for the settings to take effect

Now question is how effective is this tip ???
will it lead to substantial power savings?????

---

### Post by wieman01 on 2007-10-09
On my notebook it had no noticeable effect. I did not like the "click" sound so I turned it off (was enabled by default in Feisty).

---

### Post by dcstar on 2007-10-10
Since Linux is constantly generating various log messages, these are written to disk on a regular basis so I have my doubts that turning off a hard disk that will be restarted to write data every few minutes may be worthwhile.

The extra power to restart a drive (as well as the "wear and tear" of the process) may well outweigh the power savings during the off time.

If someone could work out a way of "quietening" Linux to minimise system/application background disk writes then this could well be worth trying (even setting up a USB stick drive for these writes would help).

---

### Post by jazzgossen on 2007-10-23
> **dcstar said:**
> If someone could work out a way of "quietening" Linux to minimise system/application background disk writes then this could well be worth trying 

There is a way. Check out laptop-mode-tools.

---

