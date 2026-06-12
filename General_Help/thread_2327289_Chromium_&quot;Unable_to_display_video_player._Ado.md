---
title: "Chromium &quot;Unable to display video player. Adobe Flash Player is either not installed&quot;"
date: 2016-06-09
forum: General Help
---

### Post by morgoth2 on 2016-06-09
Hey. I was trying to watch a video on niconicodouga and chromium says


[B]Unable to display video player.
Adobe Flash Player is either not
installed or an outdated version.
[/B]
I have the latest flash installed. How do I fix this?
Thanks

---

### Post by X-RED_Tech on 2016-06-09
It works in mine with [FONT=Arial, Helvetica, sans-serif][COLOR=#333333]Adobe Flash [/COLOR][/FONT][FONT=arial][COLOR=#333333]21.0.0.242.

How did you install flash?[/COLOR][/FONT]

---

### Post by morgoth2 on 2016-06-09
I tried to do it via the terminal but it said it already has the latest version.

---

### Post by X-RED_Tech on 2016-06-09
[https://www.adobe.com/software/flash/about/](https://www.adobe.com/software/flash/about/) <- You can check your version here by opening it in Chromium.

Please post the exact commands... Saying "via terminal" is akin to this dialogue:
Question: What route have you took for your trip?
Answer: I drove my car.

---

### Post by morgoth2 on 2016-06-09
[http://postimg.org/image/qq93vf9mz/](http://postimg.org/image/qq93vf9mz/)
What am I supposed to be seeing here?
I am using ubuntu on a sony laptop.
Also I installed flash by adding this on terminal
[PHP]sudo apt-get install flashplugin-installer[/PHP]

---

### Post by QLee on 2016-06-09
> **morgoth2 said:**
> Also I installed flash by adding this on terminal
[PHP]sudo apt-get install flashplugin-installer[/PHP]

That isn't going to work, as you have found, it installs the old unuseful version. If you want the newer version like poster X-RED_Tech then consider installing these four packages.

adobe-flashplugin
Description: Adobe Flash Player plugin
Adobe® Flash® Player is a cross-platform, browser-based application runtime
that provides uncompromised viewing of expressive applications, content, and
videos across browsers and operating systems.
.
This package provides plugins compatible with both Chromium and Mozilla based
web browsers

adobe-flash-properties-gtk
Description: GTK+ control panel for Adobe Flash Player plugin
Adobe® Flash® Player is a cross-platform, browser-based application runtime
that provides uncompromised viewing of expressive applications, content, and
videos across browsers and operating systems.

This package provides the GTK+ control panel for the Flash plugin.

pepperflashplugin-nonfree
Description: Pepper Flash Player - browser plugin
This package will download Chrome from Google, and unpack it to make the
included Pepper Flash Player available for use with Chromium. The end user
license agreement is available at Google. 

browser-plugin-freshplayer-pepperflash
Description: PPAPI-host NPAPI-plugin adapter for pepperflash
The main goal of the project is to get PPAPI (Chrome) plugins
working in Firefox (and any other web-browser supporting NPAPI plugins).
It implements a wrapper which behaves like
browser to PPAPI plugin and implements NPAPI plugin interface
for browser to use.
.
This particular implementation doesn't implement any sandboxing,
which means any malicious code can break through plugin security
as there are no additional barriers. This is the same level of security as
NPAPI Flash have.
.
Flash plugin for Linux provided by adobe stopped at version 11.2; for
chrome/chromium users there is pepperflash plugin but it's not supported by
firefox/iceweasel/other browsers.
.
This package allows one to use the Pepper Flash plugin from Chrome
in NPAPI web browsers.

With these I can view flash sites with either Firefox or Chrominum.

Two of them are from the "Ubuntu partner" repository so check if you have it enabled. Consider that lack of sandbox description and decide if you still want flash.

---

### Post by X-RED_Tech on 2016-06-09
You're supposed to see your installed version which isn't the latest if any at all. It couldn't be the latest with that installer either.

The laptop's brand is totally irrelevant; the Ubuntu version you didn't mention might be important. Perhaps you should read this [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475) before opening a new thread.

Anyway... This should work for all supported versions:
1. Enable the Partners repository (Settings -> Software Properties in 16.04)
2. ```
sudo apt-get update
sudo apt-get install adobe-flashplugin
```


-Or -

Download and install Google Chrome which comes with the latest Flash for your convenience. If you don't care about the Google proprietary things it has, it's by far the most convenient option.


(EDIT)

Ninja'd by QLee... Please follow HIS post as it is more complete and thorough.

---

### Post by QLee on 2016-06-09
@X-Red

Ya, thorough, that's me. So much so that people often get tired of listening to me before I finish. ;-) You would have arrived at the same point, you do good work. I just happened to have the info handy.

---

### Post by morgoth2 on 2016-06-10
Thanks a lot you guys. After enabling the repositories and following your advice, I'm able to watch vids on nicovideo.
My version now is 21,0,0,242 (I don't know why it shows commas instead of dots, olol)

QLee, you have been more than thorough ,thanks.  I am using this 2009 laptop for web browsing only, so flash is kind of needed. I have heard about HTML5 and other plugins like H-26x for videos but it's too technical for me hehe.

X-RED_Tech, your advice was heeded. :D Not that it's relevant anymore but my version is 15.10 ubuntu. I have read some really scary reviews of the new update so I haven't updated yet. (Should I?)

I should have been more analytical with my post, true. I have used ubuntu for a month in 2008 when the problems were even worse than trying to play crysis on a calculator. I remember having to select manually that I wanted headphones output from the audio settings, or else it wouldn't play right.

My experience with computers is pretty good but I am not that well versed in linux. Since all I do with this is watch youtube when I'm having lunch, I switched from vista (ughhhh) to ubuntu because it's lighter on the hardware, and much quicker. I've always loved how ubuntu looks too. I have to say the layout and fonts of ubuntu look much better than vista too. I like the whole philosophy of linux too. I know ubuntu is proprietary now but you know what I mean.

---

### Post by oklokl on 2016-06-10
```
sudo apt-get install synaptic
```

Search
Flash Player or.. adobe
install ^^.. easy
and.. user account Logout you system
all close.. 
re login
[https://www.youtube.com/watch?v=pTHDeumP8JE](https://www.youtube.com/watch?v=pTHDeumP8JE)

---

### Post by morgoth2 on 2016-06-11
thank you rilakkuma sama

---

