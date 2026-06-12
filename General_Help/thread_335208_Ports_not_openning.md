---
title: "Ports not openning"
date: 2007-01-10
forum: General Help
---

### Post by jasonpeinko on 2007-01-10
im trying to open a port for utorrent. but when i run the checker it says it is not open.

I run ifconfig to get my ip and i open the port on my router for my ip. 

it still does not work. Would ubuntu be doing something to stop it?

---

### Post by kidders on 2007-01-10
Hi there,

Opening ports is usually not enough for bittorrent apps, since you're technically running a server (ie you need to be able to accept incoming connections) when you use one.

[LIST]
[*]Make sure you enable port forwarding from your router to your Linux box.
[*]Make sure Ubuntu isn't blocking incoming connections with a firewall.
[*]Make sure your bittorrent client is configured to use the ports you're forwarding.
[/LIST]

Hopefully one of those is your problem. :-)

---

### Post by jasonpeinko on 2007-01-10
how do i open the port on ubutnu?

---

### Post by kebes on 2007-01-10
If you've done a default install, Ubuntu shouldn't be blocking a port for a running program. However if you've installed some security package, it might be blocking. You can install a program called "firestarter" which lets you easily configure the Linux firewall using a GUI. Be aware that once installed it automatically creates a "deny all incoming connections" rule, but you can easily go into the program and add which ports you want to open.


However most of the time the problem is on the router end. Remember that you have to not just open a port on your router, but forward it to the IP of your computer. (You mentioned that you used ifconfig, so I'm assuming you've done this right... but I'm just confirming!)

Lastly, it's also possible that your internet provider is blocking the port. You could try using different port ranges and see if that helps. (Of course you'll have to update your bittorrent program, plus the router and Linux firewall perhaps.)

---

### Post by jasonpeinko on 2007-01-10
When i forward the port on the router it has a section for IP adress and i just put in the one for my linux comp. Is there something more i should be doing?

---

### Post by jasonpeinko on 2007-01-10
well i have tried atleased 30 different ports atempting to open each on the router. Still utorrent says it is blocked.

---

### Post by kidders on 2007-01-11
Hi there,

If you're not running a firewall on your Linux box, the IP you're forwarding to is correct, and your bittorrent app is properly configured, then I think there are two possibilities:

[LIST]
[*]You have a strange router that lets you forward a port and still block incoming connections on it with its firewall. Try temporarily disabling your router's firewall ... assuming it's got one.
[*]Your ISP is blocking the connection. You could call them and ask about their network traffic policy.
[/LIST]

One thing you could try is running a service you're more familiar with (maybe a web server) on, say, port 6789. Forward that port to your Linux box and have a friend try to access the service. If he fails, have him port scan you. The state of the port might be useful in helping you out. If he succeeds, you should have no trouble with bittorrent on that port.

---

### Post by Choad on 2007-01-11
[http://www.ubuntuforums.org/showthread.php?t=331161](http://www.ubuntuforums.org/showthread.php?t=331161)

---

### Post by jasonpeinko on 2007-01-11
wow i did what you said and it is still not working

---

