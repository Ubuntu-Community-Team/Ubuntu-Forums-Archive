---
title: "Problem with Grub"
date: 2007-06-29
forum: General Help
---

### Post by nexgen on 2007-06-29
Ok ill start from the top i was interested in trying linux on my pc that has Windows XP installed so i wanted to try a dual boot so i download and installed ubuntu it worked alright grub worked fine i could boot into XP or Linux just fine then i saw other distros i wanted to just try out so i thought i would just boot gparted and just delete where linux is and just resize my windows section back to it original size before i installed linux.

  ok i did restarted and bam i get a grub error i thought no big deal ill just reinstall ubuntu again to fix the stuff but now...i get an error when i try to partition my drive again with the ubuntu installer and gparted it just dosent do it and pops up a error so now im screwed (at least i think) i think i can do i full install of ubuntu and get rid of XP since i have a new windows vista notebook i can live with ubuntu on my 3yr old desktop.

 PROBLEM... i have about $200+ worth of stuff i bought on iTunes about 60gb+ that silly me don't have back up(i have all my library on my iPod though)!  im running off the ubuntu live CD right now and saw i can mount my XP drive with my iTunes folder and file right there and i wanted to ask can i just go and buy another drive or external drive plug it in and live cd ubuntu will detected and allow me to transfer the iTunes folder to the external drive so i can just take to my notbook? 

thats was the main question but i made it a long read to explain what i did to begin with grub and all to see if theres a way i can still save XP and some how fix Grub.

When i opened what i think is the boot file for grub its blank so i think thats where my problem is ^_^ and like i said i cant resize my HD i keep getting an error the 4 times i tried. Also im a noob at linux this was the first time i tried it and i happened to mess it up.

---

### Post by mikewhatever on 2007-06-29
There are several options to solve the problem.
1. you can fix the mbr to boot windows again using Windows install cd or any other tool, super grub cd for example. Personally, I think this is the way to go.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console)
2. what was the error message you got at the partitioning stage?
3.you can use the Ubuntu install cd to pull data from the hdd to some external storage. The last option to consider, since it requires some command line knowledge.

Just a friendly advice, next time you want to try another distro, do not install, use the live cd.

---

