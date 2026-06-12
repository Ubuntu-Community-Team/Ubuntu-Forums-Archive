---
title: "OpenJDK and Chrome/Chromium on Ubuntu 12.04 64-bit"
date: 2013-02-20
forum: General Help
---

### Post by wittyman37 on 2013-02-20
I have been trying to get OpenJDK 6 or 7 working with chrome/chromium for a while now.  I have downloaded the latest updates and have tried with openjdk 1.7.0_13 and 1.6.0_27 to no avail.  I installed the icedtea plugin, of course.  

>Firefox works fine with both openjdk versions
>Chrome/Chromium words fine with oracle 7 update 13
[COLOR=#303942][FONT=Ubuntu]Chromium Version 24.0.1312.56 Ubuntu 12.04 (24.0.1312.56-0ubuntu0.12.04.1)[/FONT][/COLOR]
[COLOR=#303942][FONT=Ubuntu]Google ChromeVersion 24.0.1312.70[/FONT][/COLOR]


I have tried purging all openjdk files and fresh installing 6, purging, and installing 7 with no luck.  I have been using javatester.org to test the web browser plugins using firefox, chrome, and chromium.  

Does anyone have any suggestions, or do I just have to use the oracle java?  (I am trying to be pro-opensource)

---

### Post by dino99 on 2013-02-20
as i know, javatester only find java, not the alternatives as openjdk.

here (on i386) i use both openjdk & chromium without issue  :D

---

### Post by wittyman37 on 2013-02-20
dino99, can you give me a better site to test java with?

I tried this site <[http://www.w3.org/2000/07/8378/object/java/clock](http://www.w3.org/2000/07/8378/object/java/clock)> using chromium and openjdk7
Chromium asked me if I wanted to run the script on this page, I clicked "always run" and the  clocks are just gray boxes.  This site works on firefox.

---

### Post by wittyman37 on 2013-02-21
I have been doing some reading, and it seems it was a known issue with  chromium and the icedtea plugin  <[https://bugs.launchpad.net/ubuntu/+source/icedtea-web/+bug/1025553](https://bugs.launchpad.net/ubuntu/+source/icedtea-web/+bug/1025553)>

However, I have the latest version running in chromium (IcedTea-Web  1.2 (1.2-2ubuntu1.3)) and I still get only gray boxes where java  applets are supposed to be running.  I get the prompt to allow the  script to run, but after clicking always allow, I get only a gray box.

---

### Post by sudo san on 2013-02-21
The official chrome for windows has java built in and on my 32-bit 12.10 machine I am running the official chrome with no problem. Although I have openjdk 7 installed and icedtea I do not know if it would run without it.

> 
(I am trying to be pro-opensource)


Although it is not opensource, official google chrome works very well on 12.04 and 12.10. I also tried the site for testing java and that works fine.

Post back if you want me to show you the quick and easy way to install it.

:D

---

### Post by etsah57 on 2013-04-21
I am running Chrome, And 12.4. 
I am tryying to download a file in Chrome and I have a box with a piece of jigsaw in it and a message 'IcedTea-Web Plugin (using IcedTea-Web 1.2.3 (1.2.3 0ubuntu0.12.04.1)) needs your permission to run
How do I do that?

---

