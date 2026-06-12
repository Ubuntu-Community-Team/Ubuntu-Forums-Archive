---
title: "Conky to monitor openvpn ip on network machine"
date: 2016-01-30
forum: General Help
---

### Post by djseal on 2016-01-30
Hi.  I have a RaspberryPi on my network that has OpenVPN set up (and running headless).  I would like to monitor the external IP of this machine with Conky on my main machine.  Is there a way to do this?   If I ssh into my RPi and run ```
curl ipecho.net/plain; echo
``` it gives me the external IP.  But I'd like to display that on my main machine's conky display.

---

### Post by CantankRus on 2016-01-30
Maybe this will set you in the right direction.
[**_[COLOR="#B22222"]can-conky-monitor-other-linux-computers-on-the-network[/COLOR]_**]("http://unix.stackexchange.com/questions/66921/can-conky-monitor-other-linux-computers-on-the-network")

---

