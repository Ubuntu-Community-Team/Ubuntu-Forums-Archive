---
title: "firefox doesn't open page"
date: 2008-07-05
forum: General Help
---

### Post by markolopa on 2008-07-05
Hi, my son wants to play with

[http://seafight.com/indexInternal.es?action=internalStart&help=true&battleTeaser=&sid=9610e6a9cd18ae4ebf1ccd8f8a6317d1](http://seafight.com/indexInternal.es?action=internalStart&help=true&battleTeaser=&sid=9610e6a9cd18ae4ebf1ccd8f8a6317d1)

but firefox does not open the game we would get by clicking on the blue square "To the battle" on the middle top of the page. Nothing happens when we click. The java plugin and flash 9 are installed. I am using the latest default firefox from Hardy:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0

I have installed all java stuff shown in

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

but the problem did not change. Disabling the popup blocker also doesn't help. 

Could you please check the page to see if you have the same problem? Do you have an idea of how I can get a solution? My son says that his friends can play the game on windows machines (don't know if with firefox or IE).

Thanks a lot!
Marko

---

### Post by nikgare on 2008-07-05
What do plugins are installed when you do **about:config** in Firefox?
Which version of Ubuntu are you running?

---

### Post by umechanism on 2008-07-05
Same problem here.  I'm trying to view animated radar images from the National Weather Service.  Each time I click the link it tells me that I need Java installed.  Of course, I've read all the above and I've installed the java nonfree plugin, java 5, and the java plugin for Mozilla but no luck (and all came from the repository).

Any help is appreciated.

---

### Post by markolopa on 2008-07-07
> **nikgare said:**
> What do plugins are installed when you do **about:config** in Firefox?
Which version of Ubuntu are you running?

The plugin list is attached.  I am running an up-to-date version of Ubuntu 8.04 Hardy Heron.

Do you get something when you click on the icon I have problems with?

Thanks a lot for your help!
Marko

---

### Post by ursahoribl on 2008-07-07
After upgrading to Hardy 8.04.1 w/ Firefox 3.0 from Gutsy 7.10 w/ Firefox 2.0.0.15, I had a similar problem with pages requiring Java/Javascript. A little web research led me to a forum (can't remember which one) where it was recommended to look at the /usr/lib folder and see if there were both a /firefox and a /firefox-3.0 folder. If yes look at the /plugins folder in each to see what files were listed. In my case, the /usr/lib/firefox-3.0/plugins folder was empty. Following the forum advice, I copied the firefox/plugins to firefox-3.0/plugins using:

sudo cp /usr/lib/firefox/plugins/* /usr/lib/firefox-3.0/plugins

This resolved my problems.

Grizzly

---

### Post by markolopa on 2008-07-07
> **ursahoribl said:**
> 
sudo cp /usr/lib/firefox/plugins/* /usr/lib/firefox-3.0/plugins



It didn't help in my case. I realize now that you have to log in to get to the page I mention. It is a free login. Could someone try it? Thanks!
Marko

---

### Post by umechanism on 2008-07-07
I followed the directions in this link and now my Java and Flash are working perfectly in Firefox 3.

[Clicky]("http://blog.clickonline.org.au/2007/04/30/ubuntu-linux-tip-of-the-day-installing-java-and-flash-on-ubuntu-firefox-and-other-browsers-fiesty-edgy-dapper-breezy/")

:popcorn:

---

### Post by markolopa on 2008-07-08
> **umechanism said:**
> I followed the directions in this link and now my Java and Flash are working perfectly in Firefox 3.

[Clicky]("http://blog.clickonline.org.au/2007/04/30/ubuntu-linux-tip-of-the-day-installing-java-and-flash-on-ubuntu-firefox-and-other-browsers-fiesty-edgy-dapper-breezy/")

:popcorn:

I've tried what you did, but all the packages were already installed. Thanks for the help!

All sites I have being to work fine except this one that my son want to use for playing. That's why I wonder if someone was ever able to play the game using the plugins available for Linux.

My son insists to install windows back, but I hate dual booting and windows administration...:mad: Please help, thanks! :)

---

### Post by nikgare on 2008-07-08
I get the box that you're supposed to click on but it doesn't do anything here, either.
It looks like it's another deficiancy of Adobes Flash for linux.
I'm using version 9 of flash here, maybe version 10 would work better

---

### Post by sevenX_fold on 2009-06-16
was this issue resolved?  I am having the same problem I cannot play seafight on latest ubuntu 9.04.

---

