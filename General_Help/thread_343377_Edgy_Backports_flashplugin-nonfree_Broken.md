---
title: "Edgy Backports flashplugin-nonfree Broken?"
date: 2007-01-21
forum: General Help
---

### Post by aysiu on 2007-01-21
Believe it or not, I can't find the backports subforum. That's why I'm posting in General Help.

I was impressed at first that a .deb for Flash 9 was uploaded so quickly to the Edgy backports repositories. I even added it as a method to [Psychocats page on Flash 9](http://www.psychocats.net/ubuntu/flash).

When I wanted to actually use that method, I got this error, though: ```
Selecting previously deselected package gsfonts-x11.
(Reading database ... 96582 files and directories currently installed.)
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.20build1_all.deb) ...
Setting up gsfonts-x11 (0.20build1) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 96624 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.21.78.2ubuntu1~edgy1_i386.deb) ...
Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~edgy1) ...
Downloading... download failed
The Flash plugin is NOT installed.
``` Has anyone successfully installed Flash 9 with the Edgy Backports package? If not, maybe a bug report should be filed on that package, and I'll keep advising people to use the old method.

---

### Post by Ramses de Norre on 2007-01-21
I installed it when it became available in backports and it's working perfect here: ```
ramses@icarus:~$ apt-cache policy flashplugin-nonfree 
flashplugin-nonfree:
  Installed: 9.0.21.78.2ubuntu1~edgy1
  Candidate: 9.0.21.78.2ubuntu1~edgy1
  Version table:
 *** 9.0.21.78.2ubuntu1~edgy1 0
        500 http://archive.ubuntu.com edgy-backports/multiverse Packages
        100 /var/lib/dpkg/status
     7.0.68~ubuntu3 0
        500 http://archive.ubuntu.com edgy/multiverse Packages

```

I'm not going to try to reinstall now though, I don't have the time to fix it if I get the same errors..
I don't think the package has ever been updated...

---

### Post by niekko on 2007-01-21
Download failed for me too.

---

### Post by aysiu on 2007-01-21
Hm. That's weird. Anyone else been successful or unsuccessful using the Edgy Backports Flash 9 package?

---

### Post by kpkeerthi on 2007-01-21
Failing for me too....

---

### Post by aysiu on 2007-01-21
Well it's worked for one person, but for at least three people it's failed.

I've gone ahead and filed a bug report on it:
[https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/80870](https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/80870)

---

### Post by rclimb514 on 2007-01-21
Oddly, I had the same issue using apt-get, but when I tried again through synaptic, everything worked fine.

*Update* Uhh...I mean everything appeared to work fine but then flash didn't actually work.

---

### Post by kerry_s on 2007-01-21
No problems here, i installed through synaptic about 4 days ago. Look in /usr/lib/unpack-flash... it might have downloaded it and you can just unpack it manually.

Edit: I forgot i unistalled mine and installed the release version manually( Shockwave Flash 9.0 r31).

---

### Post by aysiu on 2007-01-21
Hm. I have a theory about this.

The .deb package, if I understand it correctly based on my experience with the old flashplugin-nonfree (version 7) doesn't actually contain Flash 9 but just smooths out the process of downloading it and unpacking it.

Either the actual .tar.gz is being hosted somewhere with a finicky server (works sometimes, doesn't other times), or it's trying to be directly downloaded from Adobe's website, which, for whatever reason, might occasionally block outside calls.

My theory may not hold any water, but that's one idea at least...

---

### Post by kerry_s on 2007-01-21
They might be in the process of updating it to the release. You can grab it straight from adobe in tgz or rpm(use alien)-> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by aysiu on 2007-01-21
> **kerry_s said:**
> They might be in the process of updating it to the release. You can grab it straight from adobe in tgz or rpm(use alien)-> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
Oh, I already have instructions for how to grab it directly from Adobe:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

But I would like to also present the option of using the repositories. But if the success rate is roughly 50%, I can't really advise using that method.

---

### Post by kodiak on 2007-01-21
me too...
> Downloading... download failed
The Flash plugin is NOT installed.

---

### Post by F for Fragging on 2007-01-21
I was about to post a topic about it too after I had problems today installing Flash, the "download failed" bullshit drove me mad. The flash package from edgy backports didn't work, and the flash package from the seveas repository didnt work either. I recall that they did work for me in the past. I switched my repositories from edgy to feisty, and the flash package from feisty did work for me.
I [googled]("http://www.google.nl/search?hl=nl&q=flashplugin-nonfree+%22download+failed%22&btnG=Google+zoeken&meta=") for this bug. According to the results, it's an issue with a http proxy setting?

---

### Post by plumeria on 2007-01-21
I also get the download failed error. I've added the backports repo and typed the following in a terminal:

sudo apt-get install flashplugin-nonfree     (remembering off the top of my head, so the name may be wrong)

When that failed with the "download failed" error, I tried:

sudo apt-get install --reinstall flashplugin-nonfree

Same result, "download failed" and the message that the flash plugin was NOT installed.

---

### Post by grim4593 on 2007-01-21
```
Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~edgy1) ...
Downloading... download failed
The Flash plugin is NOT installed.
```

Same problem. I thought it was just me. I guess I am going to alien the adobe rpm until the deb is fixed.

---

### Post by aysiu on 2007-01-21
> **grim4593 said:**
> ```
Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~edgy1) ...
Downloading... download failed
The Flash plugin is NOT installed.
```

Same problem. I thought it was just me. I guess I am going to alien the adobe rpm until the deb is fixed.
Or you can use the .tar.gz

Instructions here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by kodiak on 2007-01-22
the .tar.gz method works ***real*** fine

> Instructions here:
[http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")

---

### Post by jlc on 2007-01-23
Failed for me, and here is how I fixed it.  Basically, remove it, remove backports, install 7.0 again, add backports, upgrade.

Here is the output if you like to look at stuff......

```


