---
title: "Building Wine on Ubuntu 12.04"
date: 2015-01-03
forum: General Help
---

### Post by Ralph L on 2015-01-03
I installed Wine on my 12.04 system.  I used the latest version available for Precise (1.6.1).  However, I was unable to get the Help file for my game application to work correctly.  When I posted my problem on the Wine forum ([https://forum.winehq.org/viewtopic.php?f=8&t=23905&p=98245#p98245](https://forum.winehq.org/viewtopic.php?f=8&t=23905&p=98245#p98245)), I was told to install the latest version of Wine, and if this didn't work to file a bug report.  Because no Precise version of the latest Wine is available on the ppa, I was told to build one.  [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) contains instructions for building Wine on a 64 bit system and references [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages) for building on a 32 bit system (which is what I have).  This site says to download and execute the script on  [http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh](http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh), by executing ```
sudo sh ./install-wine-deps.sh
```.  When I execute this script I get ```
E: Unable to locate package libhal-storage-dev-dev
```  It seems to me that the missing package has a strange name ending in "-dev-dev".  

Does anybody know if libhal-storage-dev-dev is a real package, or did someone just make an error in the script?  I asked this question in the Wine Forum, and nobody knew the answer. They suggested that I ask here.  I guess I could just delete the extra "-dev" and see if the build worked, but I thought I would try to get an answer first.

---

### Post by DuckHook on 2015-01-03
It's hard enough configuring WINE to work at the best of times. Are you really sure you want to build from source? Agreed that the version in the Precise repositories is old. So try adding the PPA instead. You have your choice of stable or beta (bleeding edge). This should be enough to keep even the most fanatically current user satisfied. Instructions [here]("https://www.winehq.org/download/ubuntu").

I have my doubts that your problem is the age of your version of WINE. It is notoriously hard to get Windows apps to work in WINE, and you should check the [WineHQ database]("https://appdb.winehq.org/") to see how your game is rated. Anything less than "gold" is not worth installing, IMO.

---

### Post by Holger_Gehrke on 2015-01-03
I googled a bit about your problem and found your posting on the wine-forum. Seems like it's really not wine itself that's giving you grief but winhelp.exe or winhelp32.exe. The ones included with wine are attempts at reimplementation of these tools, broken in a lot of ways and fixing them is a low priority since even windows doesn't use hlp files anymore. If you own a windows license you could try to use the original windows help programs.

---

### Post by Ralph L on 2015-01-04
Thanks for the response.  Yes, my problem is with handling the help file.  What are the windows xp programs that I would need to transfer to ubuntu?

Thanks
Ralph

---

