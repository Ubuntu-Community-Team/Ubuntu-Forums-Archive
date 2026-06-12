---
title: "Computer Sluggishness"
date: 2007-06-01
forum: General Help
---

### Post by mp4215 on 2007-06-01
Of late (the past week or so) my computer has been rather sluggish in starting up programs. Firefox takes at least 20-30 seconds if not a minute to load. Amarok the same. I don't even dare booting OOo. Even programs which used to be snappy like Gvim, the terminal and file browser are now slow. Whats weird is that everything used to be fast.

My computer is using the latest version of Ubuntu (fiesty) and I update using Synaptic every few days. When it boots less than 1/2 of the total ram (786mb) is used. No swap is used. 


Any suggestions on how to speed it up? Do you need any more details? I guess this is probably pretty vague but I am not sure what else would be needed.

---

### Post by Mikey_MW on 2007-06-02
Is there any other changes to your computer recently that you can think of? Any added packages... As a temporary workaround see if you can get by on high speed apps - dillo, abiword. Some more information on the machine might help

EDIT: Oh and I forgot - sometimes (rarely) updates might reset any settings you might have that affect speed. Is OpenOffice memory tweaked?

---

### Post by jjacobs2 on 2007-06-02
Try "sudo hdparm -t /dev/sda"
without quotes.  That should test your hard drive speed.  Mine is 50 MB/sec so around there is good.  Also try opening system monitor in administration and then opening a large program.  Watch the CPU usage to see if that is 100%.  375 MB of ram filled just by booting is quite a bit.  My computer usually uses under 200 with light usage.  Maybe look at what programs are using a large amount of ram in system monitor and try closing them if they aren't necessary?

---

### Post by mp4215 on 2007-06-02
My computer is pretty old by todays standards. I built it in 2001. 
Proc: Athlon XP 1800+
Memory: 784mb ddr
Hard drives: 250gb, just bought last summer, an older disk that is 10gb or so.
 
I cannot think of anything that I installed that would have done this. I did just install java, but that was after this problem started showing up. 

Here is the hdparm stuff.
> mikeyp@prometheus:/dev$ sudo hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:   68 MB in  3.11 seconds =  21.90 MB/sec
mikeyp@prometheus:/dev$ sudo hdparm -t /dev/hdd

/dev/hdd:
 Timing buffered disk reads:  162 MB in  3.03 seconds =  53.52 MB/sec
mikeyp@prometheus:/dev$ sudo hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:   70 MB in  3.07 seconds =  22.80 MB/sec
mikeyp@prometheus:/dev$ sudo hdparm -t /dev/hdd

/dev/hdd:
 Timing buffered disk reads:  172 MB in  3.02 seconds =  56.99 MB/sec
mikeyp@prometheus:/dev$ sudo hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:   70 MB in  3.06 seconds =  22.87 MB/sec
mikeyp@prometheus:/dev$ sudo hdparm -t /dev/hdd

/dev/hdd:
 Timing buffered disk reads:  132 MB in  3.01 seconds =  43.89 MB/sec


I started up the System monitor. When idle my cpu is somewhere around 10%. I started up OOo and it actually did not take that long. About 10 seconds and the cpu usage peaked at about 60%.

---

