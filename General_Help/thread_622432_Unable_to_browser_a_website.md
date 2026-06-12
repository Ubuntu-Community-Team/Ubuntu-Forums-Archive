---
title: "Unable to browser a website"
date: 2007-11-24
forum: General Help
---

### Post by dakochan on 2007-11-24
Hi,

I have a problem to browse a website ([www.ocbc.com](www.ocbc.com)). I don't understand why. This problem start since I installed Ubuntu. But I can browse the website using other OS (Windows XP and PC Linux 2007).

Is the website blocked by iptables ?

Please help.

David.

---

### Post by oneadvent on 2007-11-24
what part? I can to it from my gutsy.

---

### Post by dakochan on 2007-11-24
Gutsy can access the website ?
I'm using Feisty and I'm unable to retrieve the content of the website, even the main page.

Should I upgrade to Gutsy ?

---

### Post by gali98 on 2007-11-24
almost quite sure this has nothing to do with it. Did you try rebooting?
Kory

---

### Post by dakochan on 2007-11-25
I installed Feisty half year ago.
But not even once I can browse to that website.

---

### Post by cookies on 2007-11-25
I get a favicon, and that's about it. Seems hung on 25% for me. :/ Weird issue here....

---

### Post by oneadvent on 2007-11-25
what parts can you not access?

---

### Post by FuturePilot on 2007-11-25
For some reason it gets stuck at Transferring Data...
Using Gutsy
Might be a thing on their end. You could try booting of one of the other live CDs and see if you can access it.

---

### Post by gali98 on 2007-11-25
Have you tried pinging it?
Kory

---

### Post by FuturePilot on 2007-11-25
Here's what I got from a ping
```
~$ ping -c3 www.ocbc.com
PING www.ocbc.com (203.126.194.62) 56(84) bytes of data.
From 165.21.43.110 icmp_seq=1 Packet filtered
From 165.21.43.110 icmp_seq=3 Packet filtered

--- www.ocbc.com ping statistics ---
3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 6579ms

```

---

### Post by gali98 on 2007-11-25
That's really weird. I don't really know what to tell you. I'm not real good at the whole networking thing yet. I'm sure this could help someone who knows what they're doing help you. 
I also just thought of a couple thing when writing this.
It could be blocked in your router.
You could probably just get to it going through a proxy. Just a thought.
Kory

---

### Post by FuturePilot on 2007-11-25
Interesting. It worked through a proxy. That's very odd:confused:

---

### Post by dakochan on 2007-11-25
When I pinged, I also have the same result:

> PING [www.ocbc.com](www.ocbc.com) (203.116.27.62) 56(84) bytes of data.
From atm0-0-0-34-r10.starhub.net.sg (203.116.10.90) icmp_seq=1 Packet filtered
From atm0-0-0-34-r10.starhub.net.sg (203.116.10.90) icmp_seq=2 Packet filtered
From atm0-0-0-34-r10.starhub.net.sg (203.116.10.90) icmp_seq=3 Packet filtered

--- [www.ocbc.com](www.ocbc.com) ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms


---

### Post by dakochan on 2007-11-25
I don't thing it has anything to do with the router.
Because I use PCLinux as well to the same router, but it can browse to the website.

Anyway, I ever changed the router before, but it showed the same result.

---

### Post by gali98 on 2007-11-25
> **dakochan said:**
> I don't thing it has anything to do with the router.
Because I use PCLinux as well to the same router, but it can browse to the website.

Anyway, I ever changed the router before, but it showed the same result.

Yeah didn't even think of that. Fiesty must filter it somehow....This is really beyond my scope.
I guess it worked through the proxy because it doesn't show the ip address of that site. IT comes through as coming from the proxy which isn't filtered. You might check in the network manager or some such thing to see if it has a blocked list.
Kory

---

### Post by handzmonkey on 2007-11-25
The ping really doesn't mean anything.  As it is a bank's website  they are filtering the ping request so you would either get the error message like the one you got or
3 packets transmitted, 0 received, 100% packet loss, time 2000ms.  I am running 7.10 and was able to view the website, but not ping it. Maybe try another browser in Ubuntu.  Also look at your java plugins.  It could be dying when it is trying to load the java on the webpage

---

