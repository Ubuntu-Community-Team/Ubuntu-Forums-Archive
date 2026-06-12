---
title: "Is minicom on live CD?"
date: 2005-04-27
forum: General Help
---

### Post by JHolmes763 on 2005-04-27
If I type the program from the terminal, it says not found. Is this program on the Live CD? Where should I look / how can I start it, if so?

I'm in a Cisco class and am trying to use the Live CD (using it now, actually) to connect to our routers through the COM1 port (or is it /dev/ttyS0 in linux?). From what I could find searching, minicom is what I'm after. If not, can anyone recommend something else?

Thanks. 

---John Holmes...

---

### Post by JHolmes763 on 2005-05-01
**sudo apt-get install minicom** (as recommended on another forum) worked for me, btw. I just have to do it every time. ;) 

---John Holmes...

---

### Post by angrykeyboarder on 2005-05-07
[QUOTE=JHolmes763]**sudo apt-get install minicom** (as recommended on another forum) worked for me, btw. I just have to do it every time. ;) 

---John Holmes...[/QUOTE]

I finally got tired of reinstalling everything (at least via the usual method) so, last time I copied all the debs that I'd always been downloading and installing, to a USB flash drive (1GB) and now I just copy that directory into my home directory and do a "dpkg - i *" and save myself about 30 minutes downloading and installing with apt-get or Synaptic. :-)

One of these days I'll just install Ubuntu and stop playingn with the Live CD.... ;-)

---

### Post by JHolmes763 on 2005-05-07
Good idea. I wondered about that. My USB drive just broke, so I've got to order another... will try that when it comes in. 

---John Holmes...

---

