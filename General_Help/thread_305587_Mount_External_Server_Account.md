---
title: "Mount External Server Account???"
date: 2006-11-23
forum: General Help
---

### Post by olieviya on 2006-11-23
I'd like to know if it's possible to mount an external server account on Ubuntu.

What I have is a ssh2 tunnel connection to a server with files/programs etc. Because I want to be able to access files run programs etc with more ease and since using putty every time i want to run a program/open a file/etc is quite time consuming - i thought that'd be a good plan.;)



(I'm running a m5550 alienware, if that helps in anyway :) )


EDIT: now that I'm thinking about it, it might not be... because that'll mean the files won't be updated back onto the server? You guys know much more than me ..

---

### Post by olieviya on 2006-11-23
If anybody has any other solution/work around for doing anything that will make my life easier, also welcome and I will be very thankful.

---

### Post by burek on 2006-11-24
> **olieviya said:**
> If anybody has any other solution/work around for doing anything that will make my life easier, also welcome and I will be very thankful.

we try to do the same same time 
[http://ubuntuforums.org/showthread.php?t=305671&highlight=putty](http://ubuntuforums.org/showthread.php?t=305671&highlight=putty)

i tried with putty tunnel but the firewall kick me ouut; block me

i have no idea

i tracert the pc and there is lot of nat in between


i cant

---

### Post by christhemonkey on 2006-11-24
Is this not poosible from the Places > Connect to Server dialog box?


Enter your username and password and the relevant numbers an then you can have it open as a folder on your desktop?

---

### Post by olieviya on 2006-11-24
> **christhemonkey said:**
> Is this not poosible from the Places > Connect to Server dialog box?


Enter your username and password and the relevant numbers an then you can have it open as a folder on your desktop?

Oh, cool, thanks it does, is it also possible to run programs in an easier way than putty?

---

### Post by christhemonkey on 2006-11-24
If it is  just an ssh tunnel to the server,
you can run the command:
```
ssh username@ser.ver.ipa.dres 
```

And if you want X forwarding run ```
ssh -X username@ser.ver.ipa.dres 
```

If they are executable files on the server then you can just double click on them when viewing the folder on your desktop.

---

### Post by olieviya on 2006-11-24
> **christhemonkey said:**
> If it is  just an ssh tunnel to the server,
you can run the command:
```
ssh username@ser.ver.ipa.dres 
```

And if you want X forwarding run ```
ssh -X username@ser.ver.ipa.dres 
```

If they are executable files on the server then you can just double click on them when viewing the folder on your desktop.

Ok, thank you :)

btw how do you get out of ssh and back to normal terminal?

---

### Post by christhemonkey on 2006-11-24
Type exit or logout (one of the two, i forget!)

---

### Post by olieviya on 2006-11-24
> **christhemonkey said:**
> Type exit or logout (one of the two, i forget!)

Heh, it's ok I found it: exit, quit, logout etc all work

---

### Post by christhemonkey on 2006-11-24
Mint.  If there's any other problems just let us know!

---

### Post by olieviya on 2006-11-24
> **christhemonkey said:**
> Mint.  If there's any other problems just let us know!

:mrgreen: 8) 

thanks x

---

