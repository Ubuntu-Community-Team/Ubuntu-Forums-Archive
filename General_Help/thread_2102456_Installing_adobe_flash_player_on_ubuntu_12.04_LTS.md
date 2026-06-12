---
title: "Installing adobe flash player on ubuntu 12.04 LTS"
date: 2013-01-07
forum: General Help
---

### Post by Raafat1991 on 2013-01-07
Hi guys....i hope all to be fine


when i enter to a site it requires from me to install adobe flash player but i don't exactly know if i have one or not ?

i can run youtube  video and any a video i see but with that site i can't .


thanks....

---

### Post by sudodus on 2013-01-07
I suggest that you install ***flashplugin-installer*** either with Synaptic (GUI) or

```
sudo apt-get install flashplugin-installer
``` (terminal window)

You can read a short description about flashplugin-installer in Synaptic.

---

### Post by philinux on 2013-01-07
> **Raafat1991 said:**
> Hi guys....i hope all to be fine


when i enter to a site it requires from me to install adobe flash player but i don't exactly know if i have one or not ?

i can run youtube  video and any a video i see but with that site i can't .


thanks....

Sounds like u already have flash installed. Which site is the one that complains?

---

### Post by Raafat1991 on 2013-01-08
> **sudodus said:**
> I suggest that you install ***flashplugin-installer*** either with Synaptic (GUI) or

```
sudo apt-get install flashplugin-installer
``` (terminal window)

You can read a short description about flashplugin-installer in Synaptic.


No luck...it's already installed .

I don't know what is wrong exactly !!

---

### Post by Raafat1991 on 2013-01-08
> **philinux said:**
> Sounds like u already have flash installed. Which site is the one that complains?


this :  [www.livemocha.com](www.livemocha.com)

---

### Post by sudodus on 2013-01-08
> **Raafat1991 said:**
> this :  [www.livemocha.com](www.livemocha.com)
I can see that page. (But NoScript warned, that there is a script)

What do you want to do (which link on that page do you want to use)?

Which web browser do you use? Firefox, Chromium-browser ...

---

### Post by Raafat1991 on 2013-01-08
> **sudodus said:**
> I can see that page. (But NoScript warned, that there is a script)

What do you want to do (which link on that page do you want to use)?

Which web browser do you use? Firefox, Chromium-browser ...

I think to see the link you need to register with that site

i'm using firefox

---

### Post by sudodus on 2013-01-08
> **Raafat1991 said:**
> I think to see the link you need to register with that site

i'm using firefox
OK, so I can't check if I can see that link.

In Firefox, check via the ***Tools*** dropdown menu your ***plugin modules***, check that you have installed a Flash module, and that it is activated!

---

### Post by Raafat1991 on 2013-01-09
> **sudodus said:**
> OK, so I can't check if I can see that link.

In Firefox, check via the ***Tools*** dropdown menu your ***plugin modules***, check that you have installed a Flash module, and that it is activated!

Hi...i have no one , but how can i install it ?

---

### Post by Raafat1991 on 2013-01-09
> **Raafat1991 said:**
> Hi...i have no one , but how can i install it ?

