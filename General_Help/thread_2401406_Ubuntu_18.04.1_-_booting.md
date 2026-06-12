---
title: "Ubuntu 18.04.1 - booting"
date: 2018-09-18
forum: General Help
---

### Post by AnupamMitra on 2018-09-18
I had installed Ubuntu 16.04.1 (32 bit) in my daughter's desktop with dual booting option of Windows 7. In the mid-August, system was upgraded to 18.04.1. 

However, since then computer do not start as usual. The first page asking me to choose Ubuntu, Advance Option for Ubuntu Recovery Mode, Windows 7 and System set up.

After choosing Ubuntu, Login page appears, giving the password, booting starts, but stuck in the midway without any further result. 

Then I shut down the computer, restart it and choose "Advance Option for Ubuntu Recovery Mode". Login Page appears, giving password and then only computer start its booting and function normally.

Thereafter I did the following to overcome the problem : 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

But unfortunately no improvement takes place.

Seeking advice of the experts as to how I can resolve the issue.

---

