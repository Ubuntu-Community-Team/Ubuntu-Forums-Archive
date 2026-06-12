---
title: "Firefox always opens in a new window"
date: 2017-03-28
forum: General Help
---

### Post by TheFu on 2017-03-28
16.04 x64 (not really run Mate, but that is as close as the choices allow); GUI is straight openbox.
Firefox 51.0.1

For the last few weeks, anytime xdg-open gets used by other programs like thunderbird or even inside firefox, the links are always opened in a new window with just that tab.  I'd like each new link to open in an existing firefox window, just inside a new tab.  Make sense?

This worked for years correctly - new tab would be opened inside an existing FF window, the expected way.

Looked up how to disable opening a new window - found a how-to at the mozilla site which references MS-Windows Firefox menus and selections which do not exist in the Linux firefox.  

And using the center mouse button to open a new tab always double opens the same tab if done from inside Firefox. If done from Thunderbird, it opens a new FF window with 1 tab.  Doing it again opens another new FF window - not another tab in the just opened window.  What's with that? 

It is droving me nuts.

I haven't tried the following yet:
* creating a new profile
* creating a new userid
Both of those would show if the issue(s) are with my FF settings or the program.

Really hoping that someone else has already solved the issue. Figure it is in an *about:config* setting somewhere.

---

### Post by deadflowr on 2017-03-28
You can open *firefox --preferences* from a terminal if you do not see it in the menu; it's in  the Edit menu item section.
(or if you do not seethe menu there is the hamburger icon in the right side area of the top toolbar(?).) which should show the preferences section as an icon.

in the General section, you can check if the **open new windows in a new tab instead** is checked or not.

See if that does anything.

---

### Post by TheFu on 2017-03-28
Thanks for the reply. 

> **deadflowr said:**
>  
in the General section, you can check if the **open new windows in a new tab instead** is checked or not.


It was checked. The Windows instructions say 
 [INDENT]Tools --> Settings[/INDENT].  
Don't know why the Linux version has always used 
 [INDENT]Edit --> Preferences[/INDENT] 
instead, but it has for 5+ yrs.
 
Toggled it. No difference.  Just knowing that it works correctly on other systems is helpful. Does it work for you, as expected?

Need some time to finish reading all my tabs before trying the new userid and new profile ideas. I'm hopeful that will fix it.  Oddly, the issue showed up on both my normal desktop AND my laptop about the same time. I don't remember exact, since I don't use the desktop every day. Also, the desktop runs 14.04.5 and the laptop is on 16.04.2.
The laptop firefox profile was copied from the desktop many years ago and 3-4 laptops ago.  I has been restored and moved forward all this time, but not re-copied from the desktop in at least 4 yrs - at least.

---

### Post by deadflowr on 2017-03-28
>  Does it work for you, as expected?
Yes, works just fine.
But this is shmunity unity, not sure how well other desktops/window managers work.
Not sure if that matters, either.

---

### Post by TheFu on 2017-03-29
```
firefox -new-tab http://imdb.com/ 
```

Doesn't work either.  Doesn't open that URL. Tested on 14.04 - 52.0.1.
Haven't done the other tests I suggested. ...creating a new userid now ...
well - crap.  **That fixed it.**  Has to be a setting/plugin running inside my main userid. Don't really have many, but I do like tabs on the left, not the top, since wide-screen monitors are all we can buy now.

Traced the issue back to a firefox addon - "**Tree Style Tabs**" - Upgraded that to a new version (recently released) and it is working again.  Been using this addon for 5+ yrs and never had an issue like this before.

---

