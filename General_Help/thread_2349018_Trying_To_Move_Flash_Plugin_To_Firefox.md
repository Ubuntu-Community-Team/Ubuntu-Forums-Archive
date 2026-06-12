---
title: "Trying To Move Flash Plugin To Firefox"
date: 2017-01-10
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-01-10
I have this plugin in my Downloads folder and I'm trying to move the libflashplayer.so to firefox-addons which is here /usr/lib/firefox-addons.  My problem with this explanation is  I keep getting errors.  Can you please tell me know how to complete this?  ```
based on your Linux distribution and Firefox version
    o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
        + cp libflashlayer.so <BrowserPluginsLocation>
    o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
        + sudo cp -r usr/* /usr
```

---

### Post by ajgreeny on 2017-01-10
I hope you're not using 15.10 as shown in your user information, as that version has lost all support and your OS will now be unprotected and get no updates to any packages.

If you are on a supported version eg, 16.04, 16.10, or still on 14.04, you can enable the canonical-partner repos and then update the cache and install **adobe-flashplugin** in the usual way; there is no need to do as you are trying to, and install a downloaded file direct from Adobe.

However, as you have the libflashplayer.so file you could see if moving it to ~/.mozilla/plugins/ gets it working; it used to, but I have had no need to mess around trying that for a very long time now. 

You will need to create the ~/.mozilla/plugins/ folder as it is not available by default and the flashplugin will be available only to your user, no others if there are any on your machine, and the plugin will not be updated automatically as it will if you install the adobe-flashplugin package.

---

### Post by shane_faulkinbury2 on 2017-01-10
I using 16.04 LTS and this is what my Other Software in Software & Updates looks like.  The strange thing is I don't see anything about Flashplayer in it.

---

### Post by deadflowr on 2017-01-10
> **shane_faulkinbury2 said:**
> I using 16.04 LTS and this is what my Other Software in Software & Updates looks like.  The strange thing is I don't see anything about Flashplayer in it.

adobe-flashplugin is a package in the Canonical Partners repo.
flashplugin-installer is a package in the multiverse repo.

the adobe-flashplugin differs from the flashplugin-installer package by being able to install both the firefox-npapi and the google-chrome-ppapi flash versions.
the flashplugin-installer package only installs the firefox-npapi version. Or at least that's been the case so far.

---

### Post by shane_faulkinbury2 on 2017-01-10
Well the original question was how do I move the firefox-npapi to to the firefox-addons?  No explanation is given and when I try to use the cp command as stated I get errors.

---

### Post by ajgreeny on 2017-01-10
On my 16.04 system the **libflashplayer.so** file sits in **/usr/lib/adobe-flashplugin/libflashplayer.so** so see if moving it there helps you with ```
sudo cp Downloads/libflashplayer.so /usr/lib/adobe-flashplugin/
```
You probably keep getting errors either because you are not copying as root, or because the destination folder is non-existent.  Those instructions are a general idea of what you have to do, but the details of the destination folder will probably vary in different distros; in Ubuntu the **libflashplayer.so** file needs to be where I say above.

I repeat, however, that you are trying to do this in the most difficult way. You already have the canonical-partner repos enabled so just install adobe-flashplugin as I suggested in post #2 and the job will be done.

---

### Post by shane_faulkinbury2 on 2017-01-10
Okay, I got that done, now what does this mean?  ```
Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
        + sudo cp -r usr/* /usr
```

Does it go in this folder and how do I get it in there?

---

### Post by Dennis N on 2017-01-10
I have seen these same directions you display in the readme.txt file in the flashplugin's tar.gz file. 

> Okay, I got that done, now what does this mean? "Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type: sudo cp -r usr/* /usr"

The source **usr** folder in the command is the one you extracted from the tar.gz archive. What it does is copy contents of the **bin**, **lib** and **share** folders inside the source usr folder to /usr/bin, /usr/lib, and usr/share in your file system.

