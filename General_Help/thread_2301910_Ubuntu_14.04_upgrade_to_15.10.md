---
title: "Ubuntu 14.04 upgrade to 15.10"
date: 2015-11-06
forum: General Help
---

### Post by rhandy2 on 2015-11-06
Hello

I make upgrade to 15.10 not intencionally.

I just want to upgrade fail2ban I make this mistake

[h=2]Download Page for fail2ban_0.9.3-1_all.deb[/h][COLOR=#333333][FONT=Ubuntu]If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/wily/aptitude") or [synaptic]("http://packages.ubuntu.com/wily/synaptic") to download and install packages, instead of doing so manually via this website.
You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:
deb [http://*cz.archive.ubuntu.com/ubuntu](http://*cz.archive.ubuntu.com/ubuntu)* wily main universe
Replacing *cz.archive.ubuntu.com/ubuntu* with the mirror in question.
[/FONT][/COLOR]



I add [COLOR=#333333]deb http://[/COLOR]*cz.archive.ubuntu.com/ubuntu*[COLOR=#333333] wily main universe to [/COLOR][COLOR=#333333][FONT=monospace]/etc/apt/sources.list

after I make

```
#sudo apt-get update
#sudo apt-get upgrade
```

and I have 15.10 installed.


My problem is support, because 14.04 have support to 2019, and 15.10 only have 9 months???[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-11-06
*Thread moved to **General Help**.*

Can we clarify a couple of things. 

You were running 14.04 and when you added that repository and updated you are now on 15.10? What is telling you you are now running 15.10? Could you let us see the output of this command, please:

```
lsb_release -a
```

Firstly, there is no direct upgrade from 14.04 to 15.10 so that path is not really possible without a clean install of 15.10. You would need to get to 15.10 by net upgrade by going through all the releases to 15.10. I.e. you would need to upgrade 14.04 LTS> 14.10> 15.04> 15.10.

By adding that repo, the system may be showing a false positive, so to speak, as adding one repo is not going to upgrade the entire OS to a release three releases up. 

We'll know more when we see the output of that command.

The easiest way to rectify this is to delete the repo you've added and put the old one back to the way it was before, then update/upgrade as you did previously. Reboot and you should be back to square one. Then we can deal with the fail2ban issue.

Is there any reason you simply didn't install fail2ban in 14.04 LTS? It is right there in the repos (Software Centre). You don't need to add it manually by adding a repo.

---

### Post by rhandy2 on 2015-11-06
Output:

 > No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 15.10
 Release:        15.10
Codename:       wily


Anything wrong????

---

