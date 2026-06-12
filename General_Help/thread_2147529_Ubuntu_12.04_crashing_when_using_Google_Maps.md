---
title: "Ubuntu 12.04 crashing when using Google Maps"
date: 2013-05-22
forum: General Help
---

### Post by Quazze on 2013-05-22
Hi everyone

I've got Ubuntu 12.04 and it seems very stable, except when I use Google Maps. It's the only time when Ubuntu crashes on my laptop. It doesn't happen everytime, but often Ubuntu just freezes without any warning when using Google Maps, and I have to reset my laptop. Is this a known bug? Anyone got the same? Is there maybe a fix? Or should I report this bug somehow?
I use Google Maps often so it would be nice if I could do something about it.

Thanks
Cheers

---

### Post by cipherboy_loc on 2013-05-22
Which browser are you using? How much RAM do you have in the system? 

Thanks,
Cipherboy

---

### Post by theNixGuy on 2013-05-22
Have you considered this might NOT be a laptop related issue? May be a browser related issue? Probably try installing separate browser like chrome and try to access it and let us know how it goes.

---

### Post by Quazze on 2013-05-23
Thanks for the quick response.
I use Firefox and have 8 Gb RAM. I don't think the RAM is the problem, 8 Gb is more than enough, isn't it?
I can try with another browser, but I'll have to use it for a while then, before I can definitely say it doesn't have the problem, because it doesn't happen always.

I'll report back.

---

### Post by Quazze on 2013-06-04
Yes, it seems like it's Firefox related, because (until now) it hasn't happened with Chrome. Still, it freezes the whole systemn when it does.

---

### Post by gordintoronto on 2013-06-04
Can you list any extensions you have installed in Firefox? Presumably it's version 21.0?

---

### Post by Quazze on 2013-06-05
Yes, the Firefox version is 21.0.
Extensions, only Adblock plus 2.2.4. There are also "Global Menu Bar integration 4.1" and "Ubuntu Firefox Modifications 2.6", but I think those are standard in Ubuntu. (I also have "Session Manager 0.8.0.7", but that I just installed a few days ago, so it has nothing to do with the crashes)

But I read somewhere, that someone claims it has to do with the WebGL, and if you disable that, the problem should be fixed. But I don't really know what WebGL is and what other effects disabling it can have...
[http://support.mozilla.org/en-US/questions/840823](http://support.mozilla.org/en-US/questions/840823)

---

### Post by borja-pacheco on 2013-08-23
I have the same issue. I don't have to reboot, but X got frozen, and I have to open term and kill the browser.
The problem persists with chrome and firefox.

---

### Post by stefano-1 on 2013-09-01
For those still experiencing the issue, I fixed my problem with:
[http://askubuntu.com/questions/298403/firefox-cannot-draw-the-new-google-maps/340161#340161](http://askubuntu.com/questions/298403/firefox-cannot-draw-the-new-google-maps/340161#340161)

---

### Post by PauloI on 2014-04-03
Unfortunately it seems not to be connected with Firefox. I have been using Street View on Chrome just before an hour and it has frozen my laptop completely. I had to power it off. I have 4GB RAM, Ubuntu 12.04, Fujitsu-Siemens M9410 laptop, 2,50Ghz x2. I turned it on and tried to restore Chrome session. The freeze has happened again. The total resume operation costed me one hour (1h) because I tried to kill some processes from terminal. 1h just to keep it going... The same has happened when I carefully just wanted to watch some embedded videos from web pages on full screen. The system has suddenly stopped reacting and neither Alt+1 or Alt+Ctrl+F1 or maybe Alt+Ctrl+1 hasn't helped. Only old and certain power-off + removing battery for 5 seconds. Yes, I am learning how to live with Ubuntu!

---

