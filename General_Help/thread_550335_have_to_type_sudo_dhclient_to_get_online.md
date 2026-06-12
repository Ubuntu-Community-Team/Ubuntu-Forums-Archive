---
title: "have to type sudo dhclient to get online"
date: 2007-09-13
forum: General Help
---

### Post by JESSU on 2007-09-13
Why do I have to type sudo dhclient in the terminal to get online? How do I make it so I don't have to?

---

### Post by mpgarate on 2007-09-13
im not sure... but you could add it to your sessions? (startup)

go to system > preferences > sessions

click add

name it what you  want, and type sudo dhclient in the command box

---

### Post by ntetreau on 2007-09-13
Well, somehow i don't that adding it to the session will work.  You might be able to find a solution in the following thread:

[http://ubuntuforums.org/showthread.php?t=542211](http://ubuntuforums.org/showthread.php?t=542211)

In a nutshell, go into System > Admin > Network, then  go in the properties of your network interface (you fail to say if this is cable of wifi), and then enable roaming mode.  Try again.

---

### Post by JESSU on 2007-09-13
I added it to my sessions. I will restart and see what happens.
Edit: That did not work.
Edit 2: enabling roaming didn't work either.
Its cable

When I go to system/ network tools the network device is loopback but I have an ethernet connection to a router that connects to a cable modem and comcast is my ISP.

I'm using Feisty Fawn 7.04

---

### Post by ntetreau on 2007-09-13
Can you post the content of the /etc/network/interfaces file?  Also, do you know what network card you have by any chance?  Is NetworkManager running is the panel tray (upper right)?  If so, what do you see when you right click or left click on it.  If it isn't running, start it from a terminal with:

```
sudo NetworkManager --no-daemon
```

By the way, which ubuntu flavor are you running?

---

### Post by JESSU on 2007-09-14
The what file? I don't know what network card I have. I dont see NetworkManager but I see  manual network configuration in the upper right. 

When I type in sudo NetworkManager --no-daemon I get sudo: networkmanager: command not found

---

### Post by ntetreau on 2007-09-18
The reason you see only the manual network configuration on the upper right is because your network card(s) are not in roaming mode.  Go back to System > Preferences > Network and check the Roaming mode in the cards preferences.  Check again the icon on the upper right, it should now show up the connections.  Now that I think of it, i' m not even sure if your conenction is wired or wifi, which one is it? 

Nic

---

### Post by JESSU on 2007-09-18
I checked roaming restarted and tried it and it didn't work but it did change my icon now it says network connection when I put the mouse over it. From that I put a dot next to wired network and now the internet seems to be working with out me having to type sudo dhclient.

---

### Post by Fakircho on 2007-09-21
I also have to type in sudo dhclient everytime i boot up into Ubuntu.

WHY ?

---

