---
title: "Firefox crashes as soon as it tries to load a page"
date: 2008-02-18
forum: General Help
---

### Post by whakim on 2008-02-18
Hi,

Using Gutsy on a barnd-new Compaq Presario C751NR laptop. So far the install has been working pretty well, but all of a sudden after the latest round of updates yesterday (using Synaptic) Firefox crashes as soon as it is started & tries to load a page. I haven't been able to use it at all & have never seen anything like it -- I load Firefox, key in a URL or click a bookmark, & poof! Firefox vanishes. 

I tried renaming my profile folder so it would have to start with a new one -- no luck. As soon as I try to load a webpage it vanishes. Epiphany & Opera work so I can at least use the Internet. 

Prior to these updates everything was working just fine. Is anyone else having this problem? Any suggestions? I miss Firefox, clunky memory hog though it may be...

Thanks in advance!

---

### Post by UK-Wobbie on 2008-02-18
> **whakim said:**
> Hi,

Using Gutsy on a barnd-new Compaq Presario C751NR laptop. So far the install has been working pretty well, but all of a sudden after the latest round of updates yesterday (using Synaptic) Firefox crashes as soon as it is started & tries to load a page. I haven't been able to use it at all & have never seen anything like it -- I load Firefox, key in a URL or click a bookmark, & poof! Firefox vanishes. 

I tried renaming my profile folder so it would have to start with a new one -- no luck. As soon as I try to load a webpage it vanishes. Epiphany & Opera work so I can at least use the Internet. 

Prior to these updates everything was working just fine. Is anyone else having this problem? Any suggestions? I miss Firefox, clunky memory hog though it may be...

Thanks in advance!

Have you had a go reinstalling Firefox? :) 
Your book makes will be OK! Only the Firefox data files will be reinstalled.
Go to System -> Administration -> Synaptic Package Manager, Put in Firefox in your search box.
And right click on Firefox and click on uninstall.

Reboot your Computer, Go back to Synaptic Package Manager and reinstall Firefox, 
Hope for the best that will work! :)

---

### Post by whakim on 2008-02-18
Tried it. No luck. Removed Firefox through Synaptic, rebooted, reinstalled, rebooted, & exactly the same problem. I key in a URL, hit enter, & Firefox vanishes. 

Sigh. Now what? I can't think of anything else to try...

---

### Post by y-lee on 2008-02-18
Post the error messages you get when you run firefox from the terminal.

```
firefox
```

---

### Post by whakim on 2008-02-19
This is what I get:

wafa@Wanderer:~$ firefox

(gecko:5741): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 12'
Segmentation fault (core dumped)


A font? How weird is that. I checked the font settings & there is nothing unusual; they are set to the default serif/sans-serif. (Especially now since I renamed my profile folder.) 

I did copy my Windows fonts over into ~/.fonts, but I have done that many times before on other systems & it has never caused a problem.

---

### Post by y-lee on 2008-02-19
> A font? How weird is that. I checked the font settings & there is nothing unusual; they are set to the default serif/sans-serif. (Especially now since I renamed my profile folder.)

I did copy my Windows fonts over into ~/.fonts, but I have done that many times before on other systems & it has never caused a problem.


Very Odd, but I googled it and a ton of people are having this same sort of error :(

Try the code below which i found, on [www.holik.at/]("http://www.holik.at/")

```
dpkg-reconfigure libcairo2 libpango1.0-common
fc-cache -fs
update-pangox-aliases
```

Looks like to me these need to run as root, either in a root terminal or with sudo in front of.


**EDIT:** This assumes  I think you are running Gusty, if you don't have  libcairo2 or  libpango1.0-common and are not running gusty let us know what version of ubuntu you have and maybe what firefox.

---

### Post by whakim on 2008-02-19
I do have both & I ran them with no error messages. I think Firefox is working now (don't have Internet access on the laptop at the moment, so I tested it on locally saved HTML files...will confirm this in a few hours). 

On the other hand, I think I need to start another thread because a new problem has cropped up out of the blue -- fonts in a non-Gnome, X-windows application (Stata) are an unreadable mess, & Stata crashes when I try to modify them. (e.g. if I try to increase the size to make them legible) Stata was also working fine before this latest round of updates. What on earth seems to be going on? Is this part of the same problem? Do I start a new thread?

---

### Post by y-lee on 2008-02-19
> think I need to start another thread because a new problem has cropped up out of the blue -- fonts in a non-Gnome, X-windows application (Stata) are an unreadable mess, & Stata crashes when I try to modify them. (e.g. if I try to increase the size to make them legible) Stata was also working fine before this latest round of updates. What on earth seems to be going on? Is this part of the same problem? Do I start a new thread?

Yeah you might want to start a new thread on the Stata issue, I'll google it but I never even heard of that app.:lolflag:

The code:

```
dpkg-reconfigure libcairo2 libpango1.0-common
fc-cache -fs
update-pangox-aliases
```

should have been harmless enough we are just reconfiguring the font info is all that does. Maybe reinstalling stata would help :confused:

---

### Post by y-lee on 2008-02-19
the Stata issue is outta my league but it may have something to do with 

> Unfortunately Stata only supports ASCII fonts. If you use a Unicode font, then it will not show up correctly in Stata


See  [Stata and accents (diacriticals)]("http://cluelessresearch.com/2007/05/stata-and-accents-diacriticals/"), unfortuantely that is from a Mac user may or may not help, may or may not be your problem :confused:

Anyway let us know on the FF issue :)

---

### Post by whakim on 2008-02-19
I don't think the fact that it's Stata or Matlab or whatever is relevant....it just uses basic GTK 1. That's why I suspected the fonts, especially since this started right now. (everything was fine earlier.) 

Would those commands have converted my ASCII fonts to Unicode? That would be bizarre. Anyway I'll take your advice & start a new thread if I can't fix it on my own. I strongly suspect something has messed up the GTK fonts.

---

### Post by y-lee on 2008-02-19
> Would those commands have converted my ASCII fonts to Unicode?

I doubt it :)

---

### Post by whakim on 2008-02-20
Thanks for the Firefox fix! I've tested it fully now & it works. So that's one big problem fixed, yay.

---

### Post by y-lee on 2008-02-20
Glad that worked and hope you can get your other issue fixed :)

If you are sure FF is fixed mark this thread as solved, (thread tools at the top of the posts) makes the forums easier to use ;)

Good luck!

---

### Post by bartman on 2008-03-30
Thanks, the above 3 commands resolved the same issue for me. I believe the problem was caused by *msstcorefonts* which I installed for wine.

---

