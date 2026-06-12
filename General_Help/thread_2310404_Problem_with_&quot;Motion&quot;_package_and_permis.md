---
title: "Problem with &quot;Motion&quot; package and permisions."
date: 2016-01-18
forum: General Help
---

### Post by davidjhi on 2016-01-18
Hello Ubuntu!

Im triying to make a security camera server with and old PC and ubuntu, Im using motion as recording software, i have used the same package in the past without too much effort.

But this time, im having troubles with the permisions, first of all; when you install motion and user and a group its created:

motion:motion

So when you run motion, it should run as motion user; but its not working....

First step, activate daemon mode on the config files of motion; this line should run a script located in /etc/init.d/motion

The script basically config the permisions, main lines:

> mkdir -m 02750 /var/run/motion
            chown motion:motion /var/run/motion
             mkdir -m 02750 /var/log/motion
            chown motion:adm /var/log/motion


I think the script never worked quite well for me because triying to run motion i was getting the same errors about the said folders, so i run the commands manually.

And after that, i can finally run motion without error's!:

> [0] [NTC] [ALL] conf_load: Processing thread 0 - config file /etc/motion/motion.conf
[0] [NTC] [ALL] motion_startup: Motion 3.2.12+git20140228 Started with SDL support
[0] [NTC] [ALL] motion_startup: Logging to file (/var/log/motion/motion.log)


But aparently, its not working, the server on localhost:8081 its not running and im not getting any recors, i checked and the motion service and its not running as motion user, its running as root! (i think...)
> ps aux | grep -v grep | grep motion
root      2028 16.6  2.1 138404 42324 ?        Sl   19:49   4:32 motion


Wich is weird because i run "motion", not "sudo motion", im not even asked for a sudo password.

But.... when i run sudo motion, the software works OK and its recording!, but i need to run motion as motion user (better practice?)... and for adding the motion service to the startup.

Im missing something?

---

