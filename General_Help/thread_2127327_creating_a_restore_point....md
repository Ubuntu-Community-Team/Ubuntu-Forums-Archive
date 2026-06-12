---
title: "creating a restore point...?"
date: 2013-03-19
forum: General Help
---

### Post by blackadam on 2013-03-19
(New to Ubuntu)
 
I just installed a fresh copy of 12.04 on my desktop plus some aps i had installed .  I had wanted to know if it was possible to create like a default restore point as to how my pc is setup now? (well at least i wasn't able to find the option)  Someone recommended that i can use aptoncd and burn my aps and settings on it and in-case anything ever happens i don't have to install everything again from scratch. I wanted to know if there was another option or if that best way to go about saving everything

---

### Post by ibjsb4 on 2013-03-19
There are several different ways to backup installed packages and configuration files.

I use Synaptic Package Manager to backup all installed packages.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages+synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages+synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=)

Many more ways here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en&siteurl=)

Backing up configuration files is a bit harder.  Most configuration files are located in your home folder, but not all.  Heres a place to start.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+system+configuration+settings+files&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+system+configuration+settings+files&as_qdr=all&sa=Google+Search&lang=en&siteurl=)

---

### Post by arpanaut on 2013-03-19
No restore points w/Ubuntu but Clonezilla will work well
[http://ubuntuforums.org/showthread.php?t=2099089&p=12426264&viewfull=1#post12426264](http://ubuntuforums.org/showthread.php?t=2099089&p=12426264&viewfull=1#post12426264)

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Mark Phelps on 2013-03-19
Just so you know ... if you want something in Linux that works like System Restore does in Windows -- then you've probably been mislead to believe that System Restore is like a time machine, in that it restores your COMPUTER system back to a previous point in time.

Sadly, it does not do that.  Instead, it restores the Operating System, and select components, to an older version.  Your files and data are not touched, and also, NOT restored.

So, if you are using System Restore on Windows in order to completely restore your Windows PC to a previous time, you should consider an alternative (like Macrium Reflect, or Acronis Backup and Recovery) that really do image off the PC.

---

### Post by blackadam on 2013-03-28
Thanks you guys,  @ mark what you described was exactly what i had thought a restore point was thanks for clarifying.  i will definitely look at  the software you mentioned. 

Is there a way since i have 2 computers to if i log into 1 it could see what apps i have installed and either download them automatically or have a pop up saying hey you downloaded blah do you want to download them here as well?

I'm asking because i recently saw this [http://www.youtube.com/watch?v=_mB2sY9NNOQ](http://www.youtube.com/watch?v=_mB2sY9NNOQ) (1:45 i think is where the canonical person speaks) and it got in really motivated to try and switch all mh electronics to open source

---

### Post by oldfred on 2013-03-28
I have not used any of these.

 Offline Updates:
[https://launchpad.net/keryx/+download](https://launchpad.net/keryx/+download)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

I prefer clean install, but backup /home, any system file I manually edit I copy into /home so it gets backed up, and export a list of installed applications. But I have high speed Internet so install & download updates and applications is quick. 
      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

