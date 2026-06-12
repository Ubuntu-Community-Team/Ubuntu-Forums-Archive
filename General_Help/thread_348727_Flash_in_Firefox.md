---
title: "Flash in Firefox"
date: 2007-01-29
forum: General Help
---

### Post by bigjack on 2007-01-29
I can't get Firefox 2.0.0.1 to see Flash.  After visiting sites that said I didn't have the latest version of Flash, I downloaded the .rpm version from the Flash site.  Converted to .deb with Alien and used GDebi Package Installer to install flash-plugin_9.0.31.0-1_i386.deb.  When I look at files insta lled with Synaptic Package Manager, the updated flash-plugin is listed.  If I view aboutplugins in Firefox, Flash is not listed.  Also, when returning to web pages with Flash, I still get the message to upgrade to the latest version of Flash.  I've rebooted, but no luck.

---

### Post by j19sch on 2007-01-29
Here's what worked for me:
1. go to a webpage with flash
2. click the Firefox message that says the flash plugin wasn't found
3. let Firefox search for the Firefox flash plugin, download and install
4. restart Firefox.

If anyone can tell me why you need to install a (external) plugin-package AND the (internal) Firefox-plugin, please do. There are people who'd like to know.:)

---

### Post by taurus on 2007-01-29
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by flossgeek on 2007-01-29
Go to site: [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Download the .tar.gz file. Right click on it and extract it, inside the folder you should see a file named libflashplayer.so. You need to move this file to the firefox plugin directory. I presume the file is on the desktop!

Make sure you are on Desktop in terminal

cd Desktop

then move file

sudo mv libflashplayer.so /usr/lib/firefox/plugins

Resart Firefox and flash will be running...

---

### Post by bigjack on 2007-01-29
That's what I did in the first place.  But no luck.  I have solved the problem.  For some reason there was no link to libflashplayer.so in usr/lib/firefox/plugins.  So I copied libflashplayer.so from usr/lib/flash-plugin to /usr/lib/firefox/plugins.  (Did cp in terminal as sudo.)  Now the latest version of flash works in Firefox.

---

### Post by strabes on 2007-01-29
the /usr location is the global location for plugins (for all users) the /home one is just for your user

---

