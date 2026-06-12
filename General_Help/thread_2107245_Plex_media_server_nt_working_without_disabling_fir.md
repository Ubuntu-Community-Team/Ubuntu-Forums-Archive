---
title: "Plex media server nt working without disabling firewall"
date: 2013-01-21
forum: General Help
---

### Post by manish_m on 2013-01-21
I have setup plexmedia server on ubuntu 12.04.
When i try to connect from tv, it is not able to connect until i disable firewall. i tried enabling all the ports that plexmedia server uses, but it is not working.
Is there any command, which tells which devices are connected to the ubuntu setup & which port.

---

### Post by steeldriver on 2013-01-21
You could try

```
sudo netstat -ntp | grep 'ip.of.remote.device'
```FYI, if it's tricky to figure out what specific ports to open, you could consider using iptables directly to allow all connections from a specific MAC address - I just did this for my OTA tuner box

---

### Post by manish_m on 2013-01-24
I tried the following:
sudo iptables -A INPUT -i wlan0 -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT

It did not work.
I also tried..
sudo iptables -A INPUT -s XXX.XXX.X.X -j ACCEPT
sudo iptables -A OUTPUT -d XXX.XXX.X.X -j ACCEPT
It also did not work.
what am i missing here.

---

### Post by steeldriver on 2013-01-27
Sorry for the late reply - did you make the iptables rule persistent? else it will disappear on reboot I think

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Installing the iptables-persistent package seems to be the pain free way if you are using network-manager

---

### Post by manish_m on 2013-01-27
Hi Steeldriver,
Thanks. I figured out the issue.
If i add the following rules, it works.

sudo iptables -I INPUT 1 -p tcp -s XXX.XXX.X.X -j ACCEPT
sudo iptables -I INPUT 2 -p udp -s XXX.XXX.X.X -j ACCEPT
sudo iptables -I OUTPUT 1 -p tcp -d XXX.XXX.X.X -j ACCEPT
sudo iptables -I OUTPUT 2 -p udp -d XXX.XXX.X.X -j ACCEPT

Also, for persistence, i added the rules to user_post script of firestarter. They are working when my system boots.

---

### Post by steeldriver on 2013-01-29
Ah yes it's probably more complicated if you are running firestarter

FWIW I've now abandoned the persistent iptables rule - I think it was working but the ufw logs got all messed up

I've now purged iptables-perisitent and added a custom mac-source rule to my ufw before.rules file:

```
$ sudo diff /etc/ufw/before.rules.bak /etc/ufw/before.rules
41a42,44
> # allow all from HDHOMERUN OTA TV capture device - by MAC
> -A ufw-before-input -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT
>

```I think *that's* the right way to do it when running ufw

---

### Post by Mike Brennan on 2013-04-19
I've had a hell of a time trying to find any reliable documentation on what ports to open up in my firewall so Plex Media Server is accessible on my home network. It's amazing to me that the Plex folks don't clearly document this.

However, I just found this: [http://forums.plexapp.com/index.php/topic/33751-problems-with-pms-and-ufw-on-ubuntu/?p=215319](http://forums.plexapp.com/index.php/topic/33751-problems-with-pms-and-ufw-on-ubuntu/?p=215319)

Opening the ports mentioned in that worked for me.

For the sake of completeness, here are my ufw rules (minus those not applicable to Plex Media Server):

```

To        Action From
--        ------ ----
32400     ALLOW  192.168.1.0/24
5353/udp  ALLOW  192.168.1.0/24
1900/udp  ALLOW  192.168.1.0/24
32469     ALLOW  192.168.1.0/24
32410/udp ALLOW  192.168.1.0/24
32412/udp ALLOW  192.168.1.0/24
32414/udp ALLOW  192.168.1.0/24

```

Some of these may be redundant (based on the info in the link), but now that it is finally working for me, I'm inclined not to mess with it any further.

---

