---
title: "Help"
date: 2006-11-24
forum: General Help
---

### Post by hilio on 2006-11-24
Hello everyone, i am very new to unbuntu and so far i am loving it.

when i go to install update i get these error's:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb)
  Could not resolve ‘216.72.196.21:80’


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb)
  Could not resolve ‘216.72.196.21:80’


from what i can make of it it says i am not connected to the net but i am, could any one help me please?

many thanks

Hilio

---

### Post by Tilex on 2006-11-24
Are you sure you're connected to the Web?  Surfing the Web works fine?  Otherwise I would guess that the server is too busy or something but that seems unprobable...

---

### Post by bapoumba on 2006-11-24
Hi, hilio,
so you can browse the internet but not perform any update from synaptic/adept ?
Could you paste the answer to :
[B]cat /etc/apt/sources.list
cat /etc/apt/apt.conf[/B]

Are you behind a proxy ?

---

### Post by hilio on 2006-11-24
yeah i am connected to the net etc because i am on the net right now like. and still errors been like that for a week or so.

---

### Post by PsaltyDS on 2006-12-05
In the network settings of your browser that's working, what are the proxy settings?  Adept and apt-get may not be setup for proxy, while the browser is, which gets you good browsing but no updates.

Hope that helps.

:)

---

