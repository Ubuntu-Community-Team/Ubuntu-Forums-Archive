---
title: "Can't Upgrade From Lubuntu 19.04 to Lubuntu 19.10"
date: 2020-04-26
forum: General Help
---

### Post by ggsantafe on 2020-04-26
I want to upgrade to Lubuntu 19.10 but I can't get the updater to notify me that 19.10  is available.
I saw a post to check that /etc/update-manager/release-upgrades has Prompt=normal which it does.
I saw another post to run do-release-upgrade which gives me the following:
  Checking for a new Ubuntu release
  Your Ubuntu release is not supported anymore.
  For upgrade information, please visit:  
  [http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)
I visited the site but it only talks about ubuntu.
Does anyone know what I should do next?  
Thanks in advance for any help.

---

### Post by CelticWarrior on 2020-04-26
The time to rlease upgrade from 19.04 is over, the support ended in January, hence the message > Your Ubuntu release is not supported anymore..

Please do your backup - something you should have already -, download the ISO for 20.04 as there's no point in installing 19.10 which has only a few months left of support) and install fresh as usual. Lubuntu 20.04 has support until April 2023. Enjoy (and prepare for the next upgrade before April 2023).

---

### Post by grahammechanical on 2020-04-26
This wiki page will explain how to do an End Of Life upgrade

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You need to run this command

```
gedit /etc/apt/sources.list
```

Look for lines that begin like this

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic universe

That is a source or archive for my install of 18.04 (bionic). Your install should show disco instead of bionic. There will be several line like that for all the repositories that your install is using.

Not you must change each archive line and replace the gb.archive.ubuntu.com or whatever is in your sources.list on your install with 

> old-releases.ubuntu.com

Save the sources.list file and run

```
sudo apt update
sudo apt upgrade
```

that you bring your installation up to date. This is needed. Then run do-release-upgrade. You may find that Lubuntu uses the same archive servers as Ubuntu.

Before you do this please prepare yourself to do a fresh install. This method can work. I have done it but it can be a tests of our nerves.

Regards.

---

### Post by ggsantafe on 2020-04-26
Ok.  Thanks for the quick reply.  I will look into the two suggestions and move on from there.

---

