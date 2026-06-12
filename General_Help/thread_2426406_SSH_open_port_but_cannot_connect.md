---
title: "SSH open port but cannot connect"
date: 2019-09-08
forum: General Help
---

### Post by montfox on 2019-09-08
Hello! I am trying to connect to my desktop via ssh from a different network. Accord to canyouseeme.org, it says "[COLOR=green][FONT=sans-serif]Success:[/FONT][/COLOR][COLOR=#777777][FONT=sans-serif] I can see your service on xxxx on port 22!" [/FONT][/COLOR]However, I am still not able to connect... 

After running ```
sudo ufw status
``` ```
[Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere                  
22/tcp                     ALLOW       Anywhere                  
OpenSSH                    ALLOW       Anywhere                  
22 (v6)                    ALLOW       Anywhere (v6)             
22/tcp (v6)                ALLOW       Anywhere (v6)             
OpenSSH (v6)               ALLOW       Anywhere (v6) 
```

no problem on my firewall, I tried running ```
sudo apt purge openssh-server && sudo apt install openssh-server
``` to no avail. 

Finally I ran ```
tcpdump -i enp3s0 port 22 -n -Q inout
``` and all I got was [this]("https://pastebin.com/yFQL6gHJ"). my ssh_config file is still the default [here]("https://pastebin.com/RTh11fEy").

What am I missing here?

---

### Post by montfox on 2019-09-08
SOLVED: apparently my android device could not SSH while on cell service

---

### Post by Skaperen on 2019-09-08
do you get internet when on cell service?

---

### Post by montfox on 2019-09-09
I do get internet, and to add to that my linux emulator is able to update ppa repositories but not ssh while on cell cervice... However, I connected to my work's wifi network and it worked just like that.

---

