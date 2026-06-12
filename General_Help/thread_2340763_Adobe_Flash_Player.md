---
title: "Adobe Flash Player"
date: 2016-10-21
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-10-21
I signed up for a class and it starts Monday 10/24/2016.  It uses Adobe Flash Player on Firefox and I'm not sure what I should download.  Adobe offers YUM for Linux, .tar.gz for other Linux, .rpm for other Linux and APT for Ubuntu 10.04 or higher. I tried tha APT one, but I get the following error.  Also, I'm using Ubuntu 16.10.  Please tell me witch one to get and if possible how to get it running.

---

### Post by Dennis N on 2016-10-22
Since you use 16.10, just install the adobe-flashplugin package from the Ubuntu repositories. It's the same plugin as the one offered for Linux from the Adobe web site.

First, enable "Canonical Partners" repository in Software and Updates > Other Software tab. Then update your software sources list with **sudo apt-get update**. adobe-flashplugin should then show up in the available packages for installation.

---

### Post by shane_faulkinbury2 on 2016-10-22
Okay, I did what you said and I still have the same problem.  Here are the screen shots.

---

### Post by bearlake on 2016-10-22
It should have worked but you can try this now from the terminal window.

```
sudo apt-get update
```

then

```
sudo apt-get install flashplugin-installer
```

---

### Post by Dennis N on 2016-10-22
> Okay, I did what you said and I still have the same problem.

Are you referring to the error message? If you have adobe-flashplugin installed from the Ubuntu repository, then you have no need to download anything from Adobe. The error message apparently comes from trying the "APT for Ubuntu" install method, which I think is no longer supported. Above all, does the flash player work (try the test below)? 

Sorry, but in the first screenshot in post #3 the print is illegible for me - what is it about?

_Test flash player here_:

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

Do you see the bouncing cube when the page loads?
Does the Version Information Box on the same page report that you have a version of flash player installed?

---

### Post by shane_faulkinbury2 on 2016-10-22
Nope and yes Flash Player is installed.

---

### Post by shane_faulkinbury2 on 2016-10-22
Also the web page you directed me to to test it just shows a black screen.

---

### Post by Frogs Hair on 2016-10-22
Have you restated the browser since the installation ?

---