Hi...i have installed with this guide [http://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems](http://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems)

but the same problem.....

---

### Post by sudodus on 2013-01-09
See the following links

[http://blogdaprima.com/2012/install-adobe-flash-plugin-on-ubuntu-12-04-lts-precise-pangolin/]("http://blogdaprima.com/2012/install-adobe-flash-plugin-on-ubuntu-12-04-lts-precise-pangolin/")
[http://ubuntupop.blogspot.se/2012/09/Linux-mint-13-tutorial-install-adobe-flash-plugin.html]("http://ubuntupop.blogspot.se/2012/09/Linux-mint-13-tutorial-install-adobe-flash-plugin.html")
--
If your system is correctly configured, flashplugin-installer should do the work automatically.

---

### Post by Raafat1991 on 2013-01-11
> **sudodus said:**
> See the following links

[http://blogdaprima.com/2012/install-adobe-flash-plugin-on-ubuntu-12-04-lts-precise-pangolin/](http://blogdaprima.com/2012/install-adobe-flash-plugin-on-ubuntu-12-04-lts-precise-pangolin/)
[http://ubuntupop.blogspot.se/2012/09/Linux-mint-13-tutorial-install-adobe-flash-plugin.html](http://ubuntupop.blogspot.se/2012/09/Linux-mint-13-tutorial-install-adobe-flash-plugin.html)
--
If your system is correctly configured, flashplugin-installer should do the work automatically.


Hi...also no luck i don't know what is wrong with my OS or firefox

---

### Post by dannyboy79 on 2013-01-11
try another browser, google chrome or google chromium. just a thought if youtube works then flash is installed and working, it could be a bad implementation on theit website?

---

### Post by Raafat1991 on 2013-01-11
> **dannyboy79 said:**
> try another browser, google chrome or google chromium. just a thought if youtube works then flash is installed and working, it could be a bad implementation on theit website?

I have installed Chromium , there is no problem with youtube , but the same problem  with that site....

---

### Post by dannyboy79 on 2013-01-11
are you sure it's a flash problem and not a oracle java problem? like I said, if youtube works then your flash install is working fine.

---

### Post by Raafat1991 on 2013-01-11
> **dannyboy79 said:**
> are you sure it's a flash problem and not a oracle java problem? like I said, if youtube works then your flash install is working fine.


Please tell me how can i know where is my problem and with what ?

---

### Post by iMac71 on 2013-01-11
do you have installed ubuntu-restricted-extras? If not, you've to install them with Ubuntu Software Centre or Synaptic

---

### Post by dannyboy79 on 2013-01-11
> **Raafat1991 said:**
> Please tell me how can i know where is my problem and with what ?go to youtube and save the link to a video to your clipboard. right click on link and click copy. then go to keepvid.com and see if you can download the youtube video, that site uses java. if you can, then your java is installed correctly

The only way I usually tell if I have flash installed is that I check Youtube, if youtube works then flash is installed and working.

as I said, maybe something is wrong with their site?

---

### Post by Raafat1991 on 2013-01-11
> **dannyboy79 said:**
> go to youtube and save the link to a video to your clipboard. right click on link and click copy. then go to keepvid.com and see if you can download the youtube video, that site uses java. if you can, then your java is installed correctly

The only way I usually tell if I have flash installed is that I check Youtube, if youtube works then flash is installed and working.

as I said, maybe something is wrong with their site?

All what i get from keepvid.com is iLividSetup.exe and i can't run

---

### Post by Raafat1991 on 2013-01-11
> **iMac71 said:**
> do you have installed ubuntu-restricted-extras? If not, you've to install them with Ubuntu Software Centre or Synaptic

I did but also no luck....

---

### Post by rrich1974 on 2013-01-11
why dont you just install google chrome?
it comes with latest version of flash integrated.

---

### Post by Raafat1991 on 2013-01-12
> **rrich1974 said:**
> why dont you just install google chrome?
it comes with latest version of flash integrated.

firefox likes me....but tell me how will i do that ?

---

### Post by rrich1974 on 2013-01-12
you have got no chance to have the latest flash unless you use chrome. 
chrome is the best browser. (chrome, not chromium)

---

### Post by Raafat1991 on 2013-01-13
> **rrich1974 said:**
> you have got no chance to have the latest flash unless you use chrome. 
chrome is the best browser. (chrome, not chromium)

Any an idea about installation ?

---

### Post by rrich1974 on 2013-01-16
are you asking about google chrome? 
just go to google and download the .deb package for google chrome, i tell you man, it is the best browser on the market today.

---

### Post by Raafat1991 on 2013-01-17
> **rrich1974 said:**
> are you asking about google chrome? 
just go to google and download the .deb package for google chrome, i tell you man, it is the best browser on the market today.


Solved my problem but why firefox can't display that video ?

---

### Post by Warren Hill on 2013-01-17
Adobe have stopped supporting Linux so old versions of Flash will still play but the normal Flash player (in ubuntu-restricted-extras) will not handle the latest version of Flash but will handle older versions.

This is why some sites work and some don't.  Chrome has a later flash player built it so will handle later flash content

---

### Post by rrich1974 on 2013-01-17
as i told before...firefox uses flash 11.2 and google chrome uses flash 11.5
right-click on the video to see the flash version.

---

### Post by Raafat1991 on 2013-01-19
> **Warren Hill said:**
> Adobe have stopped supporting Linux so old versions of Flash will still play but the normal Flash player (in ubuntu-restricted-extras) will not handle the latest version of Flash but will handle older versions.

This is why some sites work and some don't.  Chrome has a later flash player built it so will handle later flash content

Yes as you said look here :

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

---

### Post by Raafat1991 on 2013-01-19
Thank you [rrich1974]("http://ubuntuforums.org/member.php?u=1264134") and thank you everyone....Can't firefox developers handle that problem ?

---

### Post by ajiscorp on 2013-07-12
> **Raafat1991 said:**
> Hi guys....i hope all to be fine


when i enter to a site it requires from me to install adobe flash player but i don't exactly know if i have one or not ?

i can run youtube  video and any a video i see but with that site i can't .


thanks....

if you want to install flash player plugin to your firefox browser, you can download it from here [***[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)***]("http://archive.canonical.com/pool/partner/a/adobe-flashplugin/") and click on ***adobe-flashplugin_11.2.202.297.orig.tar.gz*** and you will get the adobe flash player plugin. for installation instructions you can find them at readme.txt file ("Installing using the plugin tar.gz" part).

Sorry for my bad English.... :)

Oya, for mozilla plugins folder is here /usr/lib/mozilla/plugins (i'am *ubuntu 12.04 LTS* user)....

---

### Post by canis2 on 2013-10-12
I have adobe flash player installed. BUt when i try to play video on youtube, it says Get the latest Flash player. When i go to search for latest flash, i can't find. What to do ?

---

### Post by craig10x on 2013-10-12
The adobe flash that was installed with ubuntu restricted extras is 2 years old and only gets security updates...reason is adobe no longer provides newer versions for linux....
Easiest way to always have current and up to date flash is install Google Chrome (not chromium) from google's website...adobe has an agreement with them to provide the latest flash for Windows, Mac and Linux versions of Chrome for Chrome's pepperflash plug in which comes with the browser..

On firefox, you don't have that...you are using your system's old flash...

---

