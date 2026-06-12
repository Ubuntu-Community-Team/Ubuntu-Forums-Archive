---
title: "Frustrated with Firefox 64 bit"
date: 2008-06-13
forum: General Help
---

### Post by Majorflam on 2008-06-13
I'm starting to get really frustrated with Firefox 64bit version which I am running on an AMD system with latest Ububtu release.

The media in the BBC website keeps crashing the browser. Is there any workaround for this, as I use the BBC a lot?

---

### Post by Zorael on 2008-06-13
Firefox 3 doesn't work well with Flash; this is a known issue. The easiest workaround is to, well, not use FF3 for the time being. FF2 works for me with no major issues, but then I haven't tried the release candidate of FF3 yet. Perhaps it works better.

There are a gazillion threads on Firefox 3 and Flash over at the 64-bit forum, check those.

---

### Post by Joeb454 on 2008-06-13
It works fine over here :confused:

I can't comment too much on the BBC website, as I only usually use it for the news section

---

### Post by Sef on 2008-06-13
> The media in the BBC website keeps crashing the browser. Is there any workaround for this, as I use the BBC a lot?

By media, do you mean video, radio, or something else?  I can watch videos with no problem.  If I know what you are having problems with, I will check it out and see if I have the same problem.  I also have [Opera]("http://www.opera.com/") installed, and it works fine with bbc.

---

### Post by Majorflam on 2008-06-13
Firefox isn't working with BBC pages with any kind of flash in it. I can't get Firefox 2 to work, I just get 404 errors with every page.

I installed Opera, but that won't even access any links on the page, all I get is the home page and all links refuse to load!

Youtube doesn't show any vids with FF3 or Opera either.:(

---

### Post by Nepherte on 2008-06-13
This is a problem with your *flashplugin*, not your browser.

---

### Post by Majorflam on 2008-06-13
How would I resolve a problem with flashplugin?

---

### Post by Zorael on 2008-06-13
Send in a bug report to Adobe and hope they *deign* to fix it in Flash 10. It still works with Firefox 2, so again, using that for the time being is a valid alternative.

---

### Post by Nepherte on 2008-06-13
It works for me as well with the following: Firefox 3 RC1 + X86_64 AMD.

Try this:
```
sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree libflashsupport
```

---

### Post by joshsmith on 2008-06-13
try this:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
basically it is upgrading to flash player 10, and upgrading alsa packages to the intrepid version

---

