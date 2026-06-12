---
title: "Advice wanted on media center partitions"
date: 2008-04-29
forum: General Help
---

### Post by steelshivan on 2008-04-29
I would like advice on how to partition my (soon-to-be) media center PC.  I will be dual-booting Vista 32-bit and Linux Ubuntu.  I will have all Vista stuff on a 160GB drive, and all Ubuntu stuff on a 500GB drive.  Will plan on using MythTV in Ubuntu for all my media center stuff.  Ubuntu will be my "main" OS for everyday stuff, in addition to the media center thing and holding the movies, shows, etc.  Vista will be mainly for any gaming I do, although not too much of that.

I would like other opinions on how to setup my Ubuntu partitions on the 500GB drive.  Thanks.

---

### Post by MaddMatt on 2008-04-29
Sounds like a rad setup. I started my system dual-boot but eventually I didn't like having any of my files locked up into windows, so I got rid of it and replaced it with a VMware version, which works really well if you have extra horsepower. Here's a great tutorial if you're interested. [http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_run_Windows_with_VMware_Player_in_Linux_for_free](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_run_Windows_with_VMware_Player_in_Linux_for_free)

My one recommendation which has saved me incredible amounts of agony: 
have /home on it's own partition! (or drive if you have a spare) That way if your system goes nuclear, you can reinstall and have all of your settings and documents saved. You can also change the root directory to be /home/root or use a link so that the root preferences are saved as well (but don't get into a habit of logging in as root. Bad mojo.)

For redundancy I keep my videos and downloads and other intensive space things on 1 partition, my music on anohter drive and home seperately. That way if something goes boom I don't lose everything ("don't keep your eggs in one basket" they say)

The downside to using different physical partitions? If you decide you need to allocate space differently, it can be a pain with all of the partition resizing, etc, so make sure you have plenty to start with.

Tip: the / parition with all of your system files really only needs to be about 10-12 MAX. I have mine set at 12, and that's huge, right now I'm only using 3gigs with the fresh Hardy install. 

So, to sum up: 
500gb disk: 
/ - 10gb
/home: 20gb (if you keep documents, etc. there and you're the only user)
/storage or /media/videos, whatever you want to call it: the rest of the drive. If you are an audiophile and want seperate music / videos & photos, then make your music directory 80gb or so. I also use ReiserFS for music, because it seems to journal better than EXT3, but you can learn more about the filesystem wars here:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Hope that helps!

---

### Post by steelshivan on 2008-04-29
Thanks for your response, sounds like a plan. :)

---

