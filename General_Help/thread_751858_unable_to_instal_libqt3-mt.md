---
title: "unable to instal libqt3-mt"
date: 2008-04-10
forum: General Help
---

### Post by bpinkston on 2008-04-10
I tried to Install Virtual Box from the command line using dpkg, and it complained about several dependencies not being installed, the first of which is the libqt3-mt.  So i resigned to install it from Synaptic, when I did it errored out saying the libqt3-mt is not installable. 

I am running Gnome on Gutsy Gibbons (7.10)  I am rather new to Linux, did some work with Unix about 15 years back, and want to rid my life of Microsoft. 

Thanks, 

Brent

---

### Post by FuturePilot on 2008-04-10
Try
```
sudo apt-get install -f
```
It should install all missing dependencies.

---

### Post by bpinkston on 2008-04-11
> **FuturePilot said:**
> Try
```
sudo apt-get install -f
```
It should install all missing dependencies.

I tried that, and when it couldn't resolve the dependency it justall uninstalled the half installed Virtual Box.  I was hopeful for a moment. 

Thanks,

---

### Post by FuturePilot on 2008-04-11
Could you post your sources.list?
```
cat /etc/apt/sources.list
```
Post the output of that.

---

### Post by bpinkston on 2008-04-11
These are my sources.  Thank You

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by jocko on 2008-04-11
It could be that you are missing some repo that contain something libqt3-mt is dependent on, but I can't really see what that could be.
I see some repos are inactivated in your sources.list.

You could try this (copy-paste the commands into a terminal):

First back up your current sources.list (just in case anything would go wrong, not that I think it will):
```
cp /etc/apt/sources.list ~/sources.list.bak
```That will place a backup of your sources.list in your home directory.

Next, change your sources.list:
```
gksudo gedit  /etc/apt/sources.list
```Replace the contents with this:
```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted universe multiverse
#deb http://www.virtualbox.org/debian gutsy non-free
```Notice the inactivated lines starting with a #. As far as I know, you will not need those to solve your problem.
The first two, gutsy-backports and gutsy -proposed contain newer versions of some packages, but these are either not officially supported or not fully tested yet, so they could perhaps be a little bit less safe to use than the standard repos (but if you want to use them, remove the #).
As you mentioned virtualbox: the last line is the virtualbox repo, which you may want if you want to have the latest stable release of virtualbox instead of the virtualbox-ose that is in the gutsy repos (if you want to know the difference, check on [virtualbox.org]("http://virtualbox.org/wiki/Editions")). If you want to use it, remove the #.
Save the file and close gedit.

Now you need to reload the package information:
```
sudo apt-get update
```Now there may be some security updates to install, as some of the security repos were inactivated in your original sources.list:
```
sudo apt-get upgrade
```If apt complains about not being able to install all updates, try this:
```
sudo apt-get dist-upgrade
```


Hopefully things should work out after this. If not, you could revert to your original sources.list like this:
```
sudo cp ~/sources.list.bak /etc/apt/sources.list
sudo apt-get update
```

---

### Post by bpinkston on 2008-04-11
Thank you very much.  I will try this tonight.

---

### Post by bpinkston on 2008-04-11
Did exactly as you suggested, and now have Windows XP guest installed in Virtual Box.  Thank you again.  I am off to figure out why Virtual Box is not passing off USB to XP.  Pretty sure, I read something I just need to go find it.

---

### Post by jocko on 2008-04-12
> **bpinkston said:**
> Did exactly as you suggested, and now have Windows XP guest installed in Virtual Box.  Thank you again.  I am off to figure out why Virtual Box is not passing off USB to XP.  Pretty sure, I read something I just need to go find it.

Glad you got it working. Check [this post]("http://ubuntuforums.org/showpost.php?p=4525596&postcount=2") for solving the usb problem.

---

### Post by Dabblo on 2008-04-12
Hey guys I got router problems and I'm trying to make a static ip.. so I can port forwards an ouka chat server.r. I'm trying to get ouka to be an accessible chat server using crossover. Anyone have any ideas? 

ps sorry for posting in the wrong place I forgot where the new post button is

Dai

---

### Post by bpinkston on 2008-04-12
Thank You again.  I can't tell you how much I appreciate your help.  The USB thing worked like a charm.  I will pay this forward.  As I become more proficient with Ubuntu, I will commit more time to help other people painlessly solve problems as you have helped me.  

I would love to see the ubuntu community become so proficient at this type of support, that no one woudl ever feel the need to pay for Microsoft Wiindows again

---

