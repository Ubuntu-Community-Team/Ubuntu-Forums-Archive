---
title: "Can't get flash 32bit 12.04 install"
date: 2012-11-20
forum: General Help
---

### Post by klingzw on 2012-11-20
I am at my wits end with a recent install of 12.04 on a 32bit machine. In attempts to put together a computer for a friend of mine. I am trying to dual boot Ubuntu 12.04 and Windows XP. 

12.04 Was installed via USB on an older athlon xp2800 with 1gb ram machine, integrated VIA motherboard / graphics. Install went fine, operating system works good. I installed the usual components such as restricted extras and the like. After many hours of searching this forum and reading I cannot get flash / youtube to work in either firefox or chrome. I have tried different versions of flash as per recommended  in multiple posts on this forum. Nothing has worked to date. 

If it helps, when going to youtube and selecting a video, the black / flash box never appears. Which I thought was rather strange. 

Any advice would be appreciated. I have spent so much time on this. 

Also, the fonts in Ubuntu 12.04 don't seem very crisp so to speak. To me it looks like everything is fuzzy. Both while on firefox and on general documents / word processing. Any suggestions? Monitor has been reset and the like. After a while it seems to give me a headache from eye strain.

Thank you

---

### Post by ibjsb4 on 2012-11-20
I have seen this fuzzy screen issue in the forums lately and took a look.

I was surprised at how many hits I got.  Took a look at the first three pages and here's the most popular suggestions.

video driver

kernel

refresh rate

color depth

Try live cd (usb)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fuzzy+screen&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fuzzy+screen&as_qdr=all&sa=Google+Search&lang=en)

Not really any solid solutions, good luck

---

### Post by klingzw on 2012-11-21
ibjsb4, Thanks for the response. 

I think one of the issues is lack of "other" video drivers. The graphics is integrated VIA brand on the motherboard. Going to their website, no driver exists for Ubuntu 12.04, only up to 10.04, so I may give that a try. 

Any ideas on the flash issue? I really need to get this resolved. I have tried every suggestion I found online from installing older versions of flash to using firefox ad'ons. Nothing has worked!!!

Thanks again

---

### Post by ibjsb4 on 2012-11-21
The only thing that I ever had to do to get youtube/flash to work was to install Ubuntu Restricted Extras.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=you+tube&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=you+tube&as_qdr=all&sa=Google+Search&lang=en)

Search your video card model through googlubuntu and see if you can get some forum hits on drivers.

---

### Post by klingzw on 2012-11-26
Bump for any other ideas. I have installed, removed, purged and re installed restricted extras multiple times. I have never had this much trouble getting flash working. Really need to get it finished.

Any suggestions?

Thank you

---

### Post by rnerwein on 2012-11-26
> **klingzw said:**
> Bump for any other ideas. I have installed, removed, purged and re installed restricted extras multiple times. I have never had this much trouble getting flash working. Really need to get it finished.

Any suggestions?

Thank you
hello
you remember me just now that i have the same problem. ---- but now i got it and it works.
1. go to the adobe webpage: [www.adobe.com/support/flashplayer/downloads.html]("http://www.adobe.com/support/flashplayer/downloads.html")
2. select --> Get the latest version
3. select --> APT for Ubuntu 10.04+
folling the following instructions.

on my system - lucid - it works out of the box :-)
P.S. the box where i installed it is running a intel cpu

---

### Post by klingzw on 2012-11-26
Hi Merwein, 
                        Thanks for the suggestions, I have already been down that avenue. Installed newest and older drivers directly from Adobe, no change. 

Out of curiosity I downloaded a Mint DVD and still couldn't get flash to play. Looks like I may have found one of the few video chip sets that won't work with Linux???

Any other suggestions? I would really hate to give up on this, considering how many hours I have wasted on it already.

Thanks

---

### Post by rnerwein on 2012-11-27
> **klingzw said:**
> Hi Merwein, 
                        Thanks for the suggestions, I have already been down that avenue. Installed newest and older drivers directly from Adobe, no change. 

Out of curiosity I downloaded a Mint DVD and still couldn't get flash to play. Looks like I may have found one of the few video chip sets that won't work with Linux???

Any other suggestions? I would really hate to give up on this, considering how many hours I have wasted on it already.

Thanks
do realy followed the instructions --> select newest version and then select apt-get
(when i did that there was a message to install other software too - i answerd with yes).
my system is a sony viao with 32 bit intel cpu and running 10.04 lucid.
P.S don't load an older version take the newest
good luck

---

