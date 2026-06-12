---
title: "Chromium flash player update?"
date: 2015-10-23
forum: General Help
---

### Post by c1529g on 2015-10-23
I like using the Chromium web browser but i am constantly being informed to update Adobe Flash Player. Is there a plug in i could install?

---

### Post by QDR06VV9 on 2015-10-23
Those warnings are pretty standard for linux-flash
But just to be sure you can go this site and check.
[https://www.adobe.com/software/flash/about/](https://www.adobe.com/software/flash/about/)
I have version 19,0,0,226 installed which is current.

---

### Post by ajgreeny on 2015-10-23
In Trusty 14.04, fully updated I am running flash 17,0,0,188 according to that Adobe link.

I have no idea if or how I can get version 19,0,0,226, but in any case I do not get any warnings about flash being out of date.

---

### Post by QDR06VV9 on 2015-10-23
> **ajgreeny said:**
> In Trusty 14.04, fully updated I am running flash 17,0,0,188 according to that Adobe link.

I have no idea if or how I can get version 19,0,0,226, but in any case I do not get any warnings about flash being out of date.
Early on in testing 14.04 This was kind of up in the air, But that said I use this method for pepperflash on chromium.
[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)
coffecat tells it is no longer needed. But??
Best Regards

---

### Post by coffeecat on 2015-10-23
> **runrickus said:**
> coffecat tells it is no longer needed. But??

Rather than garble what I said why not link to it?

[http://ubuntuforums.org/showthread.php?t=2298308&p=13371241&viewfull=1#post13371241](http://ubuntuforums.org/showthread.php?t=2298308&p=13371241&viewfull=1#post13371241)

[http://ubuntuforums.org/showthread.php?t=2298927&p=13373608&viewfull=1#post13373608](http://ubuntuforums.org/showthread.php?t=2298927&p=13373608&viewfull=1#post13373608)

I'm not 100% sure the adobe-flashplugin package keeps the Chromium flash plugin up-to-date, but that is what the wiki.ubuntu.com links seem to imply. If they do, I'd far rather use the partner repository than a PPA, using instructions which are over 2 years old.

---

### Post by ajgreeny on 2015-10-23
I also believe that the ppa is no longer needed for the later versions of Ubuntu which have a pepperflashplugin-installer in the default repos, but I wonder if the ppa version still gets a later version of pepperflash than the default repos version?

Very odd situation that I do not have an answer for.

---

### Post by QDR06VV9 on 2015-10-23
> **ajgreeny said:**
> I also believe that the ppa is no longer needed for the later versions of Ubuntu which have a pepperflashplugin-installer in the default repos, but I wonder if the ppa version still gets a later version of pepperflash than the default repos version?

Very odd situation that I do not have an answer for.
That PPA I trust if that means anything..Been using it for a couple of years.
But if you had installed pepperflash using default repos and showing a lower version??
Indeed an Odd situation.
Kind Regards

---

### Post by Dennis N on 2015-10-23
Definitely true that adobe-flashplugin keeps both the Firefox-compatable and Chromium-compatable plugins up to date. See also post #6 in this thread 6 days ago:
[http://ubuntuforums.org/showthread.php?t=2299231](http://ubuntuforums.org/showthread.php?t=2299231) 
Chromium on Linux Mint has been using this too for some time. Currently, this method has Firefox version at 11,2,202,540 and Chromium version at 19,0,0,226. 

The pepperflashplugin-nonfree is deprecated. [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

---

### Post by ajgreeny on 2015-10-23
Thanks Dennis.

I was not aware that Adobe-flash was the package to use again and still had pepperflashplugin-nonfree installed.

You still need freshplayer-plugin for the pepperflash to work in firefox or you still get version 11, but now with adobe-flash installed I have flash 19.0.0.226 in both browsers.

Does this mean that adobe have now started development of flash again for Linux or is the Linux version of adobe-flash package produced by our own developers?

---

### Post by efflandt on 2015-10-23
I was not familiar with freshplayer-plugin, but if that uses pepperflash instead of adobe flash, that could explain the 19.0.0.226 flash version (unless it masquerades the real flash version). My Goggle Chrome has that version, but Firefox has the most recent Linux version of Adobe flash 11.2.202.540.

I would be curious if hulu.com works at all with freshplayer-plugin? Since Hulu started their current DRM, Linux Google Chrome does not work because that is not supported by Linux pepperflash. And Adobe flash in Firefox requires installing hal for Hulu's DRM to work.

Google Chrome works for Netflix, but that does not use flash. That is using HTML5 instead of the MS Silverlight that Netflix required previously.

---

### Post by Dennis N on 2015-10-23
> You still need freshplayer-plugin for the pepperflash to work in firefox or you still get version 11, but now with adobe-flash installed I have flash 19.0.0.226 in both browsers.

I haven't tried freshplayer-plugin, but I think I will and see how it works. As far as I know, Adobe is still not doing any new development for the Firefox-compatable flash - just the Chromium-compatable. They do only security patches, as we keep getting them.

---

### Post by ajgreeny on 2015-10-24
> **Dennis N said:**
> I haven't tried freshplayer-plugin, but I think I will and see how it works. As far as I know, Adobe is still not doing any new development for the Firefox-compatable flash - just the Chromium-compatable. They do only security patches, as we keep getting them.
Freshplayer-plugin was certainly a bit flaky to start but has been great for quite a while now.  Definitely worth trying!

My problem with not getting flash version above 17,0,0,188 was simply that I had installed the pepperflashplugin-nonfree, not realising that adobe-flashplugin was back as the package to use.

---

### Post by NikTh on 2015-10-24
As far as I know, 
**for Chromium** there is a package in Official Ubuntu repositories(multiverse) named "pepperflashplugin-nonfree" that it downloads and integrates the Google Chrome(stable) Flash plugin into Chromium. 
So, for Chromium browser there is no need to install the "flashplugin-installer" package at all.

**For Firefox** things are different because Mozilla doesn't support the Google's PPAPI so it still uses the old one NPAPI, but as we know Adobe has dropped support for this API and the version is jammed in 11.2. 
Also, for Firefox the Unofficial [Fresh Player Plugin]("https://github.com/i-rinat/freshplayerplugin") exists and it works quite good but it's an unofficial plugin.

I'm in Ubuntu 14.04 LTS (fully updated) with Chromium and PepperFlashPlugin-NonFree and [Adobe page]("https://helpx.adobe.com/flash-player.html") reports "18,0,0,233 installed".

---

### Post by vasa1 on 2015-10-24
I use Google Chrome and have v. 19 (image). I don't use Flash and so I've held back updates to Google Chrome unless there are issues unrelated to Flash that the update fixes.> The stable channel has been updated to 46.0.2490.80 for Windows, Mac, and Linux. This release contains a critical update to Adobe Flash Player (19.0.0.226).from [http://googlechromereleases.blogspot.com/search/label/Stable%20updates](http://googlechromereleases.blogspot.com/search/label/Stable%20updates)

---

### Post by NikTh on 2015-10-24
> **vasa1 said:**
> I use Google Chrome and have v. 19 (image). I don't use Flash and so I've held back updates to Google Chrome unless there are issues unrelated to Flash that the update fixes.from [http://googlechromereleases.blogspot.com/search/label/Stable%20updates](http://googlechromereleases.blogspot.com/search/label/Stable%20updates)

So, I guess we are waiting for an update of "pepperflashplugin-nonfree" in trusty. 

Or, 
if someone is in hurry, he can do the same thing (of what this package does) manually. 
Downloading Google Chrome, extract the Flash Plugin and move it to appropriate place**[1]**. 
Right now, pepperflashplugin-nonfree in trusty reports. 
**Version: 1.3ubuntu1**
and from
/var/cache/pepperflashplugin-nonfree/google-chrome-stable_**45**.0.2454.85-1_amd64.deb

**[1]**```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
mkdir ChromeTMP
dpkg-deb -R google-chrome-stable_current_amd64.deb ChromeTMP
sudo mv ChromeTMP/opt/google/chrome/PepperFlash/libpepflashplayer.so /usr/lib/pepperflashplugin-nonfree/
rm google-chrome-stable_current_amd64.deb && rm ChromeTMP/ -rf
```

and [Adobe Page]("https://helpx.adobe.com/flash-player.html") should now report "19.0.0.226"

---

### Post by QDR06VV9 on 2015-10-24
> **coffeecat said:**
> Rather than garble what I said why not link to it?

[http://ubuntuforums.org/showthread.php?t=2298308&p=13371241&viewfull=1#post13371241](http://ubuntuforums.org/showthread.php?t=2298308&p=13371241&viewfull=1#post13371241)

[http://ubuntuforums.org/showthread.php?t=2298927&p=13373608&viewfull=1#post13373608](http://ubuntuforums.org/showthread.php?t=2298927&p=13373608&viewfull=1#post13373608)

I'm not 100% sure the adobe-flashplugin package keeps the Chromium flash plugin up-to-date, but that is what the wiki.ubuntu.com links seem to imply. If they do, I'd far rather use the partner repository than a PPA, using instructions which are over 2 years old.

A thousand pardons, I can see that was lacking in clear information(links).
And bear in mind the PPA was all I ever knew from testing forward. 
Even though the page is 2 years or more old the PPA is always current
I never enable the Partners Repo.
> [COLOR=#333333][FONT=monospace]PEPPER FLASH FOR CHROMIUM ON UBUNTU[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]This repository provides the pepflashplugin-installer package, which will download and install the newer "Pepper" (PPAPI) version of the Adobe Flash Player plugin for use with the Chromium Web browser on Ubuntu GNU/Linux. The package is similar to Ubuntu's official flashplugin-installer in that it does not include the plugin itself, but instead downloads the plugin and installs it automatically. (Specifically, it downloads the latest Google Chrome package, extracts the Pepper Flash files, and installs only those. Google Chrome itself is not installed nor otherwise used in any way.)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Some information on the Pepper Flash plugin and how it differs from earlier versions of Flash may be found here:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    [http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]SUPPORTED UBUNTU RELEASES[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]The pepflashplugin-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]installer package may be installed on Ubuntu 12.04 (Precise) or newer, for the amd64 or i386 architecture. It is known to work on 11.10 (Oneiric) if the update-notifier and update-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]notifier-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]common packages are upgraded to the version shipped with 12.04. It has not been tested on older releases of Ubuntu.[/FONT][/COLOR]

With ajgreeny verifing a current version I will no longer
steer anyone to this method, But I will continue to use for myself.
Seems still by all the post's no clear direction.
Hope that was not taken offensive.
Kind Regards

---

### Post by ajgreeny on 2015-10-25
I agree with runrickus's comment that there seems to be no clear direction anywhere on how best to install flash at the moment, and it does appear to be a very confusing situation with that Getting Flash wiki not being the easiest to find in all the many flash links that appear when you search.

My one final comment, however, is that by installing both **adobe-flashplugin** from the partner repos and **freshplayerplugin** from the nilarimogard-webupd8 repos I now have a fully working flash version 19.0.0.226 in both my chromium and firefox browsers.

---

### Post by rmstock2 on 2015-12-24
Instead of updating adobe.com with your recent flash version, or even starting
your browser and inserting about:plugins , the following script might be of help :

```

#!/bin/bash

FLASH_LIB=/usr/lib/flashplugin-installer/libflashplayer.so
#FLASH_LIB=/usr/lib/mozilla/plugins/libflashplayer.so
#FLASH_LIB=/usr/lib/flash-plugin/libflashplayer.so

FLASH_ARCH=`file $FLASH_LIB | sed 's/ELF/\n\nELF/' |\
         sed 's/version/\nversion/'`
LNX_ENGINE=`strings $FLASH_LIB | grep Linux-Player`
LNX_FLASH=`strings $FLASH_LIB | grep LNX`
ADOBE_FLASH=`strings $FLASH_LIB | grep Shockwave | grep 1`
ADOBE_PTNTS=`strings $FLASH_LIB | grep "^AdobePatentID" |\
         awk '{print "                "$1 }'`
ADOBE_CPRGHT=`strings $FLASH_LIB |\
         grep -i Copyright | sed 's/^.*Copyright/Copyright/' |\
         sed 's/reserved.*$/reserved./' | sed 's/All/\nAll/'`

echo "$FLASH_ARCH "
echo "Linux Engine  : $LNX_ENGINE "
echo "Flash Version : $LNX_FLASH "
echo "Adobe Version : $ADOBE_FLASH "
echo "$ADOBE_PTNTS "
echo "$ADOBE_CPRGHT "

exit 0

```
to find the full path of libflashplayer.so type 

```

stock@acer30u:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
stock@acer30u:~$ 

```

```

stock@acer30u:~$ flashv 
/usr/lib/flashplugin-installer/libflashplayer.so: 

ELF 64-bit LSB  shared object, x86-64, 
version 1 (SYSV), dynamically linked, stripped 
Linux Engine  : Linux-Player-64-2011080916100 
Flash Version : LNX 11,2,202,554 
Adobe Version : Shockwave Flash 11.2 r202 
                AdobePatentID="P057"
                AdobePatentID="P297"
                AdobePatentID="P650"
                AdobePatentID="P656"
                AdobePatentID="P912"
                AdobePatentID="P052"
                AdobePatentID="B1156"
                AdobePatentID="P649"
                AdobePatentID="B598" 
Copyright 2008 Adobe Systems Incorporated. 
All rights reserved. 
stock@acer30u:~$

```

---

