---
title: "Failed to fetch update problems"
date: 2016-10-01
forum: General Help
---

### Post by wes333 on 2016-10-01
Having trouble with "sudo apt-get upgrade"
Getting spammed with the "Failed to fetch" error
I cant find any solutions online so i've come to you all, any help would be much appreciated!

---

### Post by deadflowr on 2016-10-01
Please post the output from both
```
sudo apt-get update
sudo apt-get upgrade
```

I've also edited your thread's title to something more accessible to the problem.

---

### Post by wes333 on 2016-10-01
Here are the images:
Output from "sudo apt-get upgrade"
[http://imgur.com/a/XL8V2](http://imgur.com/a/XL8V2)
After entering "Y"
[http://imgur.com/a/uCRsr](http://imgur.com/a/uCRsr)   (There were a lot more saying "Failed to Fetch" but they went by to quickly for me to capture, but you get the gist)

Output from "sudo apt-get update"
[http://imgur.com/a/J3Av3](http://imgur.com/a/J3Av3)

---

### Post by cariboo on 2016-10-01
It would be a lot easier for us to help you, if you just copied and pasted the terminal output into your next post, be sure to use code tags like this:

[noparse]```
update
Hit:1 http://security.ubuntu.com/ubuntu yakkety-security InRelease
Hit:2 http://ca.archive.ubuntu.com/ubuntu yakkety InRelease         
Hit:3 http://archive.canonical.com/ubuntu yakkety InRelease         
Hit:4 http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu xenial InRelease
Hit:5 http://ca.archive.ubuntu.com/ubuntu yakkety-updates InRelease 
Hit:6 http://ca.archive.ubuntu.com/ubuntu yakkety-backports InRelease
Hit:7 http://ca.archive.ubuntu.com/ubuntu yakkety-proposed InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
14 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
```[/noparse]

which should look like this if done right:

```
update
Hit:1 http://security.ubuntu.com/ubuntu yakkety-security InRelease
Hit:2 http://ca.archive.ubuntu.com/ubuntu yakkety InRelease         
Hit:3 http://archive.canonical.com/ubuntu yakkety InRelease         
Hit:4 http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu xenial InRelease
Hit:5 http://ca.archive.ubuntu.com/ubuntu yakkety-updates InRelease 
Hit:6 http://ca.archive.ubuntu.com/ubuntu yakkety-backports InRelease
Hit:7 http://ca.archive.ubuntu.com/ubuntu yakkety-proposed InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
14 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
```

---

### Post by RobGoss on 2016-10-01
If you're using Ubuntu 16.04  open **Software & updates**, Click on **Other Software**. You should see a list of software you have installed just uncheck the ones you see in the list that say **failed to fetch, **these are the ones causing the issue with your installation. After you've unchecked them click on close and run the following command again:

```
sudo apt-get update
```

---

### Post by deadflowr on 2016-10-01
Seems like a network connection problem.

Does networking function correctly otherwise?

Perhaps try a quick ping, like so:
```
ping -c 5 www.ubuntu.com
```

Does it output 5 entries or does it tell you unknown host or network unreachable?
(Or some other error)

---

### Post by wes333 on 2016-10-01
It says unknown host

> **RobGoss said:**
> If you're using Ubuntu 16.04  open **Software & updates**, Click on **Other Software**. You should see a list of software you have installed just uncheck the ones you see in the list that say **failed to fetch, **these are the ones causing the issue with your installation. After you've unchecked them click on close and run the following command again:

```
sudo apt-get update
```
I am using the ubuntu server command line so I dont know how I would be able to get there

> **cariboo said:**
> It would be a lot easier for us to help you, if you just copied and pasted the terminal output into your next post, be sure to use code tags like this:

[noparse]```
update
Hit:1 http://security.ubuntu.com/ubuntu yakkety-security InRelease
Hit:2 http://ca.archive.ubuntu.com/ubuntu yakkety InRelease         
Hit:3 http://archive.canonical.com/ubuntu yakkety InRelease         
Hit:4 http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu xenial InRelease
Hit:5 http://ca.archive.ubuntu.com/ubuntu yakkety-updates InRelease 
Hit:6 http://ca.archive.ubuntu.com/ubuntu yakkety-backports InRelease
Hit:7 http://ca.archive.ubuntu.com/ubuntu yakkety-proposed InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
14 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
```[/noparse]

which should look like this if done right:

```
update
Hit:1 http://security.ubuntu.com/ubuntu yakkety-security InRelease
Hit:2 http://ca.archive.ubuntu.com/ubuntu yakkety InRelease         
Hit:3 http://archive.canonical.com/ubuntu yakkety InRelease         
Hit:4 http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu xenial InRelease
Hit:5 http://ca.archive.ubuntu.com/ubuntu yakkety-updates InRelease 
Hit:6 http://ca.archive.ubuntu.com/ubuntu yakkety-backports InRelease
Hit:7 http://ca.archive.ubuntu.com/ubuntu yakkety-proposed InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
14 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
```

Yea sorry, I just didn't wanna go through the hassle as it was a different computer and Ubuntu command line is the only OS on it

---

### Post by wes333 on 2016-10-02
Bump

---

### Post by deadflowr on 2016-10-02
Yep, something's quirky with networking.
Unfortunately, that all but ends how much help I can be, but I'll leave with a few things to look into

Perhaps take a look at the network card:
```
sudo lshw -C network
```
and maybe
```
ifconfig -a
```

Also, since you don't have readily access to post the output directly, if using images, attach them;
See:  [https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098]("https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098")
on how to use attachments.

---

### Post by wes333 on 2016-10-02
When I typed in "sudo lshw -C network"
It showed me ethernet and wireless and it said they were both disabled

---

