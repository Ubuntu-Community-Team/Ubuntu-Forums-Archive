---
title: "From Ubuntu 13.10 to 13.04"
date: 2013-10-27
forum: General Help
---

### Post by Bharath Kumar V on 2013-10-27
Dear All,


_**Requirement**_: Please let me know the command in terminal window which will drop all the packages of ubuntu 13.10 and get back to Ubuntu 13.04


_**Background:**_ I have been using UBUNTU 13.04, When I did the upgrade to 13.10 through 'Update manager' it could not complete successfully because,there was not enough power backup problem. The system logged off automatically.


Then with enough back power, I re-tried the upgrade through 'Update Manager', which was not working. I rebooted the system and I tried upgrade through terminal 'sudo apt-get-upgrade' it got completed with errors.


After booting, I tried to update with 'Update Manager', there was an error message stating that the earlier try of upgrade failed because of errors and asked to try for partial upgrade, even after choosing it, the attempt was not successful.


So, Please let me know the command in terminal window which will drop all the packages of ubuntu 13.10 and get back to Ubuntu 13.04

Thanks and regards

---

### Post by ajgreeny on 2013-10-27
Sorry but there is no way to downgrade back to the previous version after a failed upgrade from version to version.

I'm afraid you have no real choice apart from trying to get the part upgrade to 13.10 to work, or you will have to start from scratch and re-install 13.04.

---

### Post by Baldrick_NZ on 2013-10-27
The only other thing I could offer, before a fresh install, would be to try to complete the download and get the dependencies you missed for 13.10
```
sudo apt-get -f install
```
and then, to be completely sure
```
sudo apt-get update; sudo apt-get dist-upgrade
```
Failing that, I'd re-install from DVD/USB. It doesn't usually take too much time.

Unfortunately, upgrading is usually frought with issues. Best to do a complete, fresh install. Partition your drive so that your Home drive is separate to the rest, so that when situations like this arise again you only have to re-install your system files. As always, remember to back-up regularly.

Hope that helps...

---

### Post by Bharath Kumar V on 2013-10-28
[SIZE=2]Hi  ajgreeny and Baldrick_NZ. Thanks for your replies. It was very useful. I did a complete re-installation of Ubuntu 12.04 LTS and reinstated the backup files. Thanks again[/SIZE]

---

### Post by mastablasta on 2013-10-28
the update/upgrade manager notifies you to plug the laptop into reliable power source before doing updates and upgrade. while i do updates anyway if i am next to screen and have over 50% battery power. i owuld  never attempt an upgrade without power source.

---

