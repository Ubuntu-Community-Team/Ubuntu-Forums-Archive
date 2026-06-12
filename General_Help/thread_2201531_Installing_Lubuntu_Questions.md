---
title: "Installing Lubuntu Questions"
date: 2014-01-24
forum: General Help
---

### Post by walterdowis on 2014-01-24
Hi All, 
    I'm a newbie to Linux and Ubuntu.  I recently was given a 10+ year old laptop.  Well, it's free so I accepted it.  I currently have 32bit Ubuntu installed.  Ubuntu is working well on this old machine, but it's a bit slow.  So I'm thinking of installing the lighter Lubuntu.  Lubuntu tested well with LiveUSB.    
 
    I have two questions:
 
    1. Can I install all, or most of the packages in Lubuntu that exist for Ubuntu.  Also, if I follow the Ubuntu instructions to install something, will the instructions also work on Lubuntu?
    2. Is there a way I can backup my current Ubuntu and it's configurations and install programs in case I decide to re-install Ubuntu and not lose what I currently have.  How would I do the backup and restore process?

---

### Post by ajgreeny on 2014-01-24
No real need to reinstall.

Install lubuntu-desktop package and you will have lubuntu which you can choose at the login screen.

If you really want to you can remove all of the old DE with the command found at [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu) though this is for older versions than the current, so proceed with caution if you want to remove the ubontu-desktop system from your new lubuntu.

---

### Post by walterdowis on 2014-01-24
That's great.  Thank you.

---

### Post by RadicaX on 2014-01-24
To your first question, most commands you do and the way you install stuff will be the same. Like to turn on your firewall.```
sudo ufw enable
```

```
sudo ufw default deny
```

Easy peasy. So for installing the things you want, it will be the same too. "apt-get, synaptic, software center." 

As far as what was recommended by the first reply, that is an easy way to keep your stuff without having to do a reinstall, but it can take a bit of data up and give you doubles of certain things. Remember, UbuntuOne is a great way to back up stuff also, incase you ever did want to do a fresh install.

---

### Post by Elfy on 2014-01-25
*Thread moved to **General Help**.*

---

### Post by sudodus on 2014-01-25
> **walterdowis said:**
> 
    1. Can I install all, or most of the packages in Lubuntu that exist for Ubuntu.  Also, if I follow the Ubuntu instructions to install something, will the instructions also work on Lubuntu?

As you already know by now, yes, yes, in most cases :-)
> 
2. Is there a way I can backup my current Ubuntu and it's configurations and install programs in case I decide to re-install Ubuntu and not lose what I currently have.  How would I do the backup and restore process?

Yes, there are many ways to backup linux systems and data in linux systems. Sooner or later you need to restore from backup when something breaks so ***backup at least your personal data*** even if you do not intend to wipe your system and re-install.

1. ***Ordinary backup*** of typical personal data and settings for example with ***Simple Backup***
2. ***Cloning or imaging*** of the complete system for example with ***Clonezilla***
3. ***Synchronizing*** two directory trees for example with ***Unison***

---