$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  flashplugin-nonfree
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/13.2kB of archives. After unpacking 102kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 134473 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.21.78.2ubuntu1~edgy1_i386.deb) ...
Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~edgy1) ...
Downloading... download failed
The Flash plugin is NOT installed.


justin@kainos:~$ sudo aptitude remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  flashplugin-nonfree
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 102kB will be freed.
Writing extended state information... Done
(Reading database ... 134480 files and directories currently installed.)
Removing flashplugin-nonfree ...

```

Comment out backports from /etc/apt/sources.list

```

sudo aptitude update
$ sudo aptitude install flashplugin-nonfree
Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading...  done.

$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  flashplugin-nonfree
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.0kB of archives. After unpacking 65.5kB will be freed.
Do you want to continue? [Y/n/?] y
Get:1 http://us.archive.ubuntu.com edgy-backports/multiverse flashplugin-nonfree 9.0.31~ubuntu1~edgy1 [14.0kB]
Fetched 14.0kB in 0s (21.8kB/s)
Preconfiguring packages ...
(Reading database ... 134483 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 7.0.68~ubuntu3 (using .../flashplugin-nonfree_9.0.31~ubuntu1~edgy1_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.31~ubuntu1~edgy1) ...
Downloading...
--20:16:59--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.126.70
Connecting to fpdownload.macromedia.com|72.246.126.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  307.26 KB/s
   50K .......... .......... .......... .......... ..........  3%  765.17 KB/s
  100K .......... .......... .......... .......... ..........  5%  746.20 KB/s
  150K .......... .......... .......... .......... ..........  7%  856.44 KB/s
  200K .......... .......... .......... .......... ..........  9%  853.84 KB/s
  250K .......... .......... .......... .......... .......... 11%  801.94 KB/s
  300K .......... .......... .......... .......... .......... 13%  842.89 KB/s
  350K .......... .......... .......... .......... .......... 15%  898.05 KB/s
  400K .......... .......... .......... .......... .......... 17%  824.24 KB/s
  450K .......... .......... .......... .......... .......... 19%  826.95 KB/s
  500K .......... .......... .......... .......... .......... 21%  824.99 KB/s
  550K .......... .......... .......... .......... .......... 23%  845.17 KB/s
  600K .......... .......... .......... .......... .......... 25%  840.96 KB/s
  650K .......... .......... .......... .......... .......... 27%  801.06 KB/s
  700K .......... .......... .......... .......... .......... 29%  789.05 KB/s
  750K .......... .......... .......... .......... .......... 31%  916.32 KB/s
  800K .......... .......... .......... .......... .......... 33%  771.95 KB/s
  850K .......... .......... .......... .......... .......... 35%  897.62 KB/s
  900K .......... .......... .......... .......... .......... 37%  871.11 KB/s
  950K .......... .......... .......... .......... .......... 39%  842.15 KB/s
 1000K .......... .......... .......... .......... .......... 41%  813.01 KB/s
 1050K .......... .......... .......... .......... .......... 43%  818.22 KB/s
 1100K .......... .......... .......... .......... .......... 45%  842.13 KB/s
 1150K .......... .......... .......... .......... .......... 47%  884.08 KB/s
 1200K .......... .......... .......... .......... .......... 49%  774.58 KB/s
 1250K .......... .......... .......... .......... .......... 51%  870.31 KB/s
 1300K .......... .......... .......... .......... .......... 52%  834.42 KB/s
 1350K .......... .......... .......... .......... .......... 54%  833.36 KB/s
 1400K .......... .......... .......... .......... .......... 56%  782.23 KB/s
 1450K .......... .......... .......... .......... .......... 58%  789.48 KB/s
 1500K .......... .......... .......... .......... .......... 60%  945.91 KB/s
 1550K .......... .......... .......... .......... .......... 62%  858.13 KB/s
 1600K .......... .......... .......... .......... .......... 64%  819.16 KB/s
 1650K .......... .......... .......... .......... .......... 66%  813.64 KB/s
 1700K .......... .......... .......... .......... .......... 68%  842.28 KB/s
 1750K .......... .......... .......... .......... .......... 70%  837.27 KB/s
 1800K .......... .......... .......... .......... .......... 72%  829.86 KB/s
 1850K .......... .......... .......... .......... .......... 74%  831.13 KB/s
 1900K .......... .......... .......... .......... .......... 76%  859.71 KB/s
 1950K .......... .......... .......... .......... .......... 78%  817.26 KB/s
 2000K .......... .......... .......... .......... .......... 80%  819.22 KB/s
 2050K .......... .......... .......... .......... .......... 82%  842.91 KB/s
 2100K .......... .......... .......... .......... .......... 84%  824.13 KB/s
 2150K .......... .......... .......... .......... .......... 86%  825.65 KB/s
 2200K .......... .......... .......... .......... .......... 88%  852.79 KB/s
 2250K .......... .......... .......... .......... .......... 90%  792.64 KB/s
 2300K .......... .......... .......... .......... .......... 92%  791.59 KB/s
 2350K .......... .......... .......... .......... .......... 94%  824.57 KB/s
 2400K .......... .......... .......... .......... .......... 96%  907.19 KB/s
 2450K .......... .......... .......... .......... .......... 98%  772.96 KB/s
 2500K .......... .......... .......... .......... ........  100%  853.90 KB/s

20:17:02 (803.65 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [2609703/2609703]

Download done.
Flash Plugin installed.

```

Kick the browser open and go to your flashy site....

---

### Post by aysiu on 2007-01-23
Apparently, according to [one comment on the bug report](https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/80870/comments/3), the Feisty package works, but the Edgy one doesn't.

---

### Post by Cable on 2007-01-23
It just worked perfectly for me.

---

### Post by PauloPio on 2007-01-24
I don't think it is a problem with Edgy Backports. I can't even download the tar.gz file or rpm directly from the site. Maybe they remove it temporally because of the huge traffic?

---

### Post by astronerd on 2007-01-25
Hi, I got the download to work using 
 sudo aptitude update && sudo aptitude install flashplugin-nonfree
 and it said that it was installed.  Then I went to about:plugins in firefox and it wasnt installed or seen.  So I did(with advice from another site...)
 sudo rm /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/flashplayer.xpt
and 
rm ~/.mozilla/plugins/libflashplayer.so ~/.mozilla/plugins/flashplayer.xpt
  Now when I do about:plugins, I have NO flash plugin.  I see that 9 is installed, but how do I get firefox to see it?  I dont know what to add where...
Thanks

---

### Post by andnobodyslept on 2007-01-25
Well I hate to say it but I found an easy way to get flash up and running again. I went to youtube when firefox noticed I didn't have flash it told me to click the empty box, and then it installed it for me, so far seems to work fine. This is strange since I spent a lot of time going about this the harder ways.
-Ian

---

### Post by gmutt on 2007-02-22
Don't know if this has been resolved in another thread .. so forgive me if it has

I just installed Flash 9 on Ubuntu 6.10  without any problems ... using :

sudo aptitude update && sudo aptitude install flashplugin-nonfree

---

### Post by Roel123 on 2007-02-28
I am also unable to install it

...

Instellen van flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: fout bij afhandelen van flashplugin-nonfree (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug

...

Fouten gevonden tijdens behandelen van:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by enabled on 2007-03-26
There still seem to be a problem in Edgy:

sudo aptitude update && sudo aptitude install flashplugin-nonfree

gives me

Downloading...  done.
automatic installation failed due to network problems or upstream changes

I get the same when using Synaptic...

---

