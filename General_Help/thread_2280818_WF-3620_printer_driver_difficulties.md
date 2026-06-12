---
title: "WF-3620 printer driver difficulties"
date: 2015-06-02
forum: General Help
---

### Post by lusbyclark2 on 2015-06-02
I have two PCs in my house, one is a 64 bit HP Pavilion with Windows 7 and the other a 64 bit generic PC with Ubuntu 14.04.  I also have an Epson WF-3620 printer purchased seven or eight months ago.  All of these devices are exclusively WiFi systems.  The WF-3620 printer works fairly well with the Windows 7 PC,  but ever since I brought it home I have tried and tried to get it to work with my Ubuntu PC.   At first and for a long while I thought it's difficulties were related to the lack of a suitable Linux driver.  I was advised to try CUPS, so I tried CUPS - didn't work!   This last week I discovered that the Epson Driver Download site had a listing for a Linux compatible driver for their WF-3620.   Yesterday I finally managed to work my way through all the parts and pieces of the complicated downloading and installing instructions.  When I tried it, the results were no better than CUPS, i.e. didn't work.  By the way, I already am familiar with the August 11, 2014 **Loutchoa** post and its several replies.  Indeed, I was guided, in part, by these postings. 

At this point my first issue is ridding my Linux PC of CUPS.  I tried the usual **sudo apt-get remove  --purge** process but there appears to be a residue of several files of programs and documents.   I later found a .deb file on the Epson Linux drivers website, and after downloading  and installing it, my Unix shell window seemed to say it had successfully accomplished the installation.   So far nothing has worked.  I usually get an error message that claims my PC "Could not start the printer".   I am beginning to wonder if this just might be a lost cause.  Is it possible that once a Windows driver is imposed on the printer, the printer becomes unresponsive to a Linux driver?  

Someone responding to **Loutchoa's**  post suggested a different driver than the driver I originally downloaded, but it is a .tar.gz rather than a .deb file.   What am I to do with such a file?     
If someone has a similar two PC/Epson printer set-up and has been successful getting it to work, I would like to know how you managed to get the whole system functioning together.   On the other hand, if someone has tried in vain to get a similar system working, I would like to hear from you as well.

---

### Post by Geoffrey_Arndt on 2015-06-03
Well, let's try to clarify and then install the driver:

1).   Don't try to uninstall CUPS (Common Unix Print Service).   It is used as and if needed by various oem driver packages.   It usually is installed by default - - that's a good hint not to mess with it.

2).   If not already installed, install the "stand-alone' deb file installer "gdebi".   Get it from the Ubuntu Software Center or Synaptic package manager.   If Synaptic's not installed,  . . install it (either from Ubuntu Software Center or via command line).

3).   Get the deb "files" (more than 1 as you want scanner to work, etc.) from here:  [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

4).   The driver files will download to the downloads folder.  I like to create a "StandAlone Debs" folder (name it what you want).   Move the files there.   

5).   Right-click the primary printer diver (start installing in the same order as the downloads site matrix).   You'll be prompted to select installer program, in this case, select gdebi from the options list.   Do all files this way.

6).   Go to Ubuntu Settings, Printer, and then add the printer as indicated . . . I don't recall all the screens, but you should have a print test page.

7).   After install, you can also setup the printer for Cloud Print via the Google site . . . instructions are there . . . pretty simple to do in most cases.

PS:  Every Epson Workforce printer I've tried has worked quite well in linux.   My current model is the Epson Workforce 645 . . . does a great job, everything worked out of the box - - didn't need to do any of the above other than adding the printer from the Ubuntu Settings > Printers dialog.  So, the steps listed above "assume" you've already tried the normal "add printers" method to do a search-install of printer drivers.   Many Epson & HP printers are installable without need of downloading drivers

---

