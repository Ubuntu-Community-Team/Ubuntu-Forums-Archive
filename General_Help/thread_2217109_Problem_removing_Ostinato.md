---
title: "Problem removing Ostinato"
date: 2014-04-15
forum: General Help
---

### Post by M1ck4el on 2014-04-15
Hi all,
Ostinato is a software to creat and send packets...
But I have this error when I want to 
sudo apt-get update 
my system
I tried to remove folders in my directory but they are created again when I update again.


W: Duplicate sources.list entry [http://download.opensuse.org/repositories/home:/pstavirs:/ostinato/xUbuntu_12.04/](http://download.opensuse.org/repositories/home:/pstavirs:/ostinato/xUbuntu_12.04/)  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_home:_pstavirs:_ostinato_xUbuntu%5f12.04_Packages)
W: Vous pouvez lancer « apt-get update » pour corriger ces problèmes.

Please help me

---

### Post by M1ck4el on 2014-04-15
bump 

please please please u r my last hope

---

### Post by slickymaster on 2014-04-15
There is a reported bug in Launchpad, [bug #1281671]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1281671"), that shows the exact some symptoms as yours. Please do note that said bug is a duplicate of [bug # 1278330]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1278330").

---

### Post by M1ck4el on 2014-04-15
Thx

I found the error but I can't remove it
I typed sudo apt-get purge drone
but there is still a problem :

shining@Mika:/usr$ dpkg -l drone
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom            Version        Description
+++-==============-==============-============================================
un  drone          <aucun>        (aucune description n'est disponible)

---

### Post by M1ck4el on 2014-04-15
Do you know how i can properly remove totally drone & ostinato of my computer?

I don't remember exactly how I installed those software... :s

---

### Post by slickymaster on 2014-04-15
> **M1ck4el said:**
> Do you know how i can properly remove totally drone & ostinato of my computer?

I don't remember exactly how I installed those software... :s

Well, according to [Ostinato homepage]("https://code.google.com/p/ostinato/"), > Ostinato is an open-source, cross-platform network packet crafter/traffic generator and analyzer with a friendly GUI. Craft and send packets of several streams with different protocols at different rates. For the full feature list see below.
Ostinato aims to be "Wireshark in Reverse" and become complementary to Wireshark.So my advice to you is to be careful dealing with these types of software, particularly when you don't quite grasp the full extend of the potential for Wireshark exploits. Special care should be taken to avoid security related problems while running Wireshark or at least to reduce the possible impact.

That said, in order to uninstall Ostinato, its dependencies and purging its config/data too, I would run the following in a terminal window```
sudo apt-get purge --auto-remove ostinato
```

As for drone, I must confess that I don't have the slightest idea of what it is.

---

