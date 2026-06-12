---
title: "Can't access router"
date: 2006-07-11
forum: General Help
---

### Post by Shampyon on 2006-07-11
I have a DLINK DSL 504T router, used by myself and my brother for internet access and LAN.
When I first installed Ubuntu, I could access the router from Firefox without difficulty, just as I had in XP.

Now, I can't access it at all. There is no problem accessing the router from my brother's XP machine, just on mine.

This may be related to the fact that I am no longer able to browse my brother's files. I open PLACES/NETWORK SERVES/WINDOWS NETWORK and where once was his shared files and foldered is now emptiness. ***Edit:** I just checked again. I can see his and my shared files. I have no idea why or how this happened, because I don't recall changing anything since I last checked.*

I have Firestarter installed, as well as Aegis Virus Scanner and ClamAV (I don't know if those last two are relevant).

I'd also like to know how I can open up/enable ports so I can properly use bittorrent. In XP, I just had to open my firewall app and add a rule that linked to the program and has the port range (eg: uTorrent/TCP/Out/6881-6689, or Azureus/BOTH/In/40997). I have no idea what the equivalent actions would be in Linux.

---

### Post by Shampyon on 2006-07-11
It's acting up again. I used the method detailed in [this thread]("http://www.ubuntuforums.org/showthread.php?t=202605") to try to set up file sharing with my brother's XP computer.
As stated in [this thread]("http://www.ubuntuforums.org/showthread.php?t=210148"), my ability to see the contents of PLACES/NETWORK SERVERS/WINDOWS NETWORK has disappeared.

---

### Post by gwpritch on 2006-07-11
Try powering of the router, wait 10-20 seconds then power up again. Then reboot your system. This has solved a similar problem for me in the past.

---

### Post by Shampyon on 2006-07-12
I tried the reboot. Still the same problem. I checked using Firefox and Opera. There was no difference
I was able to access it by loading XP in VMWare, though.

---

### Post by gwpritch on 2006-07-13
What happens when you ping the router?

```
ping xxx.xxx.xxx.xxx 
```

Maybe try disabling firestarter and see if that has any effect.

---

### Post by Shampyon on 2006-07-13
Pinged the router. No problems.

I haven't had Firestarter on for a while. I double checked to make sure.

---

### Post by gwpritch on 2006-07-13
Am I getting this right? You can actually access the router, just not the other XP box on the local net. Are you accessing the internet via the router?

---

### Post by Shampyon on 2006-07-13
The router is working fine for accessing the internet.
You know how you can enter the IP of your router into your browser to access it's controls, to open ports and such? That's where I'm having trouble.

We can access it from my brother's XP computer, and from my copy of XP that I run through VMware.
I can ping the router from Ubuntu, but when I type the IP into a browser (I tried Firefox and Opera) I get an error saying that "Firefox/Opera can't establish a connectin to the server XX.XX.XX.XX".

It's really odd. Everything else works fine. The Ubuntu/XP network is working fine both ways, I can access the internet, but I can't get to those ruddy controls! Weird, huh?

---

