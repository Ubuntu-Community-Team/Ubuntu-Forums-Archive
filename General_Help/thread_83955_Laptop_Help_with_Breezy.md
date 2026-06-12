---
title: "Laptop Help with Breezy"
date: 2005-10-30
forum: General Help
---

### Post by richlaabs on 2005-10-30
Hey folks,

I have a Toshiba M45-S351 laptop that I have installed Kubuntu 5.10 on and everything works...except internet. Neither my wireless nor my wired connections will work. I manually configure and try to ping 192.168.1.6 and it makes one unsuccessful ping and then it goes back to 192.168.1.1

Anyone with some successful ideas...please help!!

Thanks a million. I ran this on VM Ware and everything worked well. I want to use this in real tiime and not with VM if possible.

---

### Post by adwait on 2005-10-30
What kind of connection are you using on the wired line? A plain LAN or an ADSL router/Cable Modem etc?

---

### Post by richlaabs on 2005-10-30
I use a cable internet connection with wireless router that has ports on the back that I have connected to a gigabit switch. All of my windows boxes, my mac mini and my Kubuntu box. This is the only machine I have that is having this issue. I am dual booting Kubuntu 5.10 with Windows XP Pro on this laptop.

Thanks in advance!!

---

### Post by shinygerbil on 2005-10-31
For the wireless, I found that this solved my problem:

```
sudo iwconfig {interface} essid {name of network}
sudo iwconfig {interface} key {WEP key, if you have one; if not, remove this line
sudo dhclient {interface} 
```

where {interface} is the name of your wireless interface, in my case eth0, and {name of network} is pretty self-explanatory.

I found that the Wireless config stuff in System Settings didn't work..

Hope this helps

Steve

---

### Post by kaptainlange on 2005-10-31
[QUOTE=shinygerbil]
I found that the Wireless config stuff in System Settings didn't work..
[/QUOTE]

I also find this to be true.  Upon closer inspection it appears that the WEP key is stored as a series of asterisks (attempt to disguise the key?) in the /etc/network/interfaces file.  Can anyone else confirm this?

---

### Post by shinygerbil on 2005-10-31
Heh, if I could get it to save any config stuff to the /etc/network/interfaces file, I'd tell you. I just use a startup script, which is annoying and fiddly but it works!

Steve

---

