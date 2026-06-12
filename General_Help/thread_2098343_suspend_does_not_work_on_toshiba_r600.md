---
title: "suspend does not work on toshiba r600"
date: 2012-12-26
forum: General Help
---

### Post by pumbaa247 on 2012-12-26
Hi,

neither suspend to ram nor suspend to disk works on a toshiba r600. the result of suspending is a black screen with fan running faster. only hard reset helps. 

have searched for weeks for a solution, but cannot find one. 

Using Ubuntu 12.10

---

### Post by sifterr on 2012-12-28
Hi pumbaa247,

 I  have a Toshiba Satelite and experienced  problems when installing Ubuntu 12.10 on it. This included the monitor never turning on  when resuming suspend, suspend resuming immediately for no reason,  and frequently only a  purple blank screen when rebooting.
I read many posts on the issue and found one simple solution which fixed all the above problems.

 Eduard's Post here [http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen](http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen)   pointed out that amd video cards cause many of these problems. Anyway's the solution was to install the AMD package from the Ubuntu repository.

Then do the following commands once you're dropped to the root shell:
  sudo apt-get update 
sudo apt-get upgrade 
   sudo apt-get install fglrx     
sudo aticonfig --initial
sudo reboot 

Hope this fixes your problem.

sifterr

---

