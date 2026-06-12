---
title: "Upgrade from CD"
date: 2007-10-03
forum: General Help
---

### Post by Black Mage on 2007-10-03
I was wondering if Ubuntu could be upgraded from a CD on the PS3 without problems.

My problem is I currenty don't have WiFi active on my PS3 thus I would need to connect through ethernet. But the ethernet is in another room and the only monitor I have is a 500 pound behemonth that won't fit through any doorways(and i'm not that strong) so I'm stuck with using a wireless connection.

So if I upgraded to a newer version of Fiesty Fawn or Gutsy Gibbon so that I could get the wireless working, but use a CD with an ISO of either of those and use the command

Code:

gksu "update-manager -c"


would that create different problems or it would run smoothy?

---

### Post by zvacet on 2007-10-03
To upgrade from CD you need alternate CD.You can upgrade to one version at the time

Dapper>Edgy>Feisty>Gutsy

I don´t know wich version do you have,so here it is 

[https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")

And when you are finish 

```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
```

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

```
sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list
```



Maybe you want to wait for few more weeks and download Gutsy.In case you want to do fresh install be sure that your datas are backed up and that you have separate home partition.

if you don´t have it 

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

You can upgrade via net,but in that case use AptonCD before you start.

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

That way you will save all packages you downloaded with synaptic or apt-get in case that something with upgrades goes wrong.

---

### Post by Seisen on 2007-10-03
Here are the directions to upgrade from the alternate CD.

[http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807]("http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807")

---

### Post by Black Mage on 2007-10-03
Its on the PS3 and I currently want to upgrade Fiesty Fawn 7.04 to an updated version or maybe even gutsy. Because its a PS3, its uses the version for a standard Personal Computer, so should use an upgrade with one of those versions and not the intel?

---

