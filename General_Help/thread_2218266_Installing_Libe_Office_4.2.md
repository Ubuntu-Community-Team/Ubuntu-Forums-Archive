---
title: "Installing Libe Office 4.2"
date: 2014-04-20
forum: General Help
---

### Post by rbscairns on 2014-04-20
I currently have Libre Office 3.5.7.2 installed on my Ubuntu 12.104 (Gnome Classic) computer. I am now trying to upgrade/install Libre Office 4.2. So far, I have run the following in terminal:
```
sudo apt-get install python-software-properties
sudo apt-add-repository ppa:libreoffice/libreoffice-4-2
sudo apt-get update
```
When I now open Libre Office, it is still 3.5.7.2.

Where do I go from here to get Libre Office 4.2 up and running?

---

### Post by deadflowr on 2014-04-20
Running sudo apt-get update only reloads the package listings and does not install new/updated packages.
To do so, you need to run
```
sudo apt-get dist-upgrade
```

or simply run the update manager and click install for all the new packages it has listed to install.

---

### Post by rbscairns on 2014-04-20
I do not have the most reliable of internet connections where I am. The last time Update Manager was able to check was 74 days ago.

I ran sudo apt-get dist-upgrade and got
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```
Still only getting Libre Office 3.5.7.2.

---

