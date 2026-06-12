---
title: "Firefox scrolling/load slowness"
date: 2007-01-08
forum: General Help
---

### Post by beanbrain on 2007-01-08
Hello,

I'm experiencing extremely slow scrolling and page loading in Firefox on some sites, especially the following:

- Google Maps (map dragging)
- Digg
- Dojo Toolkit ([http://dojotoolkit.org/](http://dojotoolkit.org/) examples)

The common denominator in these three cases is extensive use of JavaScript. When one of the above sites is first loading in one tab, other tabs become inaccessible, scrolling of the site is slow, etc.

I've searched the archives here without finding an answer. Can anyone suggest why this may be occurring and how it might be corrected? I can access the same sites using Firefox on XP without difficulty, but FF in Ubuntu falls down. [BTW this is Ubuntu 6.10 w/ FF 2.0.]

Thanks!

---

### Post by scrooge_74 on 2007-01-08
Maybe this can help some

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by beanbrain on 2007-01-08
Mr. Scrooge,

I can't access the gwos site, but I found similar instructions for disabling ipv6 here:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
[The first solution didn't work for me and I still could find the 'inet6' reference using grep after rebooting. Then I tried the solution outlined for Dapper and this worked. Again this is on 6.10.]

My Google Maps dragging slowness is still a problem, but I believe Digg and the Dojo Toolkit example pages are loading much faster now. [Maps dragging is via my ALPS touchpad, and I've already had to do some configuration of this as per other posts here, so perhaps some further tweaking is in order.]

Anyway, God Bless You Ebenezer Scrooge! ;)

---

### Post by scrooge_74 on 2007-01-08
Glad to hear things are improving.. 

I really don't use Google Maps but have you check you have 3D acceleration working? When in the past I tried to use Goggle earth it was alwais slow because I had not install the drivers for my Nvidia. 

Good Luck with this

---

### Post by bartek on 2007-01-11
Same issues here on both Gecko browsers (FF and Konqueror). Scrolling is painful, CPU usage through the roof and occasional freezing. Some js-heavy RSS feeds (digg) are just as terrible in Thunderbird. I use a powerful machine, this should not happen (Core 2 6600 / 4 GB RAM)

Any other ideas how to get around it / fix it?

---

### Post by scrooge_74 on 2007-01-11
You could be having a RAM issue or a HD  starting to act up. In the past if a PC of mine had freezes or very strange behavour was the begining of hardware failure.  Coul also be that the air flow inside is not good enough and the processor is heating up in a dangerous way.  

I few weeks ago an old PC of mine started to get slower and would freeze from time to time, in the end the processor just overheated and that was it for that PC

---

### Post by bartek on 2007-01-12
There are no hardware issues here at all. This only happens on js-heavy pages in Firefox, Konqueror and Thunderbird. "Freezes" last about a second or two - it doesn't freeze the machine. Browsing and scrolling just feels really sluggish. Not used to it as this is a very fast machine. Didn't experience this in Firefox and Thunderbird under Windows on the other computer....

---

### Post by kerry_s on 2007-01-12
Do you have java installed? Perhaps it's because it can't find it?

enable multiverse repos and->
sudo apt-get update
sudo apt-get install sun-java5-plugin

or you can try just unchecking java in preference but leave java script enabled.

---

### Post by fiveryanfrenzy on 2007-01-26
I'm having similar problems with slow scrolling in firefox, especially on pages with transparent tables and of course, google maps.

The IPV6 fix is for the connection and for people with older net hardware, this is not a connection problem as the things load very fast but it seems more like a graphics problem.

Any ideas on how to fix it?

---

### Post by occams_beard on 2007-01-26
Same here. Firefox and especially Thunderbird are noticeably slower under Ubuntu than they under XP. 

By slow I mean scrolling, resizing, etc. They just seem graphically sluggish... Not to the point of being unusable, but certainly to the point of being irritating.  In fact, this seems to be the case for all GTK (and some QT) based apps. These toolkits just don't seem to be able to compete with the performance of Win32. Sadly, this has been the case for as long as I've used Linux- since about 1998, and its one of the main reasons why I don't use Linux on the desktop full time.

---

### Post by scrooge_74 on 2007-01-26
Video drivers issue maybe?

---

### Post by fiveryanfrenzy on 2007-01-31
Hey I fixed mine all I had to do is get the right drivers for my 3D card installed and stuff.  Now the graphics are smooth as can be.

---

### Post by bartek on 2007-01-31
Which card do you have and what did you install?

---

### Post by beanbrain on 2007-02-04
I still have the GMaps scrolling problem, and like others here assume it's video driver-related. I did start to go down that path after my original post, but it turned into one of "those" issues that could take several days to resolve (if ever). I had no problems with this on XP and have a fast machine with plenty of RAM.

For now I'm just accepting this as a compromise I have to make to use Linux. Overall, though, I'm happy with my new OS.

---

