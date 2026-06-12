---
title: "Firefox v1.0.5???"
date: 2005-07-12
forum: General Help
---

### Post by petard on 2005-07-12
Any idea how long the wait is for the latest Firefox to hit the repositories?

---

### Post by manicka on 2005-07-12
As soon as it's in breezy it will probably be made available through backports

---

### Post by bored2k on 2005-07-12
By the way, I'm using it on my Windows side and I see/feel no difference at all.

---

### Post by byen on 2005-07-13
[QUOTE=manicka]As soon as it's in breezy it will probably be made available through backports[/QUOTE]
 oh crap! come on man....just got through making a clean install of the then new "1.04" just a few weeks ago... now I got to go through the trauma all over again...oh brother!

---

### Post by lotusleaf on 2005-07-13
I usually make my own .debs, it's faster than waiting for someone else to build it. :) You should try it, once you build it yourself you'll see how easy it is.

---

### Post by Seti on 2005-07-13
[QUOTE=byen]oh crap! come on man....just got through making a clean install of the then new "1.04" just a few weeks ago... now I got to go through the trauma all over again...oh brother![/QUOTE]


Am I the only one who simply downloads the package from the Firefox website, and simply installs it in the /home/username directory???

1. Download firefox-1.0.5.installer.tar.gz

2. do ```
tar xvzf firefox-1.0.5.installer.tar.gz
``` 

3. do ```
cd firefox-installer
``` 

4. do ```
./firefox-installer
``` 

Then simply use the official Firefox installer. Done.

Now if for some reason this is not a good way to go about it, I would surely like to know.

---

### Post by manicka on 2005-07-13
[QUOTE=lotusleaf]I usually make my own .debs, it's faster than waiting for someone else to build it. :) You should try it, once you build it yourself you'll see how easy it is.[/QUOTE]
 I haven't been able to downlaod the source file yet. The link on mozilla.org isn't working yet [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.5/source/firefox-1.0.5-source.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.5/source/firefox-1.0.5-source.tar.bz2)

---

### Post by XDevHald on 2005-07-13
[b]*** Resolved ***
[/b]

---

### Post by manicka on 2005-07-13
That's not the source file, it's the standard installer.

---

### Post by sal on 2005-07-13
[QUOTE=Seti]Am I the only one who simply downloads the package from the Firefox website, and simply installs it in the /home/username directory???

1. Download firefox-1.0.5.installer.tar.gz

2. do ```
tar xvzf firefox-1.0.5.installer.tar.gz
``` 

3. do ```
cd firefox-installer
``` 

4. do ```
./firefox-installer
``` 

Then simply use the official Firefox installer. Done.

Now if for some reason this is not a good way to go about it, I would surely like to know.[/QUOTE]
 tell me, if i install the source from the firefox website, will it be a new clean install or an upgrade of the current 1.0.4 in ubuntu 5.04? also when a new version comes out if i download the source for that will i be able to upgrade it from the previous one i installed.
i ask because i dont want to have a bunch of diferant version of the same app on my system.

---

### Post by byen on 2005-07-13
[QUOTE=Seti]Am I the only one who simply downloads the package from the Firefox website, and simply installs it in the /home/username directory???
1. Download firefox-1.0.5.installer.tar.gz
2. do ```
tar xvzf firefox-1.0.5.installer.tar.gz
``` 
3. do ```
cd firefox-installer
``` 
4. do ```
./firefox-installer
``` 
Then simply use the official Firefox installer. Done.
Now if for some reason this is not a good way to go about it, I would surely like to know.[/QUOTE]

I tried that buddy but ended up having 2 versions of the fox :mad: ....  so, waited out until it was added to the repos ](*,) .

---

### Post by manicka on 2005-07-13
[QUOTE=manicka]I haven't been able to downlaod the source file yet. The link on mozilla.org isn't working yet [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.5/source/firefox-1.0.5-source.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.5/source/firefox-1.0.5-source.tar.bz2)[/QUOTE]
 The source file at this link is now available.

When downloaded I'll be attempting to make my own deb of 1.0.5 using checkinstall. This will avoid having two copies of firefox that people who use the installer sometimes experience. Of course, removing the 1.0.4 deb before using the 1.0.5 installer would also alleviate this problem.

---

### Post by ikester on 2005-07-13
Why do we have to get it as a backport? Why can't an 1.0.5 version be made available  to update the 1.0.2 currently available for Hoary? Isn't that the whole point of apt-get and friends?

