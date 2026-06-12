---
title: "Firefox doesn't display IMG TITLE attribute as tooltip"
date: 2007-06-26
forum: General Help
---

### Post by dmonner on 2007-06-26
Hi all,

I've been having this problem for a while (before and after my upgrade from Edgy to Feisty). Firefox will not display the IMG tag's TITLE attribute as a tooltip. I have had confirmations from Windows and Mac users that Firefox does indeed display the TITLE attribute as a tooltip for them, as it should.

I've tried installing the "Long Titles" extension as a fix, but it didn't help. I have also started Firefox in Safe Mode (firefox -safe-mode), but it made no difference. I'm using Firefox 2.0.0.4 on an up-to-date Feisty.

So, can some people chime in and let me know if they have this problem? If you're not sure, visit the following page and mouse over the image of the comic:

[http://www.xkcd.com/c123.html]("http://www.xkcd.com/c123.html")

If tooltips are working, you will see this text (or a shortened version thereof) pop up as a tooltip: "You spin me right round, baby, right round, in a manner depriving me of an inertial reference frame.  Baby."

If nothing pops up, tooltips don't work. Could a few people please test this and let me know if it works for you or not?

---

### Post by letkemanp on 2007-06-26
I'm pretty sure that is the a FireFox thing because the same thing happens with FireFox and Windows XP. Right Click on the image and choose properties and you will see the alt text from the image. The "Title" attribute does display fine on my system, but not all of the text is displayed. As a web developer of sorts (more than 6 years for a local company) I should inform you that not all browsers support all tags equally.  And sad as the case may be more people tend to use Microsoft Internet Explorer than FireFox. 

I think the solution to your problem may be to add a JavaScript onmouseover/onmouseout function/event to your page. However this is not the best forum for that and I don't have anything handy at the moment.

---

### Post by dmonner on 2007-06-26
letkemanp: You said that Firefox does display title text on your system - are you using Ubuntu Feisty? You also said that Firefox on Windows XP doesn't display... what? Title text, or alt text? You seem to use the terms interchangeably in your post. I'm aware that Firefox does not (and should not) display alt text in a tooltip, but the Mozilla site claims that Firefox will display the title text as a tooltip.

By the way, I'm not investigating this due to my own web pages, but instead because of annoyances on certain websites I frequent, such as [XKCD]("http://www.xkcd.com") and [Dinosaur Comics]("http://www.qwantz.com"). I know that Firefox on other platforms supports this correctly, and since Firefox is designed to be more or less uniform across operating systems, I figured there might be a setting somewhere that I was missing.

---

### Post by speaker219 on 2007-06-26
0_0

---

### Post by outofnicks on 2007-06-27
I see a clipped version of the text, ending "in a manner depriving me of a...".
Firefox 2.0.0.1 in Dapper, no extensions besides FireFTP.

---

### Post by dmonner on 2007-06-27
speaker219, outofnicks: Thanks for your input. This problem is obviously not pervasive across Linux builds of Firefox.  As I've gotten nowhere on the Mozilla forum asking if there is a setting for displaying the title text, I must begin to think that there might be some conflict somewhere with other software I'm using; the most likely candidate seems to be the window manager. However, I have this problem in all the WMs I have installed, namely Metacity, Beryl, and Compiz. Now that I think about it, though, other programs like the panel and Eclipse have no trouble showing tooltips, so it doesn't really seem like an environment problem. Just as a check, though, what WMs are you using?

Would you guys mind posting your prefs.js and user.js (if you have it - I don't) from ~/.mozilla/firefox/<your_profile_directory>/ ? I will diff them with mine to see if there are any significant configuration differences.

---

### Post by strabes on 2007-06-27
If I remember correctly there's a setting in gconf-editor for the gnome-panels under metacity about tooltips or something. I don't think that it would affect firefox but it's worth a try. When I used gnome + beryl I remember disabling it because the gnome-panel tooltips were messing something up. Sorry, I don't exactly remember; it was a long time ago.

---

### Post by speaker219 on 2007-06-27
Here's my prefs.js, i can't find my user.js 0_0
also, i'm using the following extensions:
AdBlockPlus
All-In-One Gestures
Fasterfox
Greasemonkey
MediaPlayerConnectivity
Stylish
Although, i'm pretty sure it worked without any extensions installed.

---

### Post by dmonner on 2007-06-27
strabes: I think I found your setting: /apps/panel/global/tooltips_enabled. But it was already on, and panel tooltips are working fine. As you said, I don't know why it would make a difference for Firefox anyway. But thanks for your input!

speaker219: Thanks for the file. Unfortunately I didn't see any settings differences that looked like they would make a difference...

Well, I'm stymied. I can't think of anything else to try. Let me know if you have any further ideas...

---

### Post by Brucevdk on 2007-06-27
> **dmonner said:**
> speaker219: Thanks for the file. Unfortunately I didn't see any settings differences that looked like they would make a difference...

Perhaps *browser.chrome.toolbar_tips* is set to *false*. Modify it to *true* using *about:config*.

---

### Post by speaker219 on 2007-06-27
> **Brucevdk said:**
> Perhaps *browser.chrome.toolbar_tips* is set to *false*. Modify it to *true* using *about:config*.

I don't see how that setting could've gotten changed but I can confirm that it is "true" on mine, and the tooltips do show up.

---

### Post by dmonner on 2007-06-27
Brucevdk: I am in your debt, sir. browser.chrome.toolbar_tips was indeed set to false, although to repeat speaker219's sentiment, I have no idea how that happened.

Problem solved! :)

---

