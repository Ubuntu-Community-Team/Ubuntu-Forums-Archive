---
title: "How do I install Adobe Flash in Chrome (Idiots guide please!)"
date: 2019-03-07
forum: General Help
---

### Post by ukneil on 2019-03-07
Flash works fine in Firefox but I need to install it in Chrome so Amazon Associates widgets work on my web site. Could someone give a kind and gentle step by step guide on how to do this. I think I have downloaded it but don't know where to extract it. I am using 18.04 
Many thanks

---

### Post by Dennis N on 2019-03-07
If you install the **adobe-flashplugin** package, it should provide the correct flash plugin. You need to enable the "Canonical Partners" repository in Software & Update utility to get it.

---

### Post by ukneil on 2019-03-07
Thank you adobe is installed but only on Firefox

---

### Post by deadflowr on 2019-03-07
You have to now enable flash every time you use it for every site you use on chrome, per chrome instance.
Click on the lock icon in the address bar and set flash to allow.

If no Flash option directly in the lock icon's pop up window that means flash isn't already installed.
To install, in same pop up box go down to site settings and click on it to open chrome settings page.
Then go down to Flash and toggle it to allow. Then close the page.
Back in the page you wanted to enable flash for click on the reload button that will show under the address bar.
Now the flash window box should say you need to restart chrome, so close chrome and restart it.

Now you should see the Flash setting in the lock icon pop up window, set it to allow and click on the reload button that shows under the address bar.

This is the new way to use flash on chrome.
So every time...

Edit: adding reference to flash setting changes:
[https://productforums.google.com/forum/#!topic/chrome/65DliZsqoME;context-place=topicsearchin/chrome/flash]("https://productforums.google.com/forum/#!topic/chrome/65DliZsqoME;context-place=topicsearchin/chrome/flash")

---

### Post by ukneil on 2019-03-07
I am still unsure of how to install it. it works in firefox but nt chrome

I have been to [http://isflashinstalled.com/](http://isflashinstalled.com/) in my chrome browser but it says it is not installed

---

### Post by deadflowr on 2019-03-07
It installs automatically once you set it to allow in the settings page.
You need to restart chrome in order for it to run.
The you need to set it to run every time.


If you don't see a lock icon it should be a circle with an exclamation point in it.
(The address bar might also say Not Secure next to the icon.)
Just click on that.

---

### Post by ukneil on 2019-03-07
yes - it is all set to allow but i don't believe the plugin is installed. could someone please put some simple instructions on how to install Flash for Chrome on ubuntu 18.04 it works fine on Firefox

---

### Post by deadflowr on 2019-03-07
Did you restart chrome?

---

### Post by ukneil on 2019-03-07
yes i did.

---

### Post by deadflowr on 2019-03-07
See if following these help
[https://helpx.adobe.com/flash-player.html]("https://helpx.adobe.com/flash-player.html")
[https://support.google.com/chrome/answer/6258784]("https://support.google.com/chrome/answer/6258784")

---

### Post by ukneil on 2019-03-07
yes thats everything i did before. thank you anyway.

---

### Post by ukneil on 2019-03-07
That is what i have tried a few times before. I am sure there must be a specific google chrome folder that the files should be extracted to.

---

### Post by deadflowr on 2019-03-07
For joys open
chrome://components
and see if a listing for Adobe Flash is there
Just copy and paste this into the address bar
 ```
chrome://components/
```

---

### Post by ukneil on 2019-03-07
no - its not listed

---

### Post by Dennis N on 2019-03-07
Are you trying to use the same plugin that Firefox uses? Chrome/Chromium and Firefox use a different type of flash plugin. The adobe-flashplugin package will install the correct plugin type for BOTH browsers (if they are present) in the correct locations.

---

### Post by ukneil on 2019-03-07
no - i have definitely tried installing the chrome flash plugin as per previous instructions.

---

### Post by Dennis N on 2019-03-07
Here is the location:

```
dmn@Roxanne:~$ ls -1 /usr/lib/adobe-flashplugin/
libflashplayer.so
libpepflashplayer.so
manifest.json

```

libpepflashplayer.so is the one for Chromium-based browsers like Chrome.

---

### Post by ukneil on 2019-03-07
i have the same files and attached a screenshot.

---

### Post by Dennis N on 2019-03-07
Pages like isflashinstalled.com will say NO unless you have flash set to ALLOW for that web site. Did you do that? Click on left end of address bar to check if its allowed. See the attached image. Click on 'site settings' to set Flash to 'Allow'.

Be sure to reload the page after setting.

---

### Post by ukneil on 2019-03-07
yes - its all set to allow and i reloaded it. still says Nope!

---

### Post by Dennis N on 2019-03-07
Out of ideas here. I used Chromium for the examples, but as far as I know, Chrome should behave the same, since Chrome is based on Chromium. Did you try restarting the browser after installing the flash player?

---

### Post by deadflowr on 2019-03-07
Might this be the chromium snap package version?
open a terminal and check if chromium is listed from 
```
snap list
```

---

### Post by Dennis N on 2019-03-07
One other possibility - I noticed there is another plugin folder for Chromium browsers. 

/usr/lib/chromium-browser/plugins

You might try putting a copy of the plugin in this folder. Then restart the browser.

---

### Post by ukneil on 2019-03-07
I did and even rebooted my laptop. Its a strange one. Thank you for trying though. Very much appreciated.

---

### Post by ukneil on 2019-03-07
I tried copying the files directly into that folder and restarting chrome but no joy.

---

### Post by monkeybrain20122 on 2019-03-07
Chrome comes with flash bundled. The flashplayer package in repo only works on Firefox (maybe Chromium?) To see this go to 
~/.config/google-chrome/PepperFlash 
you should see the directory with some numbers on it (flash version), flash is inside.

If you don't see anything, open Chrome, type in the url bar
```
chrome://components/
```

then go down to Adobe Flash Player and click check update.

---

### Post by ukneil on 2019-03-07
i don't have the folder you mentioned.

also I have attached a screenshot of the components

---

### Post by monkeybrain20122 on 2019-03-07
Well you don't have chrome. That is chromium.

Chromium is a crippled, poorly maintained out of date alpha/beta version of chrome. I would get the real thing or stick to Firefox.[https://www.google.com/chrome/](https://www.google.com/chrome/)

Ps: It strikes me as comical that some people choose Chromium because it is open source yet go through great length to hack it so they can get the proprietary stuffs from chrome such as flash and pdf reader. If open source is important then just stick to firefox, it is a better browser than chrome or chromium anyway /rant

---

### Post by ukneil on 2019-03-07
aha! - i just tried looking in Software and Updates and its not there. Whats the est way to download it?

---

### Post by monkeybrain20122 on 2019-03-07
use the link I posted choose ubuntu 64 bit deb. download then click on it to install

---

### Post by ukneil on 2019-03-07
yey!!! its done. thank you so  very much to all involved! Its appreciated! I am going to fast for a month now to atone for my madness!

---

