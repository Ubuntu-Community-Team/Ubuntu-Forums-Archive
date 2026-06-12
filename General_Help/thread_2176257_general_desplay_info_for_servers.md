---
title: "general desplay info for servers"
date: 2013-09-23
forum: General Help
---

### Post by killernat on 2013-09-23
I have ubuntu server 12.10 and I was thinking it would be nice to be able to just turn on my servers monitor and see some general info about it (without logging in ). Like a screen saver of sorts that would display various info like  lm-sensor output, ram usage, hdd usage, printer status,  network activity, cpu usage, etc. I guess similarly to the system info when you login but actively displays the info when no user is logged in

i guess what im asking is does a software like this exist for servers (without having to install X-server)


i.e.

> 
System information as of Mon Sep 23 12:33:49 EDT 2013

  System load:  0.14                Processes:           168
  Usage of /:   43.5% of 228.26GB   Users logged in:     0
  Memory usage: 50%                 IP address for p5p1: xxx.xxx.xxx.xxx
  Swap usage:   0%                  IP address for eth2: xxx.xxx.xxx.xxx


---

### Post by zitch on 2013-09-23
What is currently displayed with the text-based login prompt is the contents of the text file at /etc/issue. 

For example, on my Kubuntu 13.04 setup, the contents of this file is as follows:

```
Ubuntu 13.04 \n \l


```

Looks like "\n" refers to the hostname of the machine and "\l" refers to the name of the terminal (I.E.: tty1)

Maybe you can look into having something update this file every minute or so, though there is no guarantee what you see on screen is the most recent stats (Your example if including the timestamp would help with identifying this).

If Ubuntu is using agetty, the [man page for agetty](http://linux.die.net/man/8/agetty) includes escape codes available under the section **Issue Escapes**.

---

### Post by killernat on 2013-09-23
seems like an interesting avenue to explore but not realy what im hoping to do

---

### Post by dcstar on 2013-09-26
> **killernat said:**
> I have ubuntu server 12.10 and I was thinking it would be nice to be able to just turn on my servers monitor and see some general info about it (without logging in ). Like a screen saver of sorts that would display various info like  lm-sensor output, ram usage, hdd usage, printer status,  network activity, cpu usage, etc. I guess similarly to the system info when you login but actively displays the info when no user is logged in

i guess what im asking is does a software like this exist for servers (without having to install X-server)
...........

"Software" does exist, you simply write your own script to output the data to the console tty port and refresh every few seconds. Every single tool to do this is in the base Linux install.

---

### Post by killernat on 2013-09-26
i was hoping for an exciting solution as i don't have  any free time to play with scripting

---

