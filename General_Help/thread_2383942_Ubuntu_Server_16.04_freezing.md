---
title: "Ubuntu Server 16.04 freezing"
date: 2018-01-31
forum: General Help
---

### Post by vladipiggy on 2018-01-31
I run a small gaming server from home. I finally got a new pc for it, and I set it up in October, and it has been broken ever since. I have been working and working, but it didn't work. Firstly I assumed my server got messed up in the FTP transfer, but I found that isn't the case. I have let it sit for a while, but a few weeks ago I just started it to try out an idea. Even when I don't have the game loaded it freezes. Usually when it freezes I can turn the monitor on and view the last thing the screen did before it froze. It accepts no inputs or anything, but it is there. This time whit nothing loaded it simply said tty1. I fell this could be a huge help, but I looked it up and hit another dead end. I got bored today and decided I'd try my luck here as I hadn't seen anything about this site before today. I have been asking for months to no avail. There is some command I forgot where it is something like RESUIB that is supposed to fix a frozen server, but that did nothing as the keyboard doesn't communicate. Pressing caps lock doesn't light up the indicator, so I'd assume it doesn't "talk" to the server.

---

### Post by Autodave on 2018-01-31
Since no one else has jumped in, let me give you a few ideas.

First off, it sounds more like a hardware problem than software. To make sure, make a boot disk or USB drive and run Ubuntu or Xubuntu from that. If that freezes up then you can be rather sure that you have a hardware problem. If so, my first thought is a power supply issue. Do you have a lot of peripherals plugged in? If so, they me be drawing too much power and temporarily causing the power supply to shut down. (This makes sense since you state that the Caps button ceases to function.)  A shorted keyboard or mouse could also cause this.

It could also be a memory problem: stick going bad. If you have more than one stick of RAM in there, you could try removing one at a time and see if problem goes away. Make sure that you are putting them in the proper place: there must always be one in the first slot or it will not work.

---

### Post by vladipiggy on 2018-01-31
Ok so I reinstalled the whole os today since nobody was responding. So along with that I bent a pin on the mobo assembling it. I didn't realize it at first and I started it and it would start and stop randomly, but never fully boot. I fixed this when i found the bent pin bent it back and I had also oopsied a little bit of cpu paste into the socket. I was really clumsy. It now powers on but it stays up for a few days before shutting off. That was a few months ago, do you think the bent pin is still the problem?

---

### Post by #&amp;thj^% on 2018-01-31
Doubtful, but it might help if we knew what the I/O socket or port it was that the bent pin was in. (If Possible)

---

### Post by vladipiggy on 2018-01-31
It was the cpu port. It is a skylake so instead of cpu pins it is mobo cpu pins

---

### Post by vladipiggy on 2018-02-07
Hey sorry I know it has been a few days, so I thought I'd ask if you had any clue on what to do I reinstalled ubuntu, and so far so good. I will check it tonight when I get home and update this. Last I checked it had been up for like 5 days, with no problems.

---

