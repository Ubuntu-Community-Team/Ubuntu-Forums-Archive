---
title: "The Tor Project on Ubuntu (on GNU/Linux) - help please"
date: 2015-08-26
forum: General Help
---

### Post by michael-piziak on 2015-08-26
Ubuntu 12.04 LTS here - 64 bit version

I find the Tor Project to be very desirable - I *think* it allows you to surf the web without being tracked by even your ISP - I *think* so again.

I downloaded something called Tor from the software center - had problems running it.

I downloaded 64 bit Tor browser from their website - got errors.

See my 3 screenshots below and help me if you can.

---

### Post by Yellow Pasque on 2015-08-26
> I downloaded 64 bit Tor browser from their website - got errors.


```
sudo apt-get install xz-utils
```

---

### Post by uRock on 2015-08-26
I download from this site, [https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en) , 
Move it to the home folder,
Right-click and select **Extract Here**,
then open a terminal and run the following to launch it,```
cd tor-browser_en-US/Browser/
./start-tor-browser
```
or
```
cd tor-browser_en-US/Browser/ && ./start-tor-browser
```

Edit: Run the command offered by Temüjin first.

---

