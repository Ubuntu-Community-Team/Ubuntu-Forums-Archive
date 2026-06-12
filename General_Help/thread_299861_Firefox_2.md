---
title: "Firefox 2"
date: 2006-11-14
forum: General Help
---

### Post by geovino on 2006-11-14
When is Firefox 2 going to be available via Synaptic?

---

### Post by testube_babies on 2006-11-14
It's available by default in Edgy.  For Dapper or earlier you should look around in backports or just install it yourself.  Here's a tutorial:

[http://www.ubuntuforums.org/showthread.php?t=283965](http://www.ubuntuforums.org/showthread.php?t=283965)

---

### Post by aysiu on 2006-11-14
If you don't want to upgrade to Edgy, I'd use this script to install 2.0:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by testube_babies on 2006-11-14
> **aysiu said:**
> If you don't want to upgrade to Edgy, I'd use this script to install 2.0:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

I was just about to edit my earlier post to include that script....it makes life a lot easier.

---

### Post by geovino on 2006-11-15
> **aysiu said:**
> If you don't want to upgrade to Edgy, I'd use this script to install 2.0:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Thanks, I'll look into it. I don't think I'll be upgrading Dapper, from what I read about Edgy, its mainly for testers and not the rest of the public that wants a solid, stable OS. I don't see why Ubuntu can't just add it to Synaptic so you don't have to jump through so many hoops just to upgrade Firefox. I hear that Feisty Fawn will be the next stable version of Ubuntu and that comes out next April 19. I'll wait until then.

---

### Post by dweez on 2006-11-15
1) Edgy isn't just for testers anymore.  It's been released and is as stable a build as Dapper was for me.

2) FF2 might eventually find it's way to Backports, but no one would expect the developers to change the base install apps for a release once-removed from the latest.

---

### Post by geovino on 2006-11-16
I looked into the upgrade. So by typing: gksu "update-manager -c" in the terminal it will do the upgrade to Edgy? 

Will it leave my installed programs to be used in Edgy? 

That's very smooth if it can do it.

---

### Post by s_h_a_d_o_w_s on 2006-11-16
> **aysiu said:**
> If you don't want to upgrade to Edgy, I'd use this script to install 2.0:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Yes that script works great. But remember to choose en_GB as locale to get your firefox in english. :-)

---

### Post by rosieg on 2006-11-16
I am a completely newbie and don't have a clue - I just upgraded to Edgy and everything I had already installed was still there. Only problem I've had was that it wasn't mounting my swap space but that was easily fixed.

---

### Post by dweez on 2006-11-16
Yeah, resetting the swap space is fairly easy but if you have a decent amount of RAM, odds are, your swap rarely gets used anyway.

---

### Post by geovino on 2006-11-16
> **dweez said:**
> Yeah, resetting the swap space is fairly easy but if you have a decent amount of RAM, odds are, your swap rarely gets used anyway.

How do you reset the swap space? I have 1GB RAM.

---

### Post by geovino on 2006-11-17
Im trying to upgrade to Edgy and I get this error:

davek@davek-desktop:~$ gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpXtETTQ/edgy.tar.gz'
authenticate '/tmp/tmpXtETTQ/edgy.tar.gz' against '/tmp/tmpXtETTQ/edgy.tar.gz.gpg'
davek@davek-desktop:~$


Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found

how do I add these repositories?

---

### Post by dweez on 2006-11-20
Sorry, here's some info to help you with your swap file

(referencing [http://www.ubuntuforums.org/showthread.php?t=270317&highlight=how+to+enable+swap+file](http://www.ubuntuforums.org/showthread.php?t=270317&highlight=how+to+enable+swap+file) )

do a "free -m" in your terminal
> 
me@mycomputer:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        492         10          0        165        112
-/+ buffers/cache:        214        288
Swap:          815        114        701


if "Swap:" has all zeros, then your swap file isn't mounted.

To recreate your swap file and enabled it, use the following commands in your terminal.  In the following example, the swap partition happens to be hda3.  You can run fdisk in your terminal then "m" <enter> then "p" <enter> to get a listing of your hdds/partitions to determine the proper location of your swap partition:
> 
sudo mkswap /dev/hda3
sudo swapon /dev/hda3


As for adding those repositories, they are already added.  You can do a "sudo vi /etc/apt/sources.list" to view your list.  The error is coming up because your computer cannot reach those locations.  404 typically means the servers are no longer running.

If you still need to upgrade to Edgy, try reading through the howto here ===> [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by geovino on 2006-11-21
Well I tried to do the upgrade to Edgy and it went fine for the first two hours then the network  froze in part three and I had to reboot which killed Ubuntu completely! I won't do one of those upgrades again unless I have it on CD! For now I'll use PCLinuxOS which works equally as well as Ubuntu and maybe in a while I'll install Ubuntu again on the dead partition.

---

### Post by geovino on 2006-11-24
Well, I guess I'll have to eventually install Ubuntu again to that same hda2 partition.

---

