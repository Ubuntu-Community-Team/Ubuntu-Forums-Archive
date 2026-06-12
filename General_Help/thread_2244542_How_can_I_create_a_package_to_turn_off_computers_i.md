---
title: "How can I create a package to turn off computers in my network?"
date: 2014-09-17
forum: General Help
---

### Post by redprive2 on 2014-09-17
Hi,

I would like to create a package to turn off computer daily at same hour: 6pm.

I know how I can add a task at cron, but my wish is to learn to create a .deb to distribute in all computer's network.

This way I wont have to go computer by computer to modify cron, else I would can do it from my server and launch it rest of the computers..

Anybody could help me?

Thank you!

---

### Post by Lars Noodén on 2014-09-17
There are several ways to set the computers to all turn off at 6pm.  If it's a small number, one way would be to just SSH in and paste a line into the crontab or add a line to /etc/rc.local to launch shutdown set for 18:00.  

However, in general, administration of many computers is usually helped by using ansible or puppet.  If you're planning on doing a lot of other maintenance, then either of these two could be worth looking at.  

If you really want a .deb package, then you'll need to set up some script in perl or dash/bash to install your cronjob and another to remove it.  Then there are a lot of tutorials on how to wrap that in a .deb package, but none of them so simple.  It's not as hard the second time but wading through all those guides the first time can be hard.  

[http://debian-handbook.info/browse/stable/debian-packaging.html](http://debian-handbook.info/browse/stable/debian-packaging.html)
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

For me the difficulty was in setting up the control file, I would start by getting the source debs for some simple packages and looking at them, too.

[https://www.debian.org/doc/debian-policy/ch-controlfields.html](https://www.debian.org/doc/debian-policy/ch-controlfields.html)

---

### Post by tgalati4 on 2014-09-17
You can create a *.deb package and send an email around to all of your users to install the new package.  Sort of like clicking on a virus in email.  Unless you have all of your computers with autoupdate turned on, you will have to perform some manual process on each computer.

[https://help.ubuntu.com/community/PythonRecipes/DebianPackage](https://help.ubuntu.com/community/PythonRecipes/DebianPackage)

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

I would personally send an email with a script to add to the user's cronjob to perform the shutdown function.  Some folks will follow the procedure correctly and get the crontab set up correctly.  Others will have problems and for those folks you will have to perform it manually.

You need to detail the Use Case carefully, because this type of script will upset users who may have to work past 6 pm.

Some computers' BIOS have a schedule feature where you can set it there as well.

---

### Post by Old_Grey_Wolf on 2014-09-17
If you are using the computers on a private network, and they have ssh enabled, then you may want to look into cssh ([ClusterSSH]("https://github.com/duncs/clusterssh/wiki")). Then you can send the shutdown command from one computer to all the others. The cron would only need to run on the one computer used to send the command via cssh. cssh should be in the repositories.

---

### Post by redprive2 on 2014-09-18
Im IT specialist in my school. I haven't users.. i have students like clients ;)

I can't say them "please install this script"... Althought, I have installed a kiosk mode distribution to this way save me a lot of errors..

I have a server that send packages to all clients ever time they  turn on..... If I have uploaded a new package into server, its installed in all computers... 

Now, Im learning how to create packages and I want that my first package will be used to configure computers to turn off all days at 6 pm. School close at 5:30 pm and some students don't turn off computer al last hour... This way I will be sure that all computers are sleeping, like me :-)

I suppose that I will have to create a bash script with one line that will be added to crontab user, is it correct?

Second step will be to create a .deb... is it correct?

Thank you!!!

---

### Post by btindie on 2014-09-18
If you're the 'IT specialist' in your school then you should have root access to all the computers that you administer.

Creating a package is a bit of an overkill for that task. Really you'd want to run it from one central point.

Install a public key for the root account on all clients so from your server you're able to ssh into them as root without the need for a password or Passphrase on our private key. At the minimum it's best to set 'PermitRootLogin without-password' in /etc/ssh/sshd_config.

You then just need to install pssh (parallel-ssh) on your server so you can execute the same command on multiple computers.

Create a text file with the hostnames/IP addresses one per line, e.g. /etc/default/myclients

Then create a bash script on your server that will try and connect to each host and power them down.

```
#!/bin/sh
SSHOPTS="-q -O StrictHostKeyChecking=no UserKnownHostsFile=/dev/null -O GlobalKnownHostsFile=/dev/null -i ~/.ssh/id_rsa"
parallel-ssh -h /etc/default/myclients -t 1 -x "$SSHOPTS" poweroff

```

And then simply create a crontab entry for root to run that script. (Assuming your private key is called ~/.ssh/id_rsa)

The only thing you may want to create a deb for is your root ssh public key to have it installed automatically. Make sure the permissions are set correctly. Or at least have it installed automatically when you roll out a new client.

Then to add a new client to the shutdown script, all you need to do is had the hostname (if using DNS) or the IP address.

---

