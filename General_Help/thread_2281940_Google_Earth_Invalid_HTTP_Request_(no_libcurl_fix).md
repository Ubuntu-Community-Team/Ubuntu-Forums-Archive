---
title: "Google Earth Invalid HTTP Request (no libcurl fix)"
date: 2015-06-10
forum: General Help
---

### Post by adambond on 2015-06-10
Whew!! Ubuntu never stops being awesome! 

So I go to use Google Earth and get the 'invalid Http request' error everyone is familiar with. 

All the fixes ive found, involve either changing the libcurl or uninstalling and reinstalling the newest version. 

Problem 1, currently, my google earth does not have any libcurl.so. yada yada.  I am running (apparently) google earth 5.2.1. 

Problem 2. I have TONS of places saved in my google earth. And dont want to lose them. So not sure how to remove, and reinstall while keeping my saved places.

---

### Post by cariboo on 2015-06-11
If you are using a 64-bit system you may have to use some 32-bit libraries, Google earth really isn't really  64 bit app

---

### Post by adambond on 2015-06-11
Sorry Im 32bit.

---

### Post by Portaro on 2015-06-11
Do you try this solution (rename libcurl.so.4)

[http://askubuntu.com/questions/314509/how-to-correct-google-earths-invalid-http-request-notice](http://askubuntu.com/questions/314509/how-to-correct-google-earths-invalid-http-request-notice)

---

### Post by adambond on 2015-06-11
Yes. I tried that. But my version of Google Earth has no Libcurl.so file.

---

### Post by adambond on 2015-06-11
I got it figured out. I ran all this code installing the newest version. 

```
sudo apt-get install lsb-core 
```

```
cd /tmp 
```

```
wget -c http://goo.gl/lu65z -O google-earth-stable_i386.deb 
```

```
sudo dpkg -i google-earth-stable_i386.deb
```

32bit system

---