### Post by lusbyclark2 on 2015-06-04
Twice now I have tried to execute the procedure that Mr. Arndt provided in response to my cry for help and twice, after more than two hours, the execution process seem to come to halt, although the orange *worm* continued to go back and forth incessantly (a progress bar would have been nice), making me believe the process was still underway.  Actually this process may have come to its halt within the first five minutes after its initiation.  A few minutes ago, just before I killed the second attempt, it occurred to me that there may well have been an important message on the Unix window at the end of all of the notifications of previous progress: "CUPS stop/waiting".   Is it possible that the already installed CUPS package caused the installation of the Epson printer driver package to hang up?  If any of the 200+ persons reading this post have also experienced these difficulties it would be good to hear from you, particularly if you found a way around the "gdebi" failure. 

By no means am I blaming Mr. Arndt.  For the most part, his suggestions  have proven to be quite helpful, particularly the "gdebi" file installer  worked quite well at the outset of the installation process.  A lot  easier than going through all of the command line stuff.  


Also I must report that the driver I pulled out of Epson's hat is identified as epson-inkjet-printer-escpr_1.4.5-1lsb3.2_amd64.deb.  If someone out there knows this to be the incorrect driver, I would appreciate receiving a reply identifying the correct driver.

I have now begun to wonder if a complete reload of Ubuntu 14.04 is now required.  Any suggestions?

By the way, in my initial post of this thread I asked is it possible that once the Epson WF-3620 has been given a Windows driver, it can not accept a Linux driver thereafter.  Of the many people looking at this post, no one has given me an answer to this question.  

As for needing to download and install scanner drivers, I really do not need these drivers, since the printer and this, my Linux PC, are on separate floors of my house.  The printer and my wife's Windows 7 PC are setting side-by-side in a small room on the first floor and my Linux PC and I are consigned to an even smaller room in the basement.  It is not to be thought of as a luxurious man-cave.  No not at all, its more like a dank dungeon without chains.

---

### Post by Geoffrey_Arndt on 2015-06-04
I don't know if a reinstall is needed, but it certainly wouldn't hurt to have a clean environment, and then just try adding the printer and seeing if Ubuntu can download the correct driver (that does work for some Epson models).

Re use or install of a Windows driver for the printer - - there is no connection between the two OS's re windows software affecting "installability" of a Linux/Unix coded driver.

I like to peruse [http://www.openprinting.org/printers](http://www.openprinting.org/printers).  Sometimes they don't have the drivers but will link to another site (such as Epson's) for drivers that are not yet deemed stable enough to put on openprinting's site.

Here are a couple other suggestions if a reinstall of the official drivers from Epson (via gDebi or the USC) hang:

>   Sometimes finding and installing a _similar driver_ will work (a driver with a similar model number/series, , , 90% plus of  the code is identical).  I've even seen HP printer drivers that successfully run Epson printers (really).

>   As a last resort, there is a small company in Germany that build excellent drivers for many Linux printers . . and I see your specific printer is available.   These are not free however (usually the cost is around 29-39 USD or in that area).  The company is "Turboprint" - - here's a link:  [http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Epson_WorkForceWF3620](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Epson_WorkForceWF3620)

PS:   I've always had best results in installing printer IF the printer is "initially" connected to the linux PC via USB print cable.   Then afterwards, I move the printer to remote local and connect wirelessly.

---

### Post by manuel36 on 2015-10-20
I have the same printer and the same problem.I do not get it to work on Xubuntu 14.04. I tried 5 different computers with Xubuntu 14.04, and does not recognize the printer. The printer works well with Windows 7.

 I tested the controller created by TurboPrint and neither works.

 I think the file that comes with the driver epson-inkjet-printer-escpr_1.6.0-1lsb3.2_amd64 not right, if you select and unzip the ppd not work correctly, the system recognizes it as an HP printer

 I sent a query to Epson, and they say I try to install the version 1.0.0 of the ESC / P-R driver, but this version does not exist in the download page of wf-3620

 Does anyone have any idea you could do?

---

