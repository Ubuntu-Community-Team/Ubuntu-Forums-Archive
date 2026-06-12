---
title: "SugarCRM gone Sour"
date: 2007-11-07
forum: General Help
---

### Post by jazzyphonic on 2007-11-07
Hi  Linux Lovers,

First let me note that im no techy so i dont know alot of techy jargon.  However im working on that, hopefully someday soon we could talk at per.  Now im having a problem with my new Gutsy Gibbon installation.  I migrated from windows recently and im having a blast.  However we recently installed sugarcrm at the office and while i can access it from my box, i cant view charts at all. This is slowing down alot of work.  I can use the crm comfortably from a windows box but not from my laptop.  I understand that the charts are displayed in flash.  I have installed gnash swf viewer but it hasn't been much hlep.  Does any one here have an idea what i can do.   Im lost please help.

Jazz rules

---

### Post by jazzyphonic on 2007-11-08
Hey anyone there?

Please help.  Im like so stuck.

---

### Post by jazzyphonic on 2007-12-10
Hi JazzyPhonic,

Since no one is responding to this :mad: i figured it out myself and thot id post a how to after some research.
 
 The problem is not with sugarCRM or Ubuntu OS but rather with Firefox and  flash player, uninstall gnash swf and player/shockwave  plugin in firefox ( you can get  info about this by typing "about:plugins" in your firefox address bar")  after that i go ahead and "apt-get install ubuntu-restricted extras"  ( you have to enable medibuntu packages in synaptic to do this.}  Then download Flashplayer 9 and follow the instructions below. for the download use the link below

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)


  1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu

This should also address the issues of the computer hanging when streaming videos.  Its kinda nice to learn Hands on like i did :):lolflag:


jazzyphonic

---

