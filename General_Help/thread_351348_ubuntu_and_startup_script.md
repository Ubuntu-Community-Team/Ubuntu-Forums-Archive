---
title: "ubuntu and startup script"
date: 2007-02-01
forum: General Help
---

### Post by finchy on 2007-02-01
Hi fellas,

I'm totally new to Ubuntu and I've stucked in one place. I have wireless network in my laptop; after long fight I managed to get it operational. But there is a glitch: every time I start computer I have to use this command in terminal:

 ```
sudo iwconfig eth1 mode auto
``` 

This is essential, otherwise when mode is as "managed" connection does not work. And for what I know it is impossible to change iwconfig permanently; it will always load deafult settings. Could some please guide me how to create a script for that and make it works everytime computer is started? 

Many Thanks

---

### Post by kerry_s on 2007-02-01
Put it in rc.local just under the #!/bin/sh.

sudo gedit /etc/inint.d/rc.local

put

iwconfig eth1 mode auto &

It will then run on startup as root.

---

### Post by eggdeng on 2007-02-01
> **kerry_s said:**
> 
sudo gedit /etc/inint.d/rc.local


Should read /etc/init.d/rc.local

---

### Post by finchy on 2007-02-01
Thanks!!! Works great!

---

### Post by kerry_s on 2007-02-01
> **eggdeng said:**
> Should read /etc/init.d/rc.local

Sorry, my big fat fingers or double vision got in the way. :(

---

