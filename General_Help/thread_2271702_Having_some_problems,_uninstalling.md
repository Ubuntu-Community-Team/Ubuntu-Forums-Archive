---
title: "Having some problems, uninstalling"
date: 2015-04-01
forum: General Help
---

### Post by Mark_McDonald on 2015-04-01
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Main Issue
----------------

The main issue at hand is.......I have been able to install and uninstall programs in the past through the Software Centre (SC). 
Now, it seems I can not uninstall anything, like mhWaveedit, or XCFA. 
I go to the SC icon, go to installed icon, Sound/Video heading and click on program to be removed, click remove. I let it go overnight, nothing happens, no progress in the progress icon. Then I click on X to stop it and close it down. I have also tried to download certain programs, same thing, its like it freezes.

I dont know what could have caused this probelm, I tried to download some files to be able to hook up my RC Battery Charger (IMAX B6+), so I could look at charge graphs.
I followed the instructions all the  way to just about the end, and I could not finish the final few steps.  It was all in the Terminal Icon, like old school msdos days, brings  backs some memories. What tripped me up was there were 2 programs, or shall I say 2 different ways of doing it. I chose the wrong choice, with what I got or want to get. Its hard to explain, I know thats pretty broad and generic. I dont really think that could have caused it, but it very well could have.

I also downloaded a few different programs off SC (above mentions and gmusicbrowser) to be able to convert flac music files to mp3 to be able to copy to usb and play on my car stereo deck which has USB slot on the face/deck, the program itself didnt convert the entire song, just the first 15-25 seconds.

Also downloaded 2 games. Kgjo and Mastermind, plus I think a program to change desktop colors.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Secondary Issue(s)
----------------------------

In the past I have had great luck and expirience with Ubuntu 14.04LTS,  there are some quirks getting used to it. 

One of them is when  multi-tasking, sometimes the Files icon will duplicate and have multiple  windows open (indicated by the triangle at left of icon on the icon  verticle strip on left of screen. So on about the 3rd or 4th window that  its openning it brings them all up on screen and I have to close all  but one of them down, then track down the file folder I need again. I think I  could probably try a new interface, I think I can download something off  Ubuntu Software Centre icon. Is that possible? I would prefer to have  it like windows where all the icons are all over the screen where I put  them, instead of all on the left side of screen, and having to move  mouseover to it, then moving it down to get the other icons needed.  Anyway like I said, minor annoyance, if thats the term for it.

Some other issues, with which I suppose is my really ancient old laptop, is I notice sometimes, my mouse will stop working, and I will reboot. Back to normal.
Other times I will be doing something, and the screen will dim down, this tells me its crashing, or stalling is the correct term, I wait for a few minutes and its all back to normal.

So all I use this Dell Inspiron 1525 for is downloading strictly music files. I have tried on occasion to download porn, but I always end up deleting them from downloading and get back to my music files. qBitTorrent is what I use, seems good and all, some are quick downloads others are not, depends on the seeds and such right. High seeds, and/or peers quick I get it.  On the transfers from download folder on c drive to external HD, its only getting 15mb/s which I assume is from the USB 1.0 or USB 2.0 bottle neck. But I can transfer a few GB no problem, never crashes. I can deal with that. 

OK then I go back to c drive, download file, delete everything, qbittorrent download section, delete everything as well. Everything is on the external 2TB hard drive which I have only used up about 336GB, thats a big chunk of tunes, most are at 256 or higher.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I think the ultimate "easy-way-out" but longer in terms of time consuming, is to reinstall Ubuntu, or even try a different platform all together.
What are some of the other platforms that are out there, that are on the more popular side, that is easy for newbies like me to work with. I am sticking with Linux, its a good learning opportunity for me.

---

### Post by sudodus on 2015-04-01
*Oldfred*, our most experienced expert on installing and repairing installed systems, published the following list with command lines, that you run from a terminal window. I added a couple of lines by *zika* (another experienced expert) at the end. Please try them! All of them need ***sudo*** (to get superuser privileges).

```
# Oldfred's command list for cleaning and repairing
 
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

# added zika's tip for problems with hash sum mismatch

sudo rm /var/lib/apt/lists/*
sudo apt-get update

```

---

### Post by Bucky Ball on 2015-04-01
You have a lot of issues outlined in the one post and that can only get confusing. I suggest you stick to one support request per thread and split what you have here to new threads with descriptive titles and in the appropriate forum areas. There's plenty of room here. Good luck. ;)

PS: What I will suggest is if you want something more like Win, try Mate or Xubuntu (or Lubuntu). You can make the desktop a real mess real easily!

---

