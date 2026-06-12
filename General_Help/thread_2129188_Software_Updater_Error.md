---
title: "Software Updater Error"
date: 2013-03-25
forum: General Help
---

### Post by mayagrafix on 2013-03-25
I got this error today:
> 
W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886, W:Failed to fetch [http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
After some sleuthing, me thinks it has to do with either the new version of Libre-Office (4.0) which I installed recently (instead of waiting for Updater to do so), or the Mint Cinnamom desktop, which I also added recently to my log in choice for a quick tryout.

I was planning on UN-installing Cinnamon today anyway. Or how do you guys recommend I proceed?

---

### Post by dino99 on 2013-03-25
very common question :D  [http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)

and check that ppa have a "quantal" repo indeed (an other common error :confused: )

---

### Post by ibjsb4 on 2013-03-25
And for your 404 error, there is no quantal package.

[http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/](http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/)

---

### Post by mayagrafix on 2013-03-27
'kay, tried the above links and procedures and still get this:
[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/FailedRepository_zpse642b12d.png[/IMG]
same error as in first post. Any other suggestions? I already un installed the cinnamon desktop, (apt-get remove cinnamon) and added repository keys for merlwiz79, so what should I do now?

---

### Post by Bashing-om on 2013-03-27
mayagrafix;

Let us see what the package manager relates. Post the output of terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
```[INDENT=2]so begins a tale in the telling
[/INDENT]

---

### Post by mayagrafix on 2013-03-28
These are the last lines of **apt-get Update:**
> Fetched 1,431 kB in 37s (37.8 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
And here are last lines of **apt-get Upgrade:**
> Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Do you need to see the whole kibosh? here is end of **apt-get Upgrade** second time:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Thanx for ur help ):P

---

### Post by plucky on 2013-03-28
> W: Failed to fetch [http://ppa.launchpad.net/merlwiz79/c...source/Sources](http://ppa.launchpad.net/merlwiz79/c...source/Sources) 404 Not Found

Remove that PPA from Software Sources as there is no repository for Quantal.

See [Here](http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/)

Good Luck

---

### Post by Bashing-om on 2013-03-28
mayagrafix;
Plucky beat me to it. +1 , I see no ppa available at this time past precise.
[INDENT=3]
'nuff said ?

[/INDENT]

---

### Post by mayagrafix on 2013-03-28
Wonderful! I must be getting the hang of this thing, because after the above suggestion, I knew to go to Ubuntu Software Center, look up Software Sources in the Edit Menu and delete the offending PPA. Who says old dogs can't learn new tricks?

Thank you so much, Team Canonical!

---

### Post by Bashing-om on 2013-03-28
mayagrafix;

Ain't no step for a stepper //small steps can end the longest journey
[INDENT=2]
enjoy ubuntu

[/INDENT]

---

