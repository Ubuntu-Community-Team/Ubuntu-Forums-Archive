---
title: "Flash working in both Chrome and FireFox?"
date: 2014-08-25
forum: General Help
---

### Post by Mex5150 on 2014-08-25
Hi,

I'm running FireFox 31.0 and Chrome [COLOR=#303942][FONT=Ubuntu]36.0.1985.125 on Ubuntu 12.04[/FONT][/COLOR] (32bit). Until a recent update I was able to run flash on both browsers, now it continues to work fine in FireFox, but Chrome tells me I need to install flash. After many searches, and lots of tutorials to get flash running in one or the other, I'm not sure if it is actually possible to to have it available in both browsers at the same time. I find the idea that flash can only work in one browser ridiculous, so assume my search criteria must therefore be flawed somehow. Anybody know how to fix this, and get both up and running again?

Thanks.

~Mex

---

### Post by vasa1 on 2014-08-25
Are you sure it's Chrome and not Chromium? If you are using Chrome, then Flash is definitely present but if you're using Chromium you may need some additional steps to get a functional Pepper Flash which I don't know about because I use Chrome.

If you have Chrome, fully updated, the version should be Version 36.0.1985.143 whereas you have 36.0.1985.125 which leads me to think you maybe having Chromium:
```
[11:30 PM] ~ $ apt-cache policy chromium-browser
chromium-browser:
  Installed: (none)
  Candidate: 36.0.1985.125-0ubuntu1.14.04.0~pkg1029
  Version table:
     **36.0.1985.125**-0ubuntu1.14.04.0~pkg1029 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     34.0.1847.116-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
[11:30 PM] ~ $ 
```
There have been some changes to how Chrome (and Chromium) now use plugins and so plugins (NPAPI?) that worked for Firefox and Chrome and Chromium previously will only work for Firefox.

---

### Post by grahammechanical on 2014-08-25
What is ridiculous is web site designers relying on one company's technology and that company not supporting Linux.

[http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04)

As the blog post shows the failure is due to Google making changes to Chromium. It is nothing to do with Ubuntu 14.04. Install pepper-flashplayer plugin from the software centre and then run

```
sudo update-pepperflash-plugin-nonfree --install
```

or do with two commands

```
sudo apt-get install pepperflash-plugin-nonfree
sudo update-pepperflash-plugin-nonfree --install
```

Regards.

---

### Post by monkeybrain20122 on 2014-08-25
My guess is that you are using Chromium rather than Chrome. Chrome/Chromium have recently dropped support for NPAPI plugins (including system flash) and you haven't noticed that before because Ubuntu's Chromium only update sporadically and you have been using an outdated version for which flash still worked. When Chromium finally gets updated flash stops working.

So either just uninstall Chromium and install Chrome (download .deb from google) which comes bundled with its own flash or install pepperflash following grahammechanical's instructions.

---

### Post by Mex5150 on 2014-08-25
> **vasa1 said:**
> Are you sure it's Chrome and not Chromium?

> **monkeybrain20122 said:**
> My guess is that you are using Chromium rather than Chrome.

Doh! You are both quite correct, I didn't even know they were two separate things ;^/

 > Chrome/Chromium have recently dropped support for NPAPI plugins (including system flash) and you haven't noticed that before because Ubuntu's Chromium only update sporadically and you have been using an outdated version for which flash still worked. When Chromium finally gets updated flash stops working.

So either just uninstall Chromium and install Chrome (download .deb from google) which comes bundled with its own flash or install pepperflash following grahammechanical's instructions.Don't have time tonight, but I'll try pepperflash tomorrow and report back ;^>


~M

---

### Post by Mex5150 on 2014-08-30
Hi,

I had problems with pepperflash, so installed Chrome instead. Everything works great now, thanks guys ;^>

~M

---

