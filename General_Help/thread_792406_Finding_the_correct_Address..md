---
title: "Finding the correct Address."
date: 2008-05-12
forum: General Help
---

### Post by ErusGuleilmus on 2008-05-12
Hello, I am having an issue with Desktop Sharing. The issue is, that I do not know what my computers IP address is. I went to [www.whatismyip.com](www.whatismyip.com) to find it, but it turns out that IP is for my DSL modem, but not my computer. I tried the link provided by Ubuntu, but that did not work either. How do I find out what address I need to send my freind so that he can connect to my computer?

Thanks.

---

### Post by Mr A Mouse on 2008-05-12
Desktop sharing needs some extra set-up steps if you're on a network behind a cable or DSL modem, and that depends on how your home network is set up. For some people, the best answer is to set up an ftp server and do port forwarding.

If you could tell us more about your home network setup, I'm sure someone will be able to provide help.

---

### Post by ErusGuleilmus on 2008-05-12
Ok, this is how my home network is configured: DSL Modem --> 4 Port Swwitcher --> Wireless Router --> (Via Ethernet) PC.

---

### Post by Mr A Mouse on 2008-05-12
> **ErusGuleilmus said:**
> Ok, this is how my home network is configured: DSL Modem --> 4 Port Swwitcher --> Wireless Router --> (Via Ethernet) PC.

I'm assuming your via ethernet connection comes from the 4-port switch, rather than the wireless router. If that assumption is wrong, this may not help.

In this case, the IP address you got from whatismyip is your *external* address. The IP address you get from Network Configuration is your *internal* address.

1: Set up port forwarding on your 4-port so that 5900 is forwarded to your machine's *internal* IP address. (You'll also have to make sure any firewalls you have installed will allow traffic on that port.)
2: Set up Remote Desktop so that it will accept outside connections--for safety's sake, you should definitely have a password on the connection.
3: Email your friend the *external* IP address and password. They should be able to vnc into your machine.

If it doesn't work like that, it may not work at all--I can't remember if vnc is restricted to local addresses only, or if it can work across the internet. And someone else may come up with a better idea or an easier way, so if my setup doesn't work, keep watching this thread.

---

### Post by ErusGuleilmus on 2008-05-12
> **Mr A Mouse said:**
> I'm assuming your via ethernet connection comes from the 4-port switch, rather than the wireless router. If that assumption is wrong, this may not help.

That assumption is incorrect, sorry for being so vague. It goes: DSL Modem (Ethernet to) 4 Port Switcher (Ethernet to) Wireless Router (Ethernet to) PC. As far as I am aware, I cannot access the settings of the four port switcher. I know that I can access the wireless via browser by typing "192.168.1.1", and the Modem via "192.168.0.1", but I do not think that the four port has such capabilities.

Edit: Will this work if I tell the Wireless Router to forward port 5900 to my PC's internal IP?

---

### Post by Mr A Mouse on 2008-05-12
> **ErusGuleilmus said:**
> Edit: Will this work if I tell the Wireless Router to forward port 5900 to my PC's internal IP?

No need to apologize for the confusion--that was on my part for not reading your middle post accurately.

The best answer I can give is "Maybe, try it and see." If it works, great--let us know. If it doesn't, like I said, keep watching this thread. 

Oh, and if it dies work, make sure you disable Remote Desktop and port forwarding for port 5900 as soon as your friend is done. This kind of a setup is terribly insecure, but will be fine for a brief connection.

---

### Post by ErusGuleilmus on 2008-05-13
Got it!! I did a overhaul of my network so that my PC is directly connected to the modem, then set it to forward port 5900 to my internal address. Works perfectly. Thank You!!

---

### Post by Mr A Mouse on 2008-05-13
Sweet! (Makes notes for future work on my network.)

---