Where do we draw the line with updates vs. backports? When is a new (minor) version considered an update and when is it considered to be in the next release and a backport for the current?

Debian stable already has Firefox at 1.0.4 (and they're supposed to be slow).

---

### Post by wellery on 2005-07-13
Am i right in saying that even though it says that it's 1.02 it's actually 1.02 with security patches applied so it really is 1.04? I just assume it would be unsecure if the latest security updates for firefox weren't in the ubuntu repos

---

### Post by Efwis on 2005-07-13
[QUOTE=wellery]Am i right in saying that even though it says that it's 1.02 it's actually 1.02 with security patches applied so it really is 1.04? I just assume it would be unsecure if the latest security updates for firefox weren't in the ubuntu repos[/QUOTE]
from what I have read you are correct, there is a bug report on file about it when you first try to get the extensions and themes for 1.0.4. There is even a work around so that you can download the extensions and themes

---

### Post by Haegin on 2005-07-14
be well assured - we do have fox version 1.0.4

---

### Post by petard on 2005-07-16
Mercy!  Look what I started!    :grin: 

I plan on waiting for the repos to have the latest.  I don't want two versions on my laptop.  I have v1.05 on my Windo$ XP box, and that's where I do my serious surfing.  So I'll just wait a few days or so... and let the Update Manager take car of things.

---

### Post by Luggy on 2005-07-18
I hope it's not too long before its on the updates.
I recently installed Hoary and found myself unable to surf the net the way I want to.
I need adblock damnit!

---

### Post by graigsmith on 2005-07-18
Firefox is something that should be kept up to date  in the repositories.  

1. its better security for me.
2. i can't use extentions because i have the wrong version of firefox.  

please someone get the newest firefox in the repositories.  because i dont know how to install it system wide.

---

### Post by byen on 2005-07-18
Has it occured to anyone yet...how silly all this looks from a firefox-user standpoint! why dont they(mozilla and co) just figure a way where firefox can just update itself every once in a while.... I mean, dont get me wrong...I love firefox and really appretiate what they have been doing but why not get a firefox-auto update manager.

EDIT: Ok looked like a said it too fast...seems that they are working on that as we speak. 
link: [http://news.yahoo.com/s/cmp/20050714/tc_cmp/165702039/nc:1817;_ylt=AjMbmmCkEWAZkk2dl7TXSmGor7oF;_ylu=X3oDMTBiMW04NW9mBHNlYwMlJVRPUCUl](http://news.yahoo.com/s/cmp/20050714/tc_cmp/165702039/nc:1817;_ylt=AjMbmmCkEWAZkk2dl7TXSmGor7oF;_ylu=X3oDMTBiMW04NW9mBHNlYwMlJVRPUCUl)

---

### Post by raven on 2005-07-18
I would wait for 1.06 which will be released soon

read on 
[http://news.zdnet.com/2100-1009_22-5792635.html](http://news.zdnet.com/2100-1009_22-5792635.html)

---

### Post by WildTangent on 2005-07-19
> **byen]Has it occured to anyone yet...how silly all this looks from a firefox-user standpoint! why dont they(mozilla and co) just figure a way where firefox can just update itself every once in a while.... I mean, dont get me wrong...I love firefox and really appretiate what they have been doing but why not get a firefox-auto update manager.

EDIT: Ok looked like a said it too fast...seems that they are working on that as we speak. 
link: [url]http://news.yahoo.com/s/cmp/20050714/tc_cmp/165702039/nc:1817 said:**
> 
i know for a fact that the windows version displays an update icon a little while after the new version is out.

-Wild

---

### Post by Lord Illidan on 2005-07-19
[QUOTE=graigsmith]Firefox is something that should be kept up to date  in the repositories.  

1. its better security for me.
2. i can't use extentions because i have the wrong version of firefox.  

please someone get the newest firefox in the repositories.  because i dont know how to install it system wide.[/QUOTE]

You can use extensions..

Using firefox, enter about:config in the url bar. Then change general.useragent.vendorSub to 1.04

You can then download themes and extensions...

Personally, apart from security issues, there is not that much of a change over 1.02, or 1.03, I think...

---

### Post by Kimm on 2005-07-19
I downloaded and installed 1.0.5 over my past installation yesterday and I experiance that this acctually speeded up firefox, it's alot more stable! That might be because its built for i686 and not i386 though...

---

### Post by graigsmith on 2005-07-21
someone had me change the user agent version in firefox, and i can go to the extention pages after that.  also it looks like the new version of firefox in synaptics, also does that, but puts the newest version in there for you.

---

