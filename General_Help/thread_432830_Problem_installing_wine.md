---
title: "Problem installing wine"
date: 2007-05-04
forum: General Help
---

### Post by LuckN1ne on 2007-05-04
ok im falling this guide [[http://ubuntuforums.org/showthread.php?t=149585&highlight=wine]](http://ubuntuforums.org/showthread.php?t=149585&highlight=wine]) and when i to sudo apt-get install libgtk1.2  this problem occurs


> james@james-desktop:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgtk1.2: Depends: libgtk1.2-common (>= 1.2.10-18) but it is not going to be installed
             Depends: libglib1.2 (>= 1.2.0) but it is not going to be installed
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-11-1ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
james@james-desktop:~$ apt-get -f installE: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
james@james-desktop:~$ 


---

### Post by angryfirelord on 2007-05-04
In your second command, you left you sudo. Therefore, run it again, but this time use **sudo apt-get -f install**.

However, I'd recommend adding the wine repo to your sources.list.
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

It's easy with just 2 simple commands. First do:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
Then, pick one of the following:

For Ubuntu Feisty (7.04):
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```
For Ubuntu Edgy (6.10):
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list
```
For Ubuntu Dapper (6.06):
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list -O /etc/apt/sources.list.d/winehq.list
```

Now run a **sudo apt-get update** along with **sudo apt-get install wine**.

---

### Post by LuckN1ne on 2007-05-04
omg THANKS !!!!! it works i greatly appreciate it :)

---

