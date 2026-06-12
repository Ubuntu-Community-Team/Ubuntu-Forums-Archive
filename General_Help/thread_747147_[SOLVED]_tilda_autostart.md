---
title: "[SOLVED] tilda autostart"
date: 2008-04-06
forum: General Help
---

### Post by harrybazeegar on 2008-04-06
HI...

I have been using tilda since a long time... i want to know how to make tilda start automatically with my session...

i tired adding `tilda` to the end of ~/.bashrc but it caused a queer problem:
with the loading of the terminal in tilda, the .bashrc script was executed again. 
So i get another tilda, then again bashrc, then again tilda, then ....

so what do i doooo?? :)

cheerio

---

### Post by harrybazeegar on 2008-04-07
helloop

---

### Post by tamoneya on 2008-04-07
try going into system->preferences->settings.

Please wait 24 hours before bumping

---

### Post by harrybazeegar on 2008-04-07
pardon... settings?

in pregerences i got:
   screensaver
   screen resolution
   sessions
   sound
   SCIM input method setup

so what do i look for?

I m using GNOME on ubuntu 7.04... just so u know

---

### Post by FuturePilot on 2008-04-07
In System&#8594;Preferences&#8594;Session
Add a new entry. Give it a Name and put this in for the command
```
tilda
```
Give it a Comment if you want. It will now start when you login.

---

### Post by harrybazeegar on 2008-04-07
thanks!

btw how do i do this by command line? i mean there must some session startup script or something..??

---

### Post by tamoneya on 2008-04-07
sorry that was a typo on my part.  Thanks Future Pilot

---

