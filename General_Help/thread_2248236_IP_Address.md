---
title: "IP Address?"
date: 2014-10-13
forum: General Help
---

### Post by tomsubt on 2014-10-13
Hello Everyone,  How do I get my ip address to come up on ubuntu?  Thanks

---

### Post by nerdtron on 2014-10-13
What's your GUI? 
Right Click on the network icon> Connection Information

On the terminal, type "ifconfig" and press enter.
Laptop can have wlan0 or eth0 interfaces.

---

### Post by tomsubt on 2014-10-13
> **nerdtron said:**
> What's your GUI? 
Right Click on the network icon> Connection Information

On the terminal, type "ifconfig" and press enter.
Laptop can have wlan0 or eth0 interfaces.

I tried the ipconfig in terminal and it did not recognize the command, but I did get it
with the Connection information, Thank you
PS, why didnt the terminal work, any ideas? Thanks

---

### Post by nerdtron on 2014-10-13
It is not "**ipconfig**" it is "**ifconfig**".

---

### Post by whitesmith on 2014-10-13
If you're behind a NAT router, ifconfig generally won't give your external IP. Here's a trick I read about years ago that never failed to work for me:```
curl -w '\n' ident.me
```

---

### Post by nerdtron on 2014-10-13
> **whitesmith said:**
> If you're behind a NAT router, ifconfig generally won't give your external IP. Here's a trick I read about years ago that never failed to work for me:```
curl -w '\n' ident.me
```

HHmmm thanks.. The site is very minimal and straightforward. Is it safe to embed on scripts? I mean does this site go down sometimes?

---

### Post by whitesmith on 2014-10-13
Never known it to. If you look around you'll find alternatives.

---

