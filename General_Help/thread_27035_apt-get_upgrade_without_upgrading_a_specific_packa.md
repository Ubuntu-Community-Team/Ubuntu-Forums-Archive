---
title: "apt-get upgrade without upgrading a specific package"
date: 2005-04-14
forum: General Help
---

### Post by carlc on 2005-04-14
Is there a way to run apt-get upgrade without upgrading a specific package? This seems simple enough but I have googled this and did not find a straightfowad answer.

---

### Post by Leif on 2005-04-14
I'm sure it's command line doable, but doing it in synaptic is quite easy, just mark all upgrades and unmark what you don't want.

---

### Post by speedman on 2005-04-14
dpkg --get-selections > pkgs

vi pkgs

Search for the package you don't want upgraded automatically and change the notation beside it's name from install to hold.

Then ...

sudo dpkg --set-selections < pkgs

In the future if you want to install a newer version of the package you can repeat the steps above and change the status to hold, or you can simply do an apt-get install <pkg_name>.


Regards,

SM

---

