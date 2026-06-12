---
title: "X Server not starting"
date: 2006-11-07
forum: General Help
---

### Post by heattech on 2006-11-07
I had Ubuntu 6.06.1 up and running fine. I thought it would be nice to have some server programs running so I used the site [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) as a tutorial to set-up my server. Everything was running fine before my reboot. When I rebooted the Ubuntu boot-up screen came up as usual and started displaying the services it was starting. It got all the way to "checking all file systems." It displayed that that step was ok and then that is where the startup hung for about 30 sec.

It then went to a black screen with text that said that it was "checking quotas" (I installed quota during installation of server programs if that matters any) It then displayed the following "I/O error on device hdc1 (hdc1 is where Ubuntu is installed) logical black 648812112114. It then went through about 15 scrolling lines of the same text just different numbers. It then said "quota check- something weird happened while checking quotas" it then said "rm cannot remove /var/lib/quota/off".

I edited my /etc/fstab during my quota installation and I think that is where my error may be. I can get into my command line interface so I do have some control over the machine. I tried to change /etc/fstab back to what the default was but it said I could not modify it even though I used the command "sudo nano /etc/fstab" which let me have root access. If anyone can help please reply back. If you need any more information I will try to go into deeper detail. (if possible) Thanks!

---

