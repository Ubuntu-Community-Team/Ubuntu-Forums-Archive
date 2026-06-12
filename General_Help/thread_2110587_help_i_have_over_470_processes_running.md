---
title: "help i have over 470 processes running"
date: 2013-01-30
forum: General Help
---

### Post by orbit1212 on 2013-01-30
i have over 470 processes running and my computer and it runs slow. i am running 12.4 how do i find out which processes are important and which ones i can kill. my cpu is running @ 98% and it only has a 1 gig or ram.  hp Intel® Pentium(R) M processor 1.86GHz 1001.4MiB memory hp compaq NC6230 what can i do?

---

### Post by dannyboy79 on 2013-01-30
run the command from a terminal window
```
top
```
then once in top, you can sort them by most used memory by hitting shift+o and then o again and then enter. with only 1gb of ram I would suggest not running ubuntu with unity or at least only run Unity 2D or switch to xubuntu or lubuntu which have a much lighter footprint.

---

### Post by kanikilu on 2013-01-30
Well, what's taking up the most resources? Use the system monitor - or something like top or htop if you want to view in the terminal - to view the running processes and sort by memory or CPU usage.

However, there is no list of "these are useful" processes. What's useful to me (say, the LAMP stack) may be completely useless to you.

That said, the Pentium CPU and 1GB of memory is barely above the recommended system requirements, so I can't imagine the computer is going to run particularly fast, no matter what "useless" processes you kill.

Have you looked into a lighter-weight version of Ubuntu. Xubuntu (XFCE) and Lubuntu (LXDE) may be worth trying if you're not too heavily invested in the current setup...

Also, don't forget that some memory is used as a cache, to make the system faster: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by orbit1212 on 2013-01-31
guys thanks so much for the help i am looking at the other versions of ubuntu now it may workout alot better for me i think im just a novice and since i have found this site my knowledge has grown and thanks to users like y'all ill survive learning a new operating system thanks a mill from an actively learning nube :KS:D

---

### Post by ibjsb4 on 2013-01-31
I don't know why you have so many processes running, but with your computer spec's You should try Xubuntu.

[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by raja.genupula on 2013-01-31
> **orbit1212 said:**
> i have over 470 processes running and my computer and it runs slow. i am running 12.4 how do i find out which processes are important and which ones i can kill. my cpu is running @ 98% and it only has a 1 gig or ram.  hp Intel® Pentium(R) M processor 1.86GHz 1001.4MiB memory hp compaq NC6230 what can i do?


you should go for Light weight installation like 
Lubuntu and Xubuntu.
[http://en.wikipedia.org/wiki/Lubuntu](http://en.wikipedia.org/wiki/Lubuntu)
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

---

### Post by dannyboy79 on 2013-01-31
> **orbit1212 said:**
> guys thanks so much for the help i am looking at the other versions of ubuntu now it may workout alot better for me i think im just a novice and since i have found this site my knowledge has grown and thanks to users like y'all ill survive learning a new operating system thanks a mill from an actively learning nube :KS:D
glad we could help. the ubuntu community is top notch IMO. Not many communites out there that are so active and willing to help others.

if you ever want real time support (still voluntary keep in mind) then go check out the ubuntu IRC channel on freenode IRC server. IRC stands for Internet Relay Chat and is basically a huge chat room with people who vary in skill level from experts and n00bs. there is most likely someone in there what has gone through the same issue you may be having at the time and can help out within the main chat window or start a private chat with you

---