### Post by pqwoerituytrueiwoq on 2016-10-22
There are 3 versions of flash you can run in firefox;
[LIST=1]
[*]NPAPI flash11 (old version that only gets security updates; some years back adobe deiced to drop Linux flash support and left us with this) 
[*]Pepper flash 23 (this uses google chrome's flash player in firefox with a wrapper) 
[*]NPAPI flash 23 (this a beta flash version, adobe change there mind recently about dropping linux flash support; i guess maintaining 2 version got to be too much work) 
[/LIST]
check if the libflashplayer.so file is present
```
ls /usr/lib/adobe-flashplugin/
```
you can try the beta version of flash like this
for a 64bit system:
```
sudo wget https://fpdownload.macromedia.com/pub/labs/flashruntimes/flashplayer/linux64/libflashplayer.so -O /usr/lib/adobe-flashplugin/libflashplayer.so
```
for a 32bit system:
```
sudo wget https://fpdownload.macromedia.com/pub/labs/flashruntimes/flashplayer/linux32/libflashplayer.so -O /usr/lib/adobe-flashplugin/libflashplayer.so
```

another option is [pepper flash]("apt:pepperflashplugin-nonfree") (64bit only)

this page can tell you what version of flash you have
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

if you have both pepper flash 23 and beta flash 23 installed the beta will be used by firefox
if you have pepper flash 23 and flash 11 installed pepper flash will be used by firefox

---

### Post by Dennis N on 2016-10-22
The terminal shows flash is installed, but no proof it is working yet, since you say the test page only shows an all black page. That's unexpected. You should see the page in the attached screen shot. The test page link that I included is OK, since I used it to access the page for the shot. Even if flash was disabled in Tools Menu, you should still get all the text on the page.

---

### Post by shane_faulkinbury2 on 2016-10-23
Well after I try sudo wget [https://fpdownload.macromedia.com/pub/labs/flashruntimes/flashplayer/linux64/libflashplayer.so](https://fpdownload.macromedia.com/pub/labs/flashruntimes/flashplayer/linux64/libflashplayer.so) -O /usr/lib/adobe-flashplugin/libflashplayer.so   It states no file or directory? After trying your solution Dennis I still have "the black box of death".  :confused:

---

### Post by Dennis N on 2016-10-23
The wget command you are trying isn't needed since your terminal output in post #6 says the flash plugin has been installed (at the bottom). wget would just download another copy, even if it had worked! 

To double-check that it is really installed, try (in the terminal):

```
apt-cache policy adobe-flashplugin
```

and post the output. You should get output similar to this (from my computer with 16.04):

```
dmn@Sydney ~ $ apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: 1:20161011.1-0ubuntu0.16.04.1
  Candidate: 1:20161011.1-0ubuntu0.16.04.1
  Version table:
 *** 1:20161011.1-0ubuntu0.16.04.1 500
        500 http://archive.canonical.com/ubuntu xenial/partner amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by deadflowr on 2016-10-23
What's it tell you about the plugin state within firefox?
click on the hamburger icon in the top right corner-ish area go to Add-ons, then select plugins.

---

### Post by shane_faulkinbury2 on 2016-10-23
Hmm, I went into plugins to check and it said to not activate so I set it to always activate did a refresh and the opened my terminal and ran the 
apt-cache policy adobe-flashplugin

and I got this?

---

### Post by deadflowr on 2016-10-23
Yeah, because you installed the flashplugin-installer package.
Not the adobe-flashplugin package.
Different packages.

Anyway, it's unclear what happened when you refreshed the browser after the toggling of the activation state...

---

### Post by shane_faulkinbury2 on 2016-10-23
Here's the refresh of the pages after updating.  I just don't understand what the problem could be.

---

### Post by SeijiSensei on 2016-10-23
I'll suggest an alternate route, one that uses Pipelight and the Windows version of Flash.  First, follow the instructions at [http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html) to install Pipelight, then activate Flash using the instructions at [http://pipelight.net/cms/plugin-flash.html](http://pipelight.net/cms/plugin-flash.html).  You may also need to run
```
sudo pipelight-plugin --create-mozilla-plugins
```
after you're finished to make everything work correctly.  Restart Firefox, and you should now seen an entry for Flash 22.0 under Tools > Add-Ons > Plugins.

---

### Post by shane_faulkinbury2 on 2016-10-23
I'm not sure what version of Ubuntu you are using, but I'm using 16.10.  As you can see I get an error running  
sudo apt-get install --install-recommends pipelight-multi

and each command thereafter.

---

### Post by mc4man on 2016-10-23
> **shane_faulkinbury2 said:**
> Here's the refresh of the pages after updating.  I just don't understand what the problem could be.
I  sorta doubt anybody can read the error shown in that 2nd screenshot, maybe you should just say what it is..

---

### Post by deadflowr on 2016-10-23
Since it's unclear if flash is the problem, looking at their [Requirements page]("https://nhlearningsolutions.com/Portals/0/Documents/OLLRequirements/OLL-Requirements-2014.pdf"), you can go here:
[https://na1cps.adobeconnect.com/common/help/en/support/meeting_test.htm]("https://na1cps.adobeconnect.com/common/help/en/support/meeting_test.htm")
Does it show flash working?

If so, then the problem might be elsewhere...

It's also unclear if you tried this yet

---

### Post by shane_faulkinbury2 on 2016-10-23
I forgot to upload the screen shot which I have now done.  The problem is flash because I'm well above the requirements.

---

### Post by shane_faulkinbury2 on 2016-10-24
Check this out.  I go to the Add-ons Manager and it says Never Activate so I change it to Always Activate, refresh the page and it's still on Always Activate, and go to the class login page, refresh and it still has a red X next to Test Virtual Classroom.  Hmmmm!

---

### Post by shane_faulkinbury2 on 2016-10-24
I have an additional question.  On the site that I'm taking classes on it says Install. When I go to that page it gives me 4 download options.  APT will not work because it doesn't like Yakkety Yak.  How do I install the YUM, tar.gz or the .rpm?

---

### Post by mc4man on 2016-10-24
Did you go here & make sure all 4 go green checked?
[https://na1cps.adobeconnect.com/common/help/en/support/meeting_test.htm](https://na1cps.adobeconnect.com/common/help/en/support/meeting_test.htm)

---

### Post by pqwoerituytrueiwoq on 2016-10-30
> **shane_faulkinbury2 said:**
> Well after I try ```
sudo wget https://fpdownload.macromedia.com/pub/labs/flashruntimes/flashplayer/linux64/libflashplayer.so -O /usr/lib/adobe-flashplugin/libflashplayer.so
```   It states no file or directory? After trying your solution Dennis I still have "the black box of death".  :confused:
then lets create that directory
```
sudo mkdir /usr/lib/adobe-flashplugin
```
you may need to remove flashplugin-installer
```
sudo apt-get purge flashplugin-installer
```

edit:
Seems doing this requires [adobe-flashplugin]("apt:adobe-flashplugin") be installed
I spent a couple hours making/testing a script to install multiple versions flash, should work on 14.04 through 16.04 64bit/32bit

---

