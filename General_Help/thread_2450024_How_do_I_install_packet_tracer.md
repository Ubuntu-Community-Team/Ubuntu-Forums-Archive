---
title: "How do I install packet tracer?"
date: 2020-09-06
forum: General Help
---

### Post by zazonion1996 on 2020-09-06
So the faq pdf file says to "Run the command "sudoapt-get install  <absolute path to the .deb file>" and follow the instructions  shown on your screen." 


Problem is I legit have only touched the terminal twice in my life.  If I have the .deb file for packet tracer in my downloads folder what  would be the absolute path to it?

---

### Post by deadflowr on 2020-09-06
Not sure apt-get can do that, but apt does.
Something like
```
cd Downloads
sudo apt install ./package-name.deb
```
Replace package-name.deb with the proper package name.

or
for full path it should be like
```
sudo apt install /home/Username/Downloads/package-name.deb
```
Replace Username with your user's name.

Alternatively you can go use the older method and use dpkg
Basically the same as apt but usually requires one more step
like
```
cd Downloads
sudo dpkg -i package-name.deb
sudo apt install -f
```

The difference between apt and dpkg is that dpkg doesn't handle any dependency issues,
so sometimes it requires running the apt install -f command to fix that.
apt handles dependencies so that would be taken care of.

---

### Post by zazonion1996 on 2020-09-12
Awesome thanks. apt didn't work, but dpkg did!

---

