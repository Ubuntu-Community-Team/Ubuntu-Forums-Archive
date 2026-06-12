---
title: "Stop Ubuntu from auto-downloading from [possibly ubuntu official] servers. 16.04"
date: 2017-05-17
forum: General Help
---

### Post by santhust on 2017-05-17
Hello :)

Problem [Short]: I notice Ubuntu starts auto downloading from from some servers which by their domain names appear to be official for Ubuntu. I want to stop this behaviour.

Problem [Detail]: I have noticed a number of times that **Ubuntu 16.04 starts to auto download in the background**. I installed etherape ( [http://etherape.sourceforge.net/](http://etherape.sourceforge.net/) ) which is a network monitor tool to see from where the downloading occurs. Some of the example domain names of the servers are: cdce.sin002.internap.com, chillipepper.canonical.com, sadalbari.canonical.com, etc. From their names it seems they have some relation to Canonical the company behind Ubuntu. In one go it downloads about 100 MB or more data. This happens roughly once a week, or sometime even twice a week.

**I am often on a limited data mobile internet connection**. I cannot afford this background downloading often. Also this sometimes decreases the bandwidth available to other task if I am at them. I want to stop this behaviour of Ubuntu. 

I do not understand why this happens. What is its purpose?

I have tried a number of suggestions from Internet, e.g., completely turning off auto update of software from Synaptic Package Manager and also from Terminal, but nothing has stopped this behaviour of  Ubuntu.

I have noticed this behaviour in Ubuntu 16.04. Or if it is there in other versions, I am unaware of it.

**Please help me to stop this behaviour of Ubuntu**. Fed up with this I am considering switching over to other Linux distros, but do not really want to.

Any suggestion is heartily welcome.

---

### Post by Bucky Ball on 2017-05-17
> **santhust said:**
> ... I am considering switching over to other Linux distros ...

And that would make a difference because? Not sure that would make any difference. If you could take note of where these downloads are coming from would help us help you. An address or mirror. 

Try going to 'Software and Updates> Updates' tab and click the box next to 'When there are security updates'. You have some options there. Is yours set to download and install automatically?

Also in Software and Updates> Ubuntu Software' tab, next to 'Download from' what mirror have you got selected? In the Other Software' tab, have you added any third-party PPAs manually?

---

### Post by howefield on 2017-05-17
Do you have unattended-upgrades switched on ?

What's in ...

```
ls /var/log/unattended-upgrades
```

---

### Post by vasa1 on 2017-05-17
And is popcon a possibility?>  The popularity-contest package sets up a cron job that will
 periodically anonymously submit to the Ubuntu developers
 statistics about the most used Ubuntu packages on this system.
 .
 This information helps Ubuntu make decisions such as which packages
 should go on the first CD. It also lets Ubuntu improve future versions
 of the distribution so that the most popular packages are the ones which
 are installed automatically for new users.from [https://launchpad.net/ubuntu/xenial/amd64/popularity-contest/1.57ubuntu1](https://launchpad.net/ubuntu/xenial/amd64/popularity-contest/1.57ubuntu1)

[s]But it may not be installed by default. At least I don't have it on Lubuntu 16.04[/s]
```
apt policy popularity-contest
popularity-contest:
  Installed: 1.64ubuntu2
  Candidate: 1.64ubuntu2
  Version table:
 *** 1.64ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by santhust on 2017-05-17
$ ls /var/log/unattended-upgrades/
unattended-upgrades-dpkg.log
unattended-upgrades-dpkg.log.1.gz
unattended-upgrades-dpkg.log.2.gz
unattended-upgrades-dpkg.log.3.gz
unattended-upgrades-dpkg.log.4.gz
unattended-upgrades-dpkg.log.5.gz
unattended-upgrades-dpkg.log.6.gz
unattended-upgrades.log
unattended-upgrades.log.1.gz
unattended-upgrades.log.2.gz
unattended-upgrades.log.3.gz
unattended-upgrades.log.4.gz
unattended-upgrades.log.5.gz
unattended-upgrades.log.6.gz

---

### Post by santhust on 2017-05-17
@Bucky Ball

> If you could take note of where these downloads are coming from would help us help you.

The most I know are these domain names:

cdce.sin002.internap.com
chillipepper.canonical.com
sadalbari.canonical.com

These are only some of the names. It keeps changing.

> Try going to 'Software and Updates> Updates' tab and click the box next to 'When there are security updates'. You have some options there. Is yours set to download and install automatically?

set to: Display immediately

> Also in Software and Updates> Ubuntu Software' tab, next to 'Download from' what mirror have you got selected? 

Download from: Server for India

> In the Other Software' tab, have you added any third-party PPAs manually? 
Yes have added some PPAs manually, but after installation I have unchecked the box in front of them, so they do not figure in updates.

---

### Post by howefield on 2017-05-17
Unattended-upgrades will work in the background upgrading existing packages where applicable and log the detail to that folder.

Open up the unattended-upgrades-dpkg.log and the unattended-upgrades.log to see what has been downloaded and upgraded. The others are compressed previous logs with the same data. I'd imagine that accounts for the canonical servers presence but I don't know what the internap server is for.

---

### Post by santhust on 2017-05-17
I had a discussion on this matter on Ubuntu channel of freenode.net:

Now implemented one of the suggestions
$  sudo systemctl disable apt-daily.timer
$ sudo apt-get update && sudo apt-get dist-upgrade #when required to update

---

