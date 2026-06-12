---
title: "what is external IP address of my router"
date: 2013-02-04
forum: General Help
---

### Post by marchelloUA on 2013-02-04
Hi all, 

how do I know what is external IP address of my router (set using dhcp) in console?

---

### Post by Cheesemill on 2013-02-04
```
curl ifconfig.me
```

---

### Post by haqking on 2013-02-04
> **marchelloUA said:**
> Hi all, 

how do I know what is external IP address of my router (set using dhcp) in console?
  visit [https://www.whatismyip.com/](https://www.whatismyip.com/)

and it will tell you, there are many ways to do so including from CLI however this is quick and simple.

You could also log into your router to see.

Peace

---

### Post by Warren Hill on 2013-02-04
Goto [https://www.google.co.uk](https://www.google.co.uk)

and type 

find my ip address

in the search box

Alternatively most routers have a status page which will tell you.  It should be described in the documentation that came with your router

---

### Post by dan000 on 2013-02-04
I use [http://checkip.dyndns.com/](http://checkip.dyndns.com/). In my experience, it tends to be faster than ifconfig.me. There are tons of places to check this.
If you have w3m installed, you could do ```
w3m -dump checkip.dyndns.com
```, or just ```
curl checkip.dyndns.com
```, and look in the <body> tag.

---

### Post by rnerwein on 2013-02-04
> **marchelloUA said:**
> Hi all, 

how do I know what is external IP address of my router (set using dhcp) in console?
in a terminal type:

ipadr="`wget -O - -q icanhazip.com`"
echo "that's my external IP: $ipadr"

that's it
cheers

---

### Post by cutesar on 2013-12-16
> **dan000 said:**
> I use [http://checkip.dyndns.com/](http://checkip.dyndns.com/). In my experience, it tends to be faster than ifconfig.me. There are tons of places to check this.
If you have w3m installed, you could do ```
w3m -dump checkip.dyndns.com
```, or just ```
curl checkip.dyndns.com
```, and look in the <body> tag.


hi,

    I visit the site what you have mentioned above . It shows only my current ip address. I'm in need to know my geolocation, country , etc. So far i have searched in online and get those details from  [Ip-details.com]("http://www.ip-details.com/")

---

### Post by jimmyh1972 on 2013-12-17
open terminal:

curl http:[COLOR=#000000]**//**[/COLOR]ipecho.net[COLOR=#000000]**/**[/COLOR]plain; [COLOR=#7A0874]**echo**[/COLOR]

---

### Post by Habitual on 2013-12-18
```
curl icanhazip.com

```
There's a gazillion of them, few with geo-data elements.

---

