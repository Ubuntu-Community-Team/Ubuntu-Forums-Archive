---
title: "Possible issue with privileges or sudo after boot sector repair."
date: 2015-07-07
forum: General Help
---

### Post by michael-mody on 2015-07-07
So basically the problems started when I reinstalled boot partition for Ubuntu a 14.04.2 LTS. Installed dual boot windows, installed a wifi extender (driver only windows compatible), now I can't connect to the internet, except through one connection. I also have to open dropbox and bluefish editor with sudo from terminal if it is to work.

 

 So a long story.  I installed windows on a separate disk from Ubuntu which had the boot partition. It deleted boot partition (grub2) accidentally, reinstalled using Ubuntu boot rescue (live disk). Running Ubuntu 14.04.2 LTS and Lubuntu together.  Separate /home on a seperate disk. Boot was on 3[SUP]rd[/SUP] spare disk... I know!  So I installed windows on this spare disk because I needed it to try to install and set up a Belkin wifi extended (absolute rubbish by the way, don't buy one).  In windows changed network settings to point to a fixed address in order to get the Belkin to work. Changed it all back. Then went back to Ubuntu after fixed boot partition back to disk with Ubuntu.  I discarded the wifi extender as it does not work, so all my wifi settings are the same as before.

 

 I could connect to the network.  Icon shows connection etc, however when I open a browser it couldn't connect to the internet.  Desperate for a solution, I thought that maybe a configuration had changed in my user profile.  I logged out and logged into a different profile I use for work, connected to my wireless. Hooray, connection good, I don't log out from this profile, but log back in the original one which has the problems, forcing it to share the working connection I've just established.  Wala, all good.
 

 However, I then notice that any of the other connections do not work.  I use Wifi tethering from my mobile phone and also a USB tether.  This now does not work. I tried someone else’s tether, this also does not work.  However, both these work with other PCs etc.

 

 Then while using tethering, still unable to connection the internet (Chrome or Firefox), however skype works! So Skype connects to the internet but not the browsers.
 

 I also found Dropbox no longer works unless I open it from terminal with sudo.  Bluefish editor also crashes unless I open it with the sudo command.  So I think there is something wrong with the root user or privileges after I performed a grub boot rescue.
 

 Launching Dropbox from terminal without sudo gives:


 ```
IOError: [Errno 13] Permission denied: '/var/lib/dropbox/.dropbox-dist/dropbox-lnx.x86_64-3.6.8/futures-2.1.3-py2.7.egg/EGG-INFO/top_level.txt' 


``` 

 And Bluefish:

 

 ```
** (bluefish:7322): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-R1KG49aC5A: Connection refused 

 error reading list 14 Error opening file: Permission denied 
  
 ** (bluefish:7322): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions 
  
 config file migration error 1:Error opening file: No such file or directoryerror reading list 14 Error opening file: Permission denied 
 error reading list 14 Error opening file: Permission denied 
 cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb 
  
 ** (bluefish:7322): WARNING **: save stringlist error 14 Error opening file '/home/michael/.bluefish/session-2.0': Permission denied 
  
  
 ** (bluefish:7322): WARNING **: save stringlist error 14 Error opening file '/home/michael/.bluefish/session-2.0': Permission denied 
 


``` I would like to correct it without having to do a re-install.  Any help would be greatly appreciated.

---

### Post by michael-mody on 2015-09-11
Well, in the end I decided to re-install.  I thought it was going to be complex or difficult, actually it was surprisingly easy!  Since I had /home on a separate partition on a separate disk, things were sweet.  I decided to try old Mint again after many years... and boy was it easy to reinstall and keep all my data. First I made sure I had my Home directory backed up, then I reinstalled, selecting /home without the formatting directory part ticked and when I restarted and logged in... voilà! It was all there, my emails, website bookmarks etc... You couldn't ever do that with windows!  Took no more than 30 minutes.

---

