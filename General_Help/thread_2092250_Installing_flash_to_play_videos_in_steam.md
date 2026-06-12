---
title: "Installing flash to play videos in steam?"
date: 2012-12-07
forum: General Help
---

### Post by SteveDeFacto on 2012-12-07
When I view a game's store page I want to be able to play the videos but it always says I need to update my flash. I have flash 11.2 installed which is the last version of flash to be made for Linux so what can I do to get steam to play videos? Is it even possible?

---

### Post by pkadeel on 2012-12-07
> **SteveDeFacto said:**
> When I view a game's store page I want to be able to play the videos but it always says I need to update my flash. I have flash 11.2 installed which is the last version of flash to be made for Linux so what can I do to get steam to play videos? Is it even possible?
Your shockwave flash plugin might be disabled in your browser. have you checked that?

---

### Post by SteveDeFacto on 2012-12-07
> **pkadeel said:**
> Your shockwave flash plugin might be disabled in your browser. have you checked that?

It works fine in chrome and firefox. What do you mean?

---

### Post by rnerwein on 2012-12-07
> **SteveDeFacto said:**
> When I view a game's store page I want to be able to play the videos but it always says I need to update my flash. I have flash 11.2 installed which is the last version of flash to be made for Linux so what can I do to get steam to play videos? Is it even possible?
search google - from adobe is: 6. Nov. 2012 – Adobe *Flash Player* 11.5.502.110 Deutsch *Free*-Download kostenlos available.

---

### Post by dannyboy79 on 2012-12-07
i wonder if you have a errant libflashplayer.so located somewhere that needs to be updated with the one that's normally located within the browser folders. Totally guessing here...

---

### Post by jim_deadlock on 2012-12-07
You must be part of the beta testing group, so reporting this as a bug and/or checking their community info might be the way to go.

---

