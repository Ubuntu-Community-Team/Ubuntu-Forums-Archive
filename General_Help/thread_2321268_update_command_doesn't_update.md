---
title: "update command doesn't update"
date: 2016-04-21
forum: General Help
---

### Post by Rodrigo_Gonalves on 2016-04-21
hi, I just installed ubuntu 16.04 and when I tried to use the command apt-get update all it did was this and non of the ppas updated

```

Hit:1 http://mirror.globo.com/ubuntu/archive xenial InRelease
Hit:2 http://mirror.globo.com/ubuntu/archive xenial-updates InRelease          
Hit:3 http://mirror.globo.com/ubuntu/archive xenial-backports InRelease        
Hit:4 http://mirror.globo.com/ubuntu/archive xenial-security InRelease         
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:6 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease
Hit:7 http://ppa.launchpad.net/noobslab/icons/ubuntu xenial InRelease
Hit:8 http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease
Reading package lists... Done

```

does any one know how to fix this?

---

### Post by dFlyer on 2016-04-21
Not sure if this will help but trying running this, but know you may not need any upgrades. See below for your ppa's.:

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

Some of your ppa's listed may not have upgraded there security and are being avoided until they upgrade. At least I read that somewhere in the past few weeks testing 16.04.

---

### Post by Rodrigo_Gonalves on 2016-04-21
no results, just shows as everything is up to date

---

### Post by RobGoss on 2016-04-21
If this is a new installation then I suggest you do another fresh installation it will save you a lot of wasted time and should fix what ever may have went wrong with the first installation.

---

### Post by Rodrigo_Gonalves on 2016-04-21
apparently my problem was a single repo that is not supporting 16.04 yet, the others repos are updating even does not appearing in the terminal

---

### Post by RobGoss on 2016-04-22
Were you able to correct the problem?

---

### Post by tom-bellas3rd on 2016-04-22
I just did a fresh 16.04 install yesterday, have not recieved any updates since. I just assumed it was up-to-date.

---

### Post by Rodrigo_Gonalves on 2016-04-22
> **RobGoss said:**
> Were you able to correct the problem?

was just a single repository not ready for 16.04 so I installed .deb versions. 
the update command still looks the same but is updating so I'm not sure if is a problem or not '-'

---

