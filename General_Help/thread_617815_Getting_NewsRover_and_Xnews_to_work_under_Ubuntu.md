---
title: "Getting NewsRover and Xnews to work under Ubuntu"
date: 2007-11-19
forum: General Help
---

### Post by INFireRedF150 on 2007-11-19
#1.  I am trying to get News Rover to work after the install.  Per another website I found I was able to install News Rover v13.1 under Wine with no problems, and it ran perfectly after the install.  However, just as another website said, but unlike their solution that didnt work, my News Rover will not run since shutting it down after the install.  I have watched script via my Terminal and saw where maybe a hang up was at but after searching all over the web I was not able to get any where.  Has anyone using this program been successful in running it over and over with no problems once installed?   I am using Ubuntu 7.10.  I am a Noob and so I am not too keen on what other specs this forum would normally as of me in order to help me solve a problem.

#2.  I have been able to run Xnews under Wine 0.9.49 just fine except embedded pics dont show up.  I have to save attachments and view outside of Xnews.  This was a nice feature under Windows XP.  I found a site speaking of 5 particular DLL files from XP so I copied those over and made sure that for my Xnews.exe entry in Wine that I had those Library files bound and set "native, bulliten"  but it still wont work, however, all other features of Xnews seem to work fine.  I would use this primarily but News Rover has a great search function to look at all ~109,000 newsgroups that my giganews subscription gets me.

Thanks in advance!

---

### Post by INFireRedF150 on 2007-11-21
I have read where Pan can be altered to allow more than 4 connections.  However, I am unable to find a write up of any kind on what to go after.  Can anyone point me in the right direction?  My newsgroup provider allows up to 10 connections so I would like to take advantage of that. 

Or.  If there is another newsgroup reader for Ubuntu/Linux that has a search function on the server level, not just the newsgroup level, please let me know.

Thank you.

---

### Post by INFireRedF150 on 2007-11-22
Well, I sort of found a solution to my News Rover problem.  It turns out that I have to open Winefile first, find the NewsRover.exe file, and double click it and it will run.  However, I cant run it from the Terminal preceeded by wine.  Xnews runs ok still with the exception of the embedded images not showing up as they do when Xnews is ran under XP Pro.

---

### Post by les-h on 2008-04-11
I use Newsrover v13.1.  To start newsrover, create a link or make a script with:
env WINEPREFIX="/home/les/.wine" wine "C:\Program Files\NewsRover\NewsRover.exe"

This always starts ok for me.  Also alot of people have problems with it not loading after start.  When you do start it go to configuration and in the advanced tab check the option to put in system tray.

I seem to have a problem on text groups where it locks after a couple of minutes, fine with binaries though.

Hope this helps.

---

### Post by les-h on 2008-04-11
P.S change path to yours :)

---

### Post by DonCoyote on 2008-05-02
I have Xnews working on a notebook computer but have been unable to use it on my new desktop because I can't get Wine to work on it.  I put Wine in with Synaptic and it shows up but if you try to do anything with it at all-- including configure it-- the entire system locks up.  I think it must be something to do with the motherboard or cpu hardware because I tried installing on two different disk drives and using both AMD64 and 32 bit versions of Gutsy.  (The processor is a sempron 3400+ with 64 bit instructions intact and the motherboard is Biostar.) The 32 bit installation was from the same disk as I used to install on my notebook.

Has anyone else had this problem or have ideas to fix it?

Don

---

