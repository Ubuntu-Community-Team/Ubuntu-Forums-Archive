---
title: "Firefox and websites guessing your language"
date: 2016-03-11
forum: General Help
---

### Post by SamInside on 2016-03-11
Hi.
I recently installed Xubuntu, but I post here because it's not specific to it.
I have a very minor problem that I want to share anyway, because it's weird.
I've set my language as *italian*; everything works fine, but with Firefox, YouTube and Google give a weird language behaviour.


**System information**

Xubuntu 14.04.4 LTS for amd64.
Also tested in Ubuntu 14.04.4 LTS, since I first tested the original flavor, and I got the same problem.

*locale* gives:
```

LANG=it_IT.UTF-8
LANGUAGE=it:en
LC_CTYPE="it_IT.UTF-8"
LC_NUMERIC=it_IT.UTF-8
LC_TIME=it_IT.UTF-8
LC_COLLATE="it_IT.UTF-8"
LC_MONETARY=it_IT.UTF-8
LC_MESSAGES="it_IT.UTF-8"
LC_PAPER=it_IT.UTF-8
LC_NAME=it_IT.UTF-8
LC_ADDRESS=it_IT.UTF-8
LC_TELEPHONE=it_IT.UTF-8
LC_MEASUREMENT=it_IT.UTF-8
LC_IDENTIFICATION=it_IT.UTF-8
LC_ALL=

```

Xfce is set in italian.

Firefox is up to date, and its GUI is in italian.

Firefox -> Add-ons Manager -> Languages, shows:
```

Italian (IT) Language Pack (ENABLED)
English (GB) Language Pack (disabled)
English (South Africa) Language Pack (disabled)

```
I've disabled the last two entries myself, just to see if it makes any difference, and it doesn't.
Interesting to notice that in Windows, Firefox doesn't have the *Languages* section in the *Add-ons Manager* page.

Preferences -> Content -> Languages -> Choose, shows, in this order:
```

[it-it]
Italian [it]
English/USA
English [en]

```

So, I think my settings are right. After all it's a brand new installation of Xubuntu.
Moreover, my IP returns a geolocation which various websites confirm it's in Italy.


**Problem and steps to reproduce**

On "Clear recent history" I delete everything.
I visit *[www.youtube.com]("http://www.youtube.com")* or even *[https://www.youtube.com/?hl=it&gl=IT](https://www.youtube.com/?hl=it&gl=IT)*.
YouTube is still in english, while the content it provides is correctly focused on Italy; a message says:
"You're viewing YouTube in English (US). You can change this preference below."

I could just do that; the problem is that:
1) I delete cookies all the time, so I'll have to do that everytime;
2) On Windows it doesn't happen, so it looks like some kind of bug to me, specific with Ubuntu / Linux.

On Windows 7 64-bit this doesn't happen, doing the same steps; I double checked, but I was sure about it because I used Windows since recently, and in fact I noticed this behaviour immediately when trying Ubuntu.

Last thing I'll add, I'm no expert on *about:config*, but in it I've found, looking for the keyword *lang* these two variables: *extensions.bootstrappedAddons* and *extensions.xpiState*; their value is full of stuff, compared to Windows, so they may be or may not be the cause, just reporting this.


I don't feel like filing a bug report until I see what more experienced users say about this.

Over to you.

---

### Post by QIII on 2016-03-11
Can this behavior be reproduced using a different browser, such as Chrome.

What you have described thus far does not yet point to Linux.  The browser is still a suspect.

---

### Post by SamInside on 2016-03-11
You're right.
I tested Chromium and the problem is not there.
Looks like a bug in Firefox, which for some reason is only present in Ubuntu (or in GNU/Linux OSs in general, I should test that too).

Here it is:
[http://osdir.com/ml/ubuntu-bugs/2015-12/msg11059.html](http://osdir.com/ml/ubuntu-bugs/2015-12/msg11059.html)
With a workaround that I've just tried and works fine. :)

---

### Post by efflandt on 2016-03-12
Maybe that will finally resolve an issue I have been having where Firefox spell checker occasionally assumes that I am using the Queens English (en-gb) instead of US English (en-us) even though I made sure that everything on the system and everything else I could find in Firefox was set to en-us. I appears to work for now, because when I just typed "english" it wanted me to use "English" and the dictionary did default to "English (United States)" for language.

---

### Post by SamInside on 2016-03-12
Nice.
Anyway, we should file a bug report. I'm not sure if to Ubuntu or Firefox though.

---

### Post by SeijiSensei on 2016-03-13
File it with Mozilla unless you determine the problem doesn't exist on other distributions like CentOS.

---