### Post by dli7319 on 2012-12-07
[http://steamcommunity.com/app/221410/discussions/0/882965239653368215/](http://steamcommunity.com/app/221410/discussions/0/882965239653368215/)

"As you may have noticed there are some problems when you are using a  64bit system & flashplayer. The current 32bit only Beta requires a  32bit Flashplayer for its browser, but it's still just looking at some  default generic directories. So here we go:

As far as 'strings' tells me there are 3 directories where Steam is searching for the Flash plugin:
/usr/lib/browser-plugins
/usr/lib/mozilla/plugins
/usr/lib/firefox/plugins
Currently working workaround: Pick one of the 3 that does not exist and  create it, then simply put the 32bit libflashplayer.so in there - every  browser should by default skip incompatible files when searching for the  plugin, so this shouldn't cause any problems with other 64bit programs  that may try to load the Flash plugin."

---

### Post by Jason80513 on 2012-12-07
Adobe no longer supports Flash for Linux, and is not releasing updates. Best bet is to uninstall the Flash player from your computer, because it won't be long before the hackers figure out how to use it to own you.

Google Chrome, not Chromium though, maintains an up-to-date version of Flash Player in Chrome for Linux. It does not use the system-installed version.

So if you want to watch Flash videos on Linux, you need to install and use Chrome. It works very well, and is the latest version. However, in the last release they removed the DRM libraries. So if you were planning on using it to watch Amazon videos, you are now completely out of luck. 

Why these guys won't just switch to HTML5 video tags is beyond me.

---

### Post by SteveDeFacto on 2012-12-08
> **dli7319 said:**
> [http://steamcommunity.com/app/221410/discussions/0/882965239653368215/](http://steamcommunity.com/app/221410/discussions/0/882965239653368215/)

"As you may have noticed there are some problems when you are using a  64bit system & flashplayer. The current 32bit only Beta requires a  32bit Flashplayer for its browser, but it's still just looking at some  default generic directories. So here we go:

As far as 'strings' tells me there are 3 directories where Steam is searching for the Flash plugin:
/usr/lib/browser-plugins
/usr/lib/mozilla/plugins
/usr/lib/firefox/plugins
Currently working workaround: Pick one of the 3 that does not exist and  create it, then simply put the 32bit libflashplayer.so in there - every  browser should by default skip incompatible files when searching for the  plugin, so this shouldn't cause any problems with other 64bit programs  that may try to load the Flash plugin."

Thanks man that worked perfectly! Cheers!

---

### Post by dannyboy79 on 2012-12-10
use the thread tools and mark it solved.

---

### Post by SeanBlader on 2012-12-21
In case the above doesn't work, the eventual solution on Page 3 of the Steam Community thread finally solved it for me.

sudo apt-get install libxt6:i386 
add libflashplayer.so to ~/.Steam/ubuntu12_32/plugins

Golden!

---

### Post by dannyboy79 on 2012-12-21
i searched for that package and only found sudo apt-get install libxt6, without the :i386 on it and there was no folder with what you listed but this location though
```
~/.steam/steam/ubuntu12_32/
```

and on top of it, it still doesn't work for me.
[IMG]https://lh5.googleusercontent.com/-7k9HoEVcEu8/UNTflGBYg7I/AAAAAAAAA0A/AeM1YsRxMVU/s800/steam_flash.png[/IMG]

---

### Post by HDave on 2012-12-28
Like Dannyboy, I tried these things and got no love.  Ubuntu 12.04 x64....

---

### Post by NikTh on 2013-01-07
It works ! 
Like SeanBlader said. 
If you cannot locate the libxt6:i386  with apt-get , try aptitude instead. 
```
sudo aptitude install libxt6:i386
``````
apt-cache policy libxt6:i386
libxt6:i386:
  Installed: 1:1.1.1-2build1
  Candidate: 1:1.1.1-2build1
  Version table:
 *** 1:1.1.1-2build1 0
        500 http://gr.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
``````
lsb_release -rcd ; uname -rm
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
3.5.0-21-generic x86_64
```Create the folder plugins ```
mkdir .steam/steam/ubuntu12_32/plugins
```copy in there the libflashplayer.so 32bit you have downloaded. 
Restart Steam.

---

### Post by NikTh on 2013-01-09
It works , even with nouveau (open source driver). 
A comparison between nouveau+nvidia 
[https://www.youtube.com/watch?v=xvkTawFCg3Y](https://www.youtube.com/watch?v=xvkTawFCg3Y)

:)

---

### Post by dannyboy79 on 2013-01-09
it wasn't that I couldn't play the game, it was merely that I couldn't play the trailer of the game within the steam window. i'll try to install that package you listed but it's not really that serious of an issue as if I want to watch a game trailer, i'd just open up my browser and search youtube for a video of the game. 

Thanks for showing us this though, i'm jealous as I only have a Nvidia 8400 GS and can't play on 1920x1080, i can still play on a decent res with medium settings though

---

### Post by NikTh on 2013-01-09
Yes I know .. post #15 is OffTopic , but rather to open a new thread I posted here :) 
I was bit excited that nouveau supports steam .. and I could play TF2 with nouveau. (even in low fps)
I have read (various Web pages) that nouveau not supports steam , that steam couldn't even open.. etc.

---

### Post by stinkeye on 2013-01-11
Just came across this in my rss feeds.
[**_[COLOR="DarkRed"]How To Get Flash Player To Work With Steam For Linux On 64bit[/COLOR]_**]("http://www.webupd8.org/2013/01/how-to-get-flash-player-to-work-with.html")

---

### Post by dannyboy79 on 2013-01-13
> **stinkeye said:**
> Just came across this in my rss feeds.
[**_[COLOR="DarkRed"]How To Get Flash Player To Work With Steam For Linux On 64bit[/COLOR]_**]("http://www.webupd8.org/2013/01/how-to-get-flash-player-to-work-with.html")it looked promising BUT it still doesn't work for me. I followed it to the "T". Still get the following.
[IMG]https://lh4.googleusercontent.com/-nQeOIyFo26g/UPLi5Br92XI/AAAAAAAABZA/9jSC_xhWVXs/s955/steam%2520flashplayer.png[/IMG]

---

### Post by Korn on 2013-01-17
> **dannyboy79 said:**
> it looked promising BUT it still doesn't work for me. I followed it to the "T". Still get the following.
[IMG]https://lh4.googleusercontent.com/-nQeOIyFo26g/UPLi5Br92XI/AAAAAAAABZA/9jSC_xhWVXs/s955/steam%2520flashplayer.png[/IMG]

Be sure to download the **32bit** FlashPlayer. The problem for me was that I downloaded the 64bit FlashPlayer.
This is the correct one:
```
korn@pc:~$ md5sum Downloads/install_flash_player_11_linux.i386.tar.gz 
b265e871269f9b3b5cebb559d58c2332  Downloads/install_flash_player_11_linux.i386.tar.gz
```

Also I put it in the **.steam/steam/ubuntu12_32/plugins/** directory.

---

### Post by dannyboy79 on 2013-01-17
i'll try again but I was positive I downloaded the 32bit flash and i obviously put it within that same folder location in my home directory.

---

### Post by myrrdinoftheforest on 2013-01-19
> **SteveDeFacto said:**
> Thanks man that worked perfectly! Cheers!


How in the world did you get this accomplished without using the command line the whole time as root? I'm so lost right now...

---

### Post by meteorrock on 2013-01-19
> **Jason80513 said:**
> Adobe no longer supports Flash for Linux, and is not releasing updates. Best bet is to uninstall the Flash player from your computer, because it won't be long before the hackers figure out how to use it to own you.

Google Chrome, not Chromium though, maintains an up-to-date version of Flash Player in Chrome for Linux. It does not use the system-installed version.

So if you want to watch Flash videos on Linux, you need to install and use Chrome. It works very well, and is the latest version. However, in the last release they removed the DRM libraries. So if you were planning on using it to watch Amazon videos, you are now completely out of luck. 

Why these guys won't just switch to HTML5 video tags is beyond me.

Is it true java stopped developing flash on linux?

---

