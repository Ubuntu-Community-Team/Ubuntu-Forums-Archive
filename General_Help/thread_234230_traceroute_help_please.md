---
title: "traceroute help please"
date: 2006-08-11
forum: General Help
---

### Post by _simon_ on 2006-08-11
I've been having a few problems recently where my webspace appears to be down. My hosts tell me that there were no issues their end yesterday when I was unable to get on and advised I use traceroute.

So, i installed traceroute and ran it.

Now the problem is the output doesn't help me at all... is it supposed to just do this (see below) or are there any flags I should be running it with?

```

simon@Ghosttouch:~$ traceroute ukrabbitsandcavies.info
traceroute to ukrabbitsandcavies.info (69.16.221.62), 30 hops max, 40 byte packe ts
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
simon@Ghosttouch:~$

```

---

### Post by beercz on 2006-08-11
Wrong forum?

---

### Post by _simon_ on 2006-08-11
Didn't know where to post it...

I don't know if it's a traceroute problem or just me not understanding how it works.

---

### Post by beniwtv on 2006-08-11
You are doing all right. Traceroute works like this.

But, unfortunately, your server appear to be not working or down? Were are you trying to use traceroute? On your server? Home PC? Strange enough that it doesn't work for some reason.

---

### Post by _simon_ on 2006-08-11
I was doing it on my home pc. I use a webhost in america.

What kind of output should I be getting?

I've just tried it again knowing that the server is ok and I CAN view my website, but traceroute gives the same output as it did before.

Would my router be causing a problem?

---

### Post by beniwtv on 2006-08-11
Unless you are directly connected with the same ISP as your server, in the first instance you should getting your router instead of the ***.

---

### Post by mozetti on 2006-08-11
The "***" indicates that traceroute wasn't able to determine the IP/name of the computer it contacted. Some example output might be (the **bold parentheses** info added by me for explanatory purposes):

```
simon@Ghosttouch:~$ traceroute ukrabbitsandcavies.info
traceroute to ukrabbitsandcavies.info (69.16.221.62), 30 hops max, 40 byte packe ts
 1  192.168.1.1 **(your router)**
 2  80.64.5.30 **(ISP local server)**
 3  80.64.10.20 **(ISP main server)**
 4 112.50.32.6 **(some server along the way)**
 5  69.16.221.62 **(the server you tracerouted to)**
simon@Ghosttouch:~$
```

I can't help explain why you're not getting info, but at least this is what you're looking for. It's possible that instead of IP addresses, it might be "reg01.cust.t-com.de" - the name of the server computer contacted.

---

### Post by _simon_ on 2006-08-11
Just ran it again, this time via Administration -> network tools

This time it did 31 hops, with hop1 showing the IP for my machine.

I guess it's a router issue then.

---

### Post by Patrick-Ruff on 2006-08-11
yeah routers have a habbit of getting in the way of things like that. if you really want to figure this out you could always plug your computer directly into the internet.


good luck

---

