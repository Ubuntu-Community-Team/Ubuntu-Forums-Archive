---
title: "trouble viewing some web pages"
date: 2008-03-04
forum: General Help
---

### Post by doondoon on 2008-03-04
First let me say I am using the Firefox and Adobe flash player plugins. I am also running Gutsy. Some of the websites I have tried to view don't show some sections or don't show at all. For example [here]("http://www.oneill.com") is the website I get some of my surfing gear(the kind you do in the ocean). I tried to get some info from the website as far as what kind of flash player they were using or what may be incompatible between us. Can you look at it and tell me what I need to do?

---

### Post by erginemr on 2008-03-04
How did you install the flash player plugin?

---

### Post by empthollow on 2008-03-04
I have not problem viewing that site on gutsy with firefox and the adobe flash plugin.  I downloaded directly from adobe and used their installer.

---

### Post by jsedwards on 2008-03-04
I have had a lot of trouble with Firefox and Adobe flash player on Gutsy.  When I first installed 7.10 it would hang as soon as I tried to view a video on YouTube.  I searched in this forum and tried a few things and nothing seemed to fix it.

Then later I tried it again and sometimes I can watch a video, or two or three or four and it works fine for a while, but eventually it will hang Firefox and I will have to kill it.

A couple of days ago, I went to my bank's web site which has a flash video on their home page and it hung there.  It hung several times and I had to keep killing Firefox.  Finally it worked ok and I was able to log in.

That said, I went to the web page you listed and it worked fine for me.  However, with my experience I suspect that if I kept trying it, it would probably fail at some point.

I'm sorry I don't have a solution for you.  I viewed YouTube and other Flash stuff all the time with 7.04 and NEVER had a problem.  Flash on 7.10 has been really flaky for me.

---

### Post by erginemr on 2008-03-04
There are basically two ways to install the Flash plugin: 

1. To visit a Flash enabled site and let Firefox install it as a plugin, or to go to Synaptic and install the package "flashplugin-nonfree".

2. To go directly to Adobe's web site, download the installer package and install from it.

Did you try both methods?

---

### Post by doondoon on 2008-03-05
nonfree like beer?
I haven't tried it from the website but won't "sudo apt-get install" do the same thing?

---

### Post by erginemr on 2008-03-05
AFAIK, the two methods I gave you install two distinct versions. In my own experience, the installer from Adobe performed better than the one from the package "flashplugin-nonfree". 

So, it is worth a try.

---

### Post by Irony on 2008-03-05
I installed the thing from here;

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

It puts a 6.7 MB program in;

```
~/.mozilla/plugins
```

It works on the surfing site.

---

### Post by Guinness70 on 2008-03-05
> **Irony said:**
> I installed the thing from here;

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

It puts a 6.7 MB program in;

```
~/.mozilla/plugins
```

It works on the surfing site.dowloaded that and followed the instructions but didnt get passed 4.

> .tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.


```
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

```

:confused: confizzled
having a 64bit thingy is currently not that great :-)

---

### Post by empthollow on 2008-03-05
that's where your problem is.  you have a 64 bit processor and flash is not written for that. there is a way to install it, something about ndiswrapper.  I did it for a friend once using a how to in this forum but i don't have the link anymore.  It is possible, it just takes some extra work.

---

### Post by erginemr on 2008-03-06
I believe it is not ndiswrapper, but is nspluginwrapper.

Whatever the terminology, to install 64 bit Flash in your system, you can try one of the following two methods:
[http://ubuntuforums.org/showthread.php?t=648356](http://ubuntuforums.org/showthread.php?t=648356)
or 
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by empthollow on 2008-03-07
thank your for the correction, it's been a while since i messed with that.

---

### Post by doondoon on 2008-03-07
I am running gutsy and I have an amd athlon 64 3400. So if you have similar hardware this may work for you.

PROBLEM SOLVED:
1 ndswrapper is for your wifi so don't use it.
2 I had shockwave as my flash player.
2a write all these directions down or copy them to an offline document.
2b close firefox. You don't want it to be running or you will get error messages when you try to play flash.
3 I had to go to Synaptic package manager via "sudo synaptic" opens it in the shell
4 I completely erased my current flashplayer. I stress the word completely, because linux asks do you want to COMPLETELY remove flashplayerx (this will remove configured files) that's okay. You want to do that.
5 "sudo apt-get install flashplugin-nonfree" provide your password, press enter, and your good to go
6 Once you are finished you can close your terminal and reopen firefox. You can try this[ website]("http://www.oneill.com/") to see if your flashplayer is working now.
Thanks to Linux Juggalo and all who helped me or at least tried.

---