If you accept the risk and decide to proceed, It will be interesting to see if it works. Let us know if you succeed.

The directions in the readme.txt seem to be generic instructions for any Linux (not just Ubuntu). If your objective is to get the newest flash version working, I suggest you follow ajgreeny's suggestion in post #2. Much easier. I don't see any good reason to install the flash plugin from a tar.gz archive unless your Ubuntu version is no longer supported from the repositories and you couldn't get it any other way.

---

### Post by shane_faulkinbury2 on 2017-01-10
I had to uncheck the and recheck the canonical-partner repos to reload and I got errors.  I however didn't see anything about the flash-plugin so we'll see.

---

### Post by mc4man on 2017-01-10
You could just simply put in ~/.mozilla/plugins folder & be done with it.
(- create plugins folder if not there

---

### Post by shane_faulkinbury2 on 2017-01-11
Okay, here's the easy way I fixed this.  I installed and opened Opera and went to their how to section.  In it I found how to install Flash Player for Opera.  I searched for Ubuntu Software Center and found I did not have it.  So I opened Ubuntu Software and put in to search for Ubuntu Software Center and it found it.  I opened it and put in a search for Adobe Flash-player and it found it.  So installed that and everything is working on Opera and Firefox,  :p

---

### Post by Dennis N on 2017-01-11
Yes, the Ubuntu Software Center offered two items that can cause confusion. (Note - I am looking at the (Xubuntu) 14.04 version, and can't say what the case is in (Xubuntu) 16.04, where U.S.C. it is not installed by default.)

The package described as "Adobe Flash Plugin" will install flashplugin-installer, while a package described as "Adobe Flash Player Plugin" will install adobe-flashplugin.

The choice now recommended for Firefox and Chromium is to use the adobe-flashplugin package, so the user would need to install the Ubuntu Software Center item "Adobe Flash Player Plugin" and not the other one. On the other hand, if you had used the terminal, you need to use the package name, not a descriptive name, so **sudo apt-get install adobe-flashplugin** would get that same package.

(Note: "Adobe Flash Player Plugin" will not show up at all in U.S.C. unless Canonical Partners repository is enabled first, and you then log out and in).

---

### Post by shane_faulkinbury2 on 2017-01-12
So here's what I did to resolve this.  I installed Opera, went to their  help section and looked for Flash.  I found a help session that said  install Shockwave Flash from the Ubuntu Software Center.  I didn't have  that on my computer so I opened Ubuntu Software, found it, downloaded  it, found it and installed.  I'll check it out when I get home from by  business trip!

---

### Post by shane_faulkinbury2 on 2017-01-19
But my home folder doesn't have a Mozilla folder in it.

---

### Post by #&amp;thj^% on 2017-01-19
Show hidden files...it is .mozilla

---

### Post by bearlake on 2017-01-19
To show hidden files just hit "Ctrl + H" at the same time.

---

### Post by shane_faulkinbury2 on 2017-01-25
I'm taking this class and trying to view the video and the page tells me I need to install the Flash plugin. So I choose and downloaded the flash_player_npapi_linux.x86_64 file to my Downloads folder.  I'm trying to move the flash_player_npapi_linux.x86_64 folder to my /usr/lib/firefox-addons folder using my terminal.  What command should I use?

---

### Post by shane_faulkinbury2 on 2017-01-25
Here's the write up on it!

```
Adobe Systems Incorporated
Flash Player for Linux
Version 24.0.0.194

Adobe recommends that all users upgrade to the latest version of Adobe Flash 
Player for the most recent features, bug fixes, and security fixes.  
For more information on the new features in Flash Player, please visit 
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/).  For more information on system 
requirements, fixed issues, and known issues, see the release notes at 
[https://helpx.adobe.com/flash-player/flash-player-releasenotes.html](https://helpx.adobe.com/flash-player/flash-player-releasenotes.html)

To confirm which version of Flash Player you have currently installed, see 
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/). Users should only install 
Players that have been downloaded from trusted sources, such as 
[https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/)

Your use of this player is governed by the Adobe End User License Agreement 
found at [http://www.adobe.com/legal/licenses-terms.html](http://www.adobe.com/legal/licenses-terms.html)


Privacy
-------

Adobe is committed to preserving the privacy of end users. For more 
information on configuring Client-side privacy visit the Settings Manager 
Documentation: [http://www.adobe.com/go/flashplayerhelp](http://www.adobe.com/go/flashplayerhelp).


Installation instructions
-------------------------

Installing using the plugin tar.gz:
    o Unpack the plugin tar.gz and copy the files to the appropriate location.  
    o Save the plugin tar.gz locally and note the location the file was saved to.
    o Launch terminal and change directories to the location the file was saved to.
    o Unpack the tar.gz file.  Once unpacked you will see the following:
        + libflashplayer.so
        + /usr
    o Identify the location of the browser plugins directory, based on your Linux distribution and Firefox version
    o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
        + cp libflashlayer.so <BrowserPluginsLocation>
    o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
        + sudo cp -r usr/* /usr

Installing the plugin using RPM:
   o As root, enter in terminal:
          + # rpm -Uvh <rpm_package_file>
          + Click Enter key and follow prompts

Installing the standalone player:
   o Unpack the tar.gz file
   o To execute the standalone player,
          + Double-click, or 
          + Enter in terminal: ./flashplayer


Uninstallation instructions
---------------------------

Manual uninstallation (for users who installed the plugin via Install script):
   o Delete libflashplayer.so binary and flashplayer.xpt file in 
   directory /home/<user>/.mozilla/plugins/

RPM uninstallation:
   o As root, enter in terminal:
          + # rpm -e flash-plugin
          + Click Enter key and follow prompts


Technical Issues and Reporting Bugs
-----------------------------------
 
The Adobe Support Center at [https://helpx.adobe.com/support.html](https://helpx.adobe.com/support.html) is a 
free online resource for support and troubleshooting information. 
Bug reports may be submitted at [http://www.adobe.com/go/wish](http://www.adobe.com/go/wish). 
To allow us to investigate reported bugs, please include the following 
information:
 
1) Platform and version
2) Browser version
3) Reproducible steps including a URL to the web site where the problem 
   was encountered.
 
If we need further information about a bug, you will be contacted. An 
automated reply will be sent to assure you that we have received your 
bug report. Due to the volume of mail received, we are not able to 
individually respond to each report.
```

---

### Post by Kris_M on 2017-01-25
Uh, something changed from when I was on Ubuntu 6 months ago, and now. I used to have to install flash23. Flash 24 now comes with FF.

---

### Post by &amp;KyT$0P# on 2017-01-25
Again?

[https://ubuntuforums.org/showthread.php?t=2349018](https://ubuntuforums.org/showthread.php?t=2349018)

---

### Post by shane_faulkinbury2 on 2017-01-25
Thanks, but like last time nothing.  :(

---

### Post by oldos2er on 2017-01-25
Your other thread is marked 'Solved.' Why are you asking the same question again? We tend to frown on duplicate threads.

The correct command would be ```
sudo cp Downloads/flash_player_npapi_linux.x86_64 /usr/lib/adobe-flashplugin/
```

---

### Post by shane_faulkinbury2 on 2017-01-25
Sorry about the double post, but that gives me the same thing.

---

### Post by oldos2er on 2017-01-25
Please copy and paste terminal output into your post here rather than posting screenshots.

And again, why are you asking the same question when the other thread is marked 'Solved'?

---

### Post by shane_faulkinbury2 on 2017-01-25
Like I said, I thought you solved it so I marked it solved, but when I tried to launch the class again today I saw it didn't work on my desktop.  However, for some reason it works on my laptop fine and I've never done a thing to it!  :confused:

---

### Post by howefield on 2017-01-26
Threads merged.

---

