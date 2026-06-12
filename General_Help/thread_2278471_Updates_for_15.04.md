---
title: "Updates for 15.04"
date: 2015-05-16
forum: General Help
---

### Post by rob64 on 2015-05-16
I'm relatively new to ubuntu and I recently upgraded to 15.04 but unable to receive updates.   I get the following messages.     I notice in the text it refers to 14.04 and not 15.04 

'Failed to download repository information'   

'check internet connection'

'W:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch [http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/source/Sources](http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bashing-om on 2015-05-16
rob64; Hello;

2 issues related to package management.
1) 'W:Failed to fetch cdrom://Ubuntu 14.04 LTS :
Uncheck the 'CDROM' box in software sources; then we might want to check what source is available:
```

cat -n /etc/apt/sources.list

```

2) , W:Failed to fetch [http://ppa.launchpad.net/gnome-split...source/Sources](http://ppa.launchpad.net/gnome-split...source/Sources) 404 Not Found
That PPA is not supported in vivid; disable them also in software sources.
see:
[http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/](http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/)
There is no index for vivid.

Now what results when terminal commands 
```

sudo apt-get update
sudo apt-get upgrade

```
are executed ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by rob64 on 2015-05-16
Source is internet

I used 'select best sever' which gave me  [http://pubmirrors.dal.corespace.com/ubuntu/](http://pubmirrors.dal.corespace.com/ubuntu/)

Following update received 


W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/source/Sources](http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/gnome-split-team/ppa/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by monkeybrain20122 on 2015-05-16
Well you have your sources messed up.

Type 'Software&Update" in the dash to bring up the source manager (not sure what it is called) from the tab Ubuntu software uncheck the box CD-rom. That should fix all the fail to fetch cdroms

As Bashing-om said the gnome-split ppa doesn't support 15.04, you should  remove it from your source, go to the tab "Other Software" and remove the entry for the ppa. And then close it and it will prompt you to reload the package manager to update the database. It should fix it (Bashing-om's post basically told you the same thing but using the command lines)

Btw. Next time do a clean install if you want to "upgrade" your OS. Do not go the "upgrade" route, it has a high probability of messing up especially if you use ppas and third party apps (including drivers) and it takes a very long time. Also it is better to wait a month before you use a new release as your main OS, new releases are always buggy, and ppas are probably not up for the new release yet.

---

### Post by rob64 on 2015-05-16
OK it's fixed, I thought just unchecking the ppa was sufficient.   It's removed.

---

### Post by Bashing-om on 2015-05-16
rob64; Great;

unchecking the PPA in software sources should have been good 'nuff . It is forseeable that the PPA maintainers will get caught up and have support for 15.04 ( or maybe it passes testing and gets included in the software repository )  then one could have re-enabled the PPA.


and we will cross
[INDENT][INDENT][INDENT][INDENT]other bridges when we come to them
[/INDENT][/INDENT][/INDENT][/INDENT]

---

