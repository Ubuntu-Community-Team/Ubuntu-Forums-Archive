---
title: "how to get a list of available high urgency updates only"
date: 2008-01-24
forum: General Help
---

### Post by freemant on 2008-01-24
Hi,

We keep track of available updates to our Ubuntu LTS 6.0.6 servers using "apt-get -s upgrade". However, we're getting frequently many updates and most of which are non-critical ones. I noticed that in the changelog each update is marked with an urgency. Is it possible to somehow only list those with a high urgency? I can't just remove the ubuntu-updates URL from the source list as it could contain both critical and non-critical updates.

Thanks for any idea!

---

### Post by Rocket2DMn on 2008-01-24
You can disable everything in your /etc/apt/sources.list file except the 2 (deb and deb-src) for "dapper-security" ones.  Even more specifically you could disable all the ones except for "dapper-security main restricted" (deb and deb-src).  This is done by placing a "#" at the start of the line.
To edit:
```
sudo nano /etc/apt/sources.list
```
or use your other favorite command line text editor (emacs, vi, etc...).

---

### Post by freemant on 2008-01-24
Thanks for the reply. However, I am concerned that by disabling dapper-updates altogether we will miss really critical updates. Is this a valid concern? Or is it a recommended practice to disable dapper-updates in an enterprise environment?

---

### Post by Rocket2DMn on 2008-01-24
I'm going to double check this exactly, but if you can post your sources.list file that would be great.  You should be able to right click and copy over an SSH session
```
cat /etc/apt/sources.list
```

---

### Post by freemant on 2008-01-24
Here is the file content:

deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Rocket2DMn on 2008-01-24
OK, first I would comment out the cdrom source in your sources.list file, otherwise when you upgrade it will look there, not see the CD and throw an error.  Place a "#" in front of that line and run
```
apt-get update
```

Other than that, we should be able to leave your sources.list as is so if later you want to install stuff from other repositories, you won't have to fiddle with it.  In order to just get security updates, you will change your upgrade command to this:
```
apt-get upgrade --target-release dapper-security
```
When I tested this myself (under gutsy), it limited the number of updates I saw, but just showed them as "gutsy-updates", so I'm not really sure what to think.  This SHOULD be how it is done.  Perhaps the updates were marked as security updates and just not placed under the security.ubuntu.com location?

The other option is comment the other stuff in your sources.list so it looks like this:
> # deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
Don't forget to run update afterward:
```
sudo apt-get update
```
This method will require you to uncomment the lines if you go looking for other software in the repos at a later date.

---

