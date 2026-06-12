---
title: "Loosing WiFi connection after weaking up Ubuntu"
date: 2020-06-03
forum: General Help
---

### Post by dorpapst on 2020-06-03
I am using Ubuntu 20.04 (newly installed two months ago) and very often I experience the following:
I use the PC for daily stuff, including using the Internet. After while, I lock the PC or I leave and it looks itself (the hard disk is also shutting down).

After while, I weak the PC up and the network connection is gone.
The strange thing is that I then cannot connect to any WiFi anymore. If I open the WiFi menu, it cannot find any WiFi networks, even though there are hundreds around.
I cannot solve the problem with something else than completely shutting down and restarting Ubuntu.

Is there any workaround for that?

It seems a bit like it is network dependent, I experienced that within one Wifi, but not within a second one. But the router is okay, other devices don't loose their connection at all.

---

### Post by dorpapst on 2020-06-07
Is there anybody having an answer?

Well, it might a good idea to move that topic into a different section for networking and wireless, sorry for that

---

### Post by #&amp;thj^% on 2020-06-07
Had this problem very early in testing 20.04, and thought it was resolved by now.
My steps back then went as follows:
Commands
1.
```
sudo lshw -class network
```
2. This will show your product number:
Example only:
```
sudo lshw -class network
  *-network                 
       description: Ethernet interface
       **[COLOR="#FF0000"]product: 82579LM[/COLOR]** Gigabit Network Connection (Lewisville)
       vendor: Intel Corporation
```

```
cd /etc/pm/sleep.d
```
3. 
```
sudo touch config
```
4. I added this line:
```

SUSPEND_MODULES= "82579LM"
```
5.
```
echo "options 82579LM fwlps=N" | sudo tee /etc/modprobe.d/82579LM.conf
``` 
6.reboot

---

### Post by dorpapst on 2020-06-08
Hello! Thank very much to you, I tried exactly that manual yesterday evening.
today, two times in a row, the wifi was still there when I came out of suspend, but now, 20min ago, I started again and the same bug happened again.

it might be worth saying that the hardware is a MacBook. Maybe there is something weird which Apple has build in?

---

