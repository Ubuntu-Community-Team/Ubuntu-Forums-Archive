---
title: "Navicat worked great on 10.04 but no love in 12.04"
date: 2014-04-03
forum: General Help
---

### Post by ionplay on 2014-04-03
Upgraded from 10.04 to 12.04 recently; but I was reluctant because 10.04 was working so well.

I had installed 12.04 at home for the wife and kids - and they enjoy the Unity interface - 12.04 appeared to be stable/robust/etc....

for the most part everything works well - the big thing was having google chrome working which does not work in 10.04 - chromium does not do flash which is a pain


I had to upgrade my Java to get ireport / jaspersoft to work on 12.04 - not a problem - and the ireport plugin for Eclipse is actually better than the stand alone program anyways

the biggest pain was Navicat which worked great in 10.04 - does not fire up in 12.04
I read countless articles on the subject and searched every log/dump file I could find - nothing of any substance

I even switched from Unity to gnome fallback because some claimed that was the problem - foolishly I believed them - it changed nothing

SQLdeveloper will work - java program
SQuirreL will not install - not sure why yet - different problem

but because I paid for Navicat Premium I thought I would try their support ticket 
[http://support.navicat.com/index.php?_a=tickets&_m=listview&_i=RHM-73469](http://support.navicat.com/index.php?_a=tickets&_m=listview&_i=RHM-73469)

they told me to go back to 10.04 as a solution - which is not an option now - and completely unacceptable as a proposed solution

the purpose for this post is to see if someone much smarter than I has figured out Navicat on 12.04 and can show me what I have overlooked

and/or - is there some other Visual SQL tool that works great on 12.04 - fishing for a Navicat alternative testimonial - I am very open to switching tools at the moment

---

### Post by grahammechanical on 2014-04-03
Have you seen this?

[http://wiki.navicat.com/wiki/index.php/Can_I_run_Navicat_on_64-bit_Linux%3F](http://wiki.navicat.com/wiki/index.php/Can_I_run_Navicat_on_64-bit_Linux%3F)

> [COLOR=#000000][FONT=sans-serif]You need to install all 32-bit libraries before working on 64-bit Linux.[/FONT][/COLOR]

> [COLOR=#000000][FONT=sans-serif]**For 64-bit Debian/Ubuntu**[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]sudo apt-get install ia32-libs[/FONT][/COLOR]


Since the release of Ubuntu 10.04 Ubuntu developers have introduced what are called multiarch libraries. It could be that in 12.04 ia32-libs is not installed that the Navicat developers have not kept up to date with the changes in Debian/Ubuntu.

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

Please read that wiki page. It has some advice.

Regards.

---

### Post by ionplay on 2014-04-03
[COLOR=#000000]grahammechanical,
[/COLOR]yes you are correct - I have read that article - unfortunately that is not my problem - as I am already on 32bit - specifically to have avoided the 64bit issue

CC3103:~$ uname -a
Linux CC3103 3.2.0-60-generic-pae #91-Ubuntu SMP Wed Feb 19 04:14:56 UTC 2014 i686 athlon i386 GNU/Linux

but thank you for the response

---

