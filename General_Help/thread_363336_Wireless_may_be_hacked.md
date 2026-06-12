---
title: "Wireless may be hacked"
date: 2007-02-16
forum: General Help
---

### Post by corstar on 2007-02-16
I need a bit of help solving this problem.
I have a wired/wireless network and it is protected with encryption. My neighbor  seems pretty smart with networks and I'm sure he's tapping into the wireless to get free internet.

What are the tools and diagnostic tests I need to run to check this out?

I have already looked on the router info page to see who's logged in and that only shows my pc and laptop.

---

### Post by kpkeerthi on 2007-02-16
You have not mentioned what kind of secured wireless you have. Anyway, If your access point is WPA protected, you are pretty much secured. I dont think you neighbor could break into it. WEP is not as secure as WPA unless you change you passphrase every hour or so. As for the tools to monitor your network traffic install ethereal or wireshark. Both are available in the repository. 
```

sudo aptitude install ethereal

```

or 

```

sudo aptitude install wireshark

```

---

### Post by meng on 2007-02-16
Also you may be able to reduce the signal strength on your router so that it doesn't extend as far. And disconnect the router when you're not using it.

---

### Post by Rhaddad on 2007-02-16
Reset your wireless router from the reset button then
get all the computers you want connecting useing encyrption
make MAC filtering. 
And disable your SSID.

and it will all be good :D

---

### Post by AusIV4 on 2007-02-16
With my router, when I go to the router's IP in a web browser, it shows me a list of the computers on my network, both wired and wireless. Most routers I've worked with will have something like this.

---

### Post by esaym on 2007-02-16
> **AusIV4 said:**
> With my router, when I go to the router's IP in a web browser, it shows me a list of the computers on my network, both wired and wireless. Most routers I've worked with will have something like this.

Yea I was going to say that too.  Most of them keep inactive ip's in the list too.  As far as I know their is not a way to get around you ip showing in the log list....

---

### Post by corstar on 2007-02-17
Thanks for the tips.
I have a WEP encryption  that is changed every couple of months. I have my 2 linux boxes on a pertinent mac ip setting. 

I guess, I'm just being a little paranoid.

---

