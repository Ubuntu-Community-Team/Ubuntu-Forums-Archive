---
title: "Problems..."
date: 2007-11-23
forum: General Help
---

### Post by motermouth on 2007-11-23
Alright...first of all when i upgraded to the newest ubuntu like last week my wireless card (broadcom 4318) showed up in the restricted drivers page. When i go to enable it...it says that it cannont find the firmware from the internet. Then also today i was on the internet and i was trying to install the adobe flash player plug-in but it can't find it!! Whats going on??

---

### Post by taurus on 2007-11-23
I bet all your repos in /etc/apt/sources.list are all commented out, with a # in front.  Therefore, it can't find anything.  So, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front all the lines that start with **deb** and **deb-src**.  Save it and close gedit window.

Then, run

```
sudo apt-get update
sudo apt-get upgrade
```
You should be able to install whatever you need from the repos now.

```
sudo apt-get install flashplugin-nonfree
```

---

