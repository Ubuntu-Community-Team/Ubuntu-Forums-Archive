---
title: "Netflix and Amazon Prime will not stream even with the latest Chrome"
date: 2014-07-04
forum: General Help
---

### Post by dtlongrifles on 2014-07-04
I installed Chrome to get the latest flash player just for the purpose of watching movies on Amazon Prime because I learned after installing Ubuntu that Adobe no longer supports Linux. I still couldn't stream Amazon but I did not get the error message that I used to get with Firefox or Chromium, now I get just a black video screen. I tried to go to Netflix and stream using Chrome with the latest Flash and it does not work I talked with their "help" desk and was told that Netflix would like let Linux users stream but Linux refuses to let them. That sounded like an absurd lie and I told them so. It's just more dirty pool by MS. Is anything going to be done to remedy these issues?

---

### Post by coldraven on 2014-07-04
I think you probably need this: [http://pipelight.net/cms/about.html](http://pipelight.net/cms/about.html)
I have never tried it as I don't use streaming services.

---

### Post by yancek on 2014-07-04
I don't know about Amazon but, Netflix requires Silverlight to play and you can install and use pipelight to do that.  Check the link below as to why Chrome no longer supports Silverlight which need NPAPI.  It was supported on older versions, up to 33 or 34, I can't remember. 

[http://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html](http://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html)

Go to the page below and click on Ubuntu to get instructions for installing pipelight on Ubuntu.

[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

Copy the instructions to a text file before beginning because if your browser is open during the installation, you will likely have problems after the install.  During the installation, you will need to accept the microsoft EULA for true-type fonts.  Make sure the OK tab is highlighted in red, use the tab key to highlight it.
Make sure you read the 'enable plugins' link at the bottom of that page.  Also, go to the page below, all the way at the bottom is some information on setting User Agent Switcher.  You need to identify your browser as using windows.  I found that User Agent Overrider works best but but that is on firefox.  You will have to check what is available on your browser. 


[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by jim_deadlock on 2014-07-04
I don't know if it was just me but when I tried the pipelight method it crashed so often it was unusable. I found this method much more stable, it's a modified version of Wine:

> sudo add-apt-repository ppa:ehoover/compholio
sudo apt-get update
sudo apt-get install netflix-desktop lovefilm-desktop

---

### Post by Bucky Ball on 2014-07-04
Perhaps you are missing the latest Flash. Try installing Pepperflash installing pepperflashplugin-nonfree. That will take Chromium to version 12 something, but ONLY Chromium. Firefox and everything else stay at 11.2. 

Good luck.

---

### Post by caver12 on 2014-07-04
> **jim_deadlock said:**
> I don't know if it was just me but when I tried the pipelight method it crashed so often it was unusable. I found this method much more stable, it's a modified version of Wine:

I had the opposite experience. I couldn't get compfolio at all. Pipelight works great.
If I'm not mistaken pipelight incorporated compfolio into it.

---

### Post by Frogs Hair on 2014-07-04
Chrome has removed most if not all media plug-ins except pepper flash for browser security reasons. This started around version 34.

---

### Post by yancek on 2014-07-04
Pipelight is also a modified version of wine.  With the Netflix Desktop, there would be problems if there was a previously installed version of wine according to Hoover at this site linked above.  Hoover's opinion of Pipelight seems pretty high as the link below attests: 

[https://plus.google.com/+ErichHoover/posts](https://plus.google.com/+ErichHoover/posts)

---

### Post by monkeybrain20122 on 2014-07-04
Pipelight doesn't work for Chrome any more since google has disabled all media plugin support since Chrome 35 (and Chromium 34), so nothing works any more in Chrome/Chromium other than flash and html5. 

Use Firefox.

---

### Post by monkeybrain20122 on 2014-07-04
> **Bucky Ball said:**
> Perhaps you are missing the latest Flash. Try installing Pepperflash installing pepperflashplugin-nonfree. That will take Chromium to version 12 something, but ONLY Chromium. Firefox and everything else stay at 11.2. 

Good luck.

Not the flash version, but DRM. To stream DRMed flash content you need either hal (work with flash 11.2) [https://launchpad.net/~mjblenner/+archive/ppa-hal](https://launchpad.net/~mjblenner/+archive/ppa-hal)
or install Windows flash with pipelight.

Both solutions work only on Firefox (or browsers that support Mozilla plugins) but not Chrome/Chromium.

---

### Post by Habitual on 2014-07-04
not a word about the User-Agent the OP is using. 
What about "*that*"?

---

### Post by monkeybrain20122 on 2014-07-05
> **Habitual said:**
> not a word about the User-Agent the OP is using. 
What about "*that*"?

Doesn't matter, it won't work on Chrome.

---

### Post by Habitual on 2014-07-05
> **monkeybrain20122 said:**
> Doesn't matter, it won't work on Chrome.

So, the OP is SOL?

---

### Post by monkeybrain20122 on 2014-07-05
Use Firefox.

---

### Post by Bucky Ball on 2014-07-05
> **Habitual said:**
> So, the OP is SOL?

What is SOL?

---

### Post by monkeybrain20122 on 2014-07-06
> **Bucky Ball said:**
> What is SOL?
  <snip>:)

---

### Post by QIII on 2014-07-06
Thanks, monkeybrain20122.

I already let Bucky Ball know the meaning of the Americanism.

---

### Post by dtlongrifles on 2014-07-06
The problem is partially fixed. I installed Wine, Pipelight and enabled the plugins on Firefox. I can stream Amazon Prime but not Netflix. Netflix detects that I am not using Windows and directs me to their page that states only Windows users may stream Netflix.

---

### Post by monkeybrain20122 on 2014-07-06
Install the user-agent-overrider addon for Firefox and set it to Windows/Firefox when using netflix, turn it off otherwise.
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)

---

### Post by yancek on 2014-07-06
> Install the user-agent-overrider addon for Firefox and set it to Windows/Firefox when using netflix, turn it off otherwise.

This plugin seems to work best.  I am using it on several Linux systems and they all work.  If its icon shows blue in the upper right of your Desktop, it is on.  Pretty simple to change.

---

