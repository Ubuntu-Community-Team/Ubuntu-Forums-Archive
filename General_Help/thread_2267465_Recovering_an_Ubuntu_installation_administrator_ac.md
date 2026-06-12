---
title: "Recovering an Ubuntu installation administrator access"
date: 2015-03-01
forum: General Help
---

### Post by lz1dsb on 2015-03-01
So here's the story. Yesterday I was fooling around with Wireshark and I decided that it is time to stop starting it as a root. So I followed that link:
[http://askubuntu.com/questions/74059/how-do-i-run-wireshark-with-root-privileges](http://askubuntu.com/questions/74059/how-do-i-run-wireshark-with-root-privileges)
and indeed I'm able to run Wireshark now as a normal user. 
I just realized today, that my super user accoung is not working anymore. Here's is an example:

superuser@NUC-desktop:~$ sudo apt-get upgrade
[sudo] password for superuser: 
superuser is not in the sudoers file.  This incident will be reported.

I'm thinkging that the following command from the above link might have changed my account:
sudo adduser $USER wireshark

So the way I see it, my user account is perfectly useable, but I'm not able to run sudo anymore... :mad:

What do you guys think? That's the latest change I did...
I found the following link:
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)
I think it's my only option to recover the system...

---

### Post by lz1dsb on 2015-03-04
I used the following link to recover my system. 
[http://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user](http://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user)

it's strange though that I've got myself into this situation in the first place.

---

