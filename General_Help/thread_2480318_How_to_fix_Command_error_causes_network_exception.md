---
title: "How to fix: Command error causes network exception"
date: 2022-10-25
forum: General Help
---

### Post by jack1966 on 2022-10-25
System migration reference systemback:
[https://github.com/BluewhaleRobot/systemback](https://github.com/BluewhaleRobot/systemback)
Enter the following two lines of command
sudo sh -c 'echo "deb [arch=amd64] [http://mirrors.bwbot.org/stable](http://mirrors.bwbot.org/stable) main" > /etc/apt/sources.list.d/systemback.list'


sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key 50B2C005A67B264F
But the stop command before installing sudo apt-get install systemback (because the desktop is to be installed) is not necessary, so it is not executed


At present, the website is interrupted every nearly three hours (the domain name cannot be resolved), but it is normal for the IP to open the website.
Execute apache2 restart to return to normal.


How to remove the influence of these two lines of instructions?


Thanks for your guidance

---

