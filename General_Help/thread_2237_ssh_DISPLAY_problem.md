---
title: "ssh DISPLAY problem"
date: 2004-10-26
forum: General Help
---

### Post by macsaint on 2004-10-26
I remotely log in unix machine from my ubutu linux machine as

ssh -X XXX.XX.edu
setenv DISPLAY 10.5.XX.XXX:0.0
xterm

However, I met this error

xterm Xt error: Can't open display: 10.5.XX.XXX:0.0

Please let me know a solution. I have never met this problem using several linux
distors..   This is quite important factor to me...

Thanks
JW

---

### Post by vulpes on 2004-10-26
By default, tcp connectivity is disabled on your X server

Change the following in /etc/gdm/*gdm.conf

DisallowTCP=false

(change from true to false)

---

### Post by macsaint on 2004-10-26
[QUOTE=vulpes]By default, tcp connectivity is disabled on your X server

Change the following in /etc/gdm/*gdm.conf

DisallowTCP=false

(change from true to false)[/QUOTE]

Thanks Vulpes, But now it shows slightly different error as:

Xlib: connection to "10.5.XX.XXX:0.0" refused by server
Xlib: No protocol specified
xterm Xt error: Can't open display: 10.5.XX.XXX:0.0

Please help me once more  :) 

JW

---

