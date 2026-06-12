---
title: "Issue after installing Bitwarden"
date: 2021-10-16
forum: General Help
---

### Post by katrinedamberg on 2021-10-16
Hi 

I'm new to ubuntu and I really need some help – I can't connect to the internet. 

I was trying to set up Bitwarden. I would just like to install the app (which I'm used to using on my Mac), but I think I didn't something completely wrong. Now it says "Connection failed. Activation of network connection failed" - I have a network cable plugged in and it worked fine before. 
When I open terminal it changed the promt to "katrine@bitwarden".

I had some troubles with getting the app to work properly, so I tried to fix it in terminal... And it seems like it was a big mistake.

I really hope somebody out there can help me.

---

### Post by GhX6GZMB on 2021-10-16
It seems you might have made a bit of a mess with your Ubuntu install.
The terminal prompt tells you that you are user "katrine" logged into the machine "bitwarden". I don't know if this is correct?

In any case, you need to tell us more.

---

### Post by katrinedamberg on 2021-10-17
yes, that was what I thought too. 

What should I tell you? How do I figure out more about what I have done wrong?

---

### Post by katrinedamberg on 2021-10-17
My internet connection works again, but I still have the issue with being logged into bitwarden, showing the "katrine@bitwarden" in terminal. 

I considered if it was better just to reinstall ubuntu all together?

---

### Post by rbmorse on 2021-10-17
At this point, since you don't know for sure what led to the connection error, I'd say a reinstall would probably be the easiest way to recover. 

BTW...I use Bitwarden on Ubuntu and can tell you that it works fine. Where did you get the bitwarden package?

---

### Post by katrinedamberg on 2021-10-17
thanks. I'll reinstall. 

How would you say is the best way to install Bitwarden (the app)?

---

### Post by rbmorse on 2021-10-18
Which version of Ubuntu are you installing?  21.10 has Bitwarden available as a SNAP package.  It's a safe installation, what I'm using and it does what it is supposed to without fuss. 

If you are allergic to SNAPs as some people are, you can get the .deb installable package directly from Bitwarden's web page and install it with apt or dpkg or the gdebi package manager.

---

### Post by GhX6GZMB on 2021-10-18
> **katrinedamberg said:**
> thanks. I'll reinstall. 

How would you say is the best way to install Bitwarden (the app)?

Quite frankly, I'd say that getting your basic install stable and running is _*issue number one*_.

The Bitwarden thing can be fixed afterwards, Internet access runs from the start without issues.

---

