---
title: "&quot;arp who-has&quot; and Comcast"
date: 2006-07-25
forum: General Help
---

### Post by Mau on 2006-07-25
I am trying to setup a Ubuntu install for a friend, and so far all is going well, but when I try to setup his high-speed cable connection, I am unable to do it.  

His cable modem is connected through Ethernet to his computer.  I have managed to get connectivity at random times (after playing with the config) to get it work for one reboot, but once we restart, it dies again.  ](*,)

I decided to do it a $ sudo tcpdump -i eth0; to see what was going on, and the screen constantly scrolls something like this: arp who-has [random ip here] tell [random ip here].  When we are connected and able to load a website, this does not happen.

We are using a dynamic IP address, and I configured the interface to use DHCP, but it's not working.  The interface is configured and activated.

What is going on?  How do I correct this?

---

### Post by Mau on 2006-07-26
Does anyone even know what "arp who-has" means? I think it may be some type of lease, but I don't know.

---

### Post by bionnaki on 2006-07-26
have you put in the correct dns servers and search domains?

---

### Post by Mau on 2006-07-26
I never entered those myself, but they were automatically filled in after connecting for the first time.

I am tentative, though, because the search domain is something like: xxxx.comcast.net[SIZE="7"]**.**[/SIZE] <--- with the trailing period.  Is that normal?  If I remove it, it goes right back.

Thanks for your reply!

---

### Post by bionnaki on 2006-07-26
yeah, the period is normal

---

### Post by Mau on 2006-07-26
When I called Comcast to see if it was on their end, the operator told me that they don't support Linux (duh), but he can tell me the what, and I just figure out the how.

So, how do would I go about re-leasing an IP?  Do I just stop and start the interface?  Is there any way I can determine my current IP address without going to whatismyip.com?

---

### Post by bionnaki on 2006-07-26
to do a power-cycle, unplug the modem, router, and turn off computer. wait 60 seconds. plug (in order) in the modem and wait for the lights to stop flickering. then plug in your router (if you have one). then turn on your computer.

to see your IP address, type ifconfig in the terminal

---

