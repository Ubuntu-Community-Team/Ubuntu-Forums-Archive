---
title: "Strigi"
date: 2008-05-18
forum: General Help
---

### Post by Luft on 2008-05-18
I have kubuntu loaded on my laptop and noticed that my 160 Gb hard drive was almost full.  After using durep to get a report on my disk usage I found almost 90 Gb were located in the .strigi directory!

Is there a way to set a limit to the amount of drive space the indexer will use?

Thanks.

---

### Post by TuxLove on 2008-05-19
Same here. On my 160GB /home folder Strigi has eaten 100MB! The more disk I free up, the more it consumes. In fact I can even watch the numbers change by looking at its status. Here's what it shows now...

[FONT=Courier New]Documents in queue   0
Documents indexed    10985658
Index size           100590 MB
Status               idling
Unique words indexed 136600[/FONT]

and in the time its taken to enter that, it now shows

[FONT=Courier New]Index size           100602 MB[/FONT]

The other curious thing is that I only have it set to index two folders!

For now I'm going to kill the strigi daemon, delete  ~/.strigi, restart it and see what happens.

---

### Post by errenay on 2008-05-23
The same here - 4.4 GB for strigi on 15 GB partition for /home. All other files in /home use only about 7 GB!
I have to manually remove strigi-deamon and strigi-applet and delete the entire folder.
TuxLove - how your method works?

---

### Post by nix2ways on 2008-05-23
I removed Strigi from my wife's Kubuntu install long ago. I think you have to ask yourself whether you personally *really* need it. You can find stuff just as easily with kfind. It's installed in Kubuntu, you just need to edit the K menu to manually add it.

---

### Post by TuxLove on 2008-05-25
I added this to Launchpad's bug listing after someone else reported excessive disk usage. The details are here;
[https://bugs.launchpad.net/ubuntu/+source/strigi/+bug/227280](https://bugs.launchpad.net/ubuntu/+source/strigi/+bug/227280)

For the record, stopping Strigi, deleting the ./strigi folder then restarting it didn't help. Within an hour or so Strigi had built a 1.3GB index of 530MB of files! For the time being, the 8.04 release of Strigi should be considered broken.  :sad:

---

### Post by markoloka on 2008-05-29
Same problem here. I participated to that bug report. Hopefully this problem gets fixed soon. I'm running out of space.
Tried: sudo apt-get clean but it helped for few minutes.

---

