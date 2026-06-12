---
title: "It works! Now what?"
date: 2013-02-12
forum: General Help
---

### Post by confuciousdragon on 2013-02-12
I finally got my ubuntu installation working after months of working to install it. Hooray! However, now I have this operating system that I know is great, but I don't know what to do with it. I'm running a dual-boot Windows 7/Ubuntu 12.10 installation. 

The main reason I downloaded linux was to improve my abilities as a programmer and get more experience for my career as a software developer (graduating college soon).  I'm looking to learn more Network programming, and need some more background in jquery and javascript specifically. Also, I'm still not that great with the terminal.

I'm just looking for suggestions on things people think a beginner ubuntu user would benefit from: software addons, interface tutorials, etc. I'm extremely new to linux, but want to get the most out of it that I can.

---

### Post by Bucky Ball on 2013-02-12
Write us some Greasemonkey scripts in Javascript:

[http://www.w3schools.com/js/js_howto.asp](http://www.w3schools.com/js/js_howto.asp)

There's heaps of stuff there. Greasemonkey is an add-on for Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/)

I know little myself but have just been checking it out.

---

### Post by Luckiboy on 2013-02-12
When I started with Linux in general, was... just beginning to use the system. Try, and fail. Try again, and if you're really not able to solve the problem yourself, search the solution on the internet. 
To increase the usability of your system, I recommend this site: [https://sites.google.com/site/easylinuxtipsproject/](https://sites.google.com/site/easylinuxtipsproject/) It contains the most important tweaks to start.
Success ;)

---

### Post by offgridguy on 2013-02-12
To help with terminal commands, here.

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by tgalati4 on 2013-02-12
Find an open source project that needs development work.  As you dig into the details, it will become clear what skills you need.

---

### Post by confuciousdragon on 2013-02-12
Alright, just finished going through all the articles on easylinuxtips. I enjoyed those, albeit a tedious process.

These command-line resources are a little bit overwhelming. I'll trudge through them in time.

I'm definitely interested in joining some open source projects. Where would be the place to go for that?

---

### Post by tgalati4 on 2013-02-12
Ask yourself the question:  *What interests me?*

Development work starts with passion for something in your life.  Find that passion and then find an open source project related to that passion.

For instance, let's say you like digital photography.  Well, there are a lot of programs used to process photos:

tgalati4@Mint14-Extensa ~ $ apt-cache search photography
darktable - virtual lighttable and darkroom for photographers
f-spot - personal photo management application
gimp-plugin-registry - repository of optional extensions for GIMP
ubuntustudio-photography - Ubuntu Studio Photography Package
tgalati4@Mint14-Extensa ~ $ apt-cache depends ubuntustudio-photography 
ubuntustudio-photography
  Depends: argyll
  Depends: darktable
  Depends: gimp
  Depends: gimp-data-extras
  Depends: gimp-gap
  Depends: gimp-plugin-registry
  Depends: gimp-resynthesizer
    gimp-plugin-registry
  Depends: gimp-ufraw
  Depends: gnome-color-manager
  Depends: icc-profiles-free
  Depends: phatch
  Depends: rapid-photo-downloader
  Depends: rawtherapee

So let's say you are interested in RAW digital processing, then spend some time with this project:

[http://www.rawtherapee.com/](http://www.rawtherapee.com/)

And immediately on that page, you see a call for testers, a call for tutorials, etc.

Find your passion, and the linux skills will follow.

---

### Post by Bucky Ball on 2013-02-13
Another good idea is to have a stable install for everyday use, say 12.04 LTS, then test 13.04 on another partition, or have a couple of partitions spare to install what you want and break. This way, you will always have the stable 12.04 fallback. ;)

I always have a couple of spare 15Gb partitions on the machine along with the LTS release.

---

### Post by grahammechanical on 2013-02-13
An open invitation to absolutely anyone:

[http://developer.ubuntu.com/get-started/]("http://developer.ubuntu.com/get-started/")

You just missed this:

[https://wiki.ubuntu.com/UbuntuDeveloperWeek]("https://wiki.ubuntu.com/UbuntuDeveloperWeek")

but click on the timetable links and you get the IRC logs. Canonical is starting to make is possible for anyone to develop for Ubuntu.

Regards.

---

