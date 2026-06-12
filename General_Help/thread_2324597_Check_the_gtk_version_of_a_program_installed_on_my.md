---
title: "Check the gtk version of a program installed on my computer"
date: 2016-05-15
forum: General Help
---

### Post by joan_carles2 on 2016-05-15
I just need to check the gtk version used by some software installed in my computer.

How can I do that?

For instance I know that transmission uses gtk3... Which command I can use in the terminal to show to other people that transmisión uses gtk 3 libraries?

Regards

---

### Post by vasa1 on 2016-05-15
> **joan_carles2 said:**
> ...

For instance I know that transmission uses gtk3... Which command I can use in the terminal to show to other people that transmisión uses gtk 3 libraries?

...

Run ```
apt-cache show transmission-gtk
```
and look at the *Depends:* section:```
Depends: transmission-common (= 2.84-3ubuntu3), 
libappindicator3-1 (>= 0.4.90), libc6 (>= 2.14), libcurl3-gnutls (>= 7.18.0), libevent-2.0-5 (>= 2.0.10-stable), 
libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), **libgtk-3-0 (>= 3.3.16)**, 
libminiupnpc10 (>= 1.9.20140610), libnatpmp1 (>= 20101211), libpango-1.0-0 (>= 1.14.0), libssl1.0.0 (>= 1.0.0), 
zlib1g (>= 1:1.1.4)

```Note the **libgtk-3-0 (>= 3.3.16)**

Edit: You can list all programs using gtk3 (and their dependencies) using```
apt-get remove -s libgtk-3-0 | grep Remv | cut -d ' ' -f 2
```The absence of "sudo" and the use of "-s" means that just a simulation is run and nothing will be removed. Please note that this command won't work if you have held packages.

---

