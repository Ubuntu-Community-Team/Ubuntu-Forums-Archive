---
title: "Strange Firefox rendering glitch"
date: 2007-04-11
forum: General Help
---

### Post by moot on 2007-04-11
This is tough to explain, so here are 2 screen caps before the big explanation paragraph:

[IMG]http://i48.photobucket.com/albums/f203/goldencream/Random/ff.png[/IMG]
[IMG]http://i48.photobucket.com/albums/f203/goldencream/Random/ff2.png[/IMG]

Sometimes when I click on a link with either my left mouse button (Render within the same tab I clicked it in) or middle mouse button (Render in a new tab) or open up my Preferences, what you're seeing in the first screen cap happens.  A bare-bones window entitled "untitled window" with the default window icon will open with only the three minimize, unminimize, close buttons in the right side of the title bar, no scroll bar, a static rendering of about 9/10 of the page that was supposed to be rendered within the same tab I clicked it in and it'll cover up 9/10 of the window space dedicated to Firefox.  I can minimize and unminimize it just fine, and even move it over to other workspaces, but if I close it then Firefox also closes.  Meanwhile, Firefox displays a static rendering of the previous page rather than the link I clicked on, but shows the URL of the link I clicked on in the address bar, you can still see the bottom 1/10 of the previous page in that screencap.  I minimized everything then maximized only Firefox again so that you could see the address bar, but for some reason it also rendered my Desktop in the space where the previous web page should've gone and rendered everything else just fine.  I can usually fix all of this with a simple refresh or by just closing the tab, but sometimes that doesn't work on pages with frames, the problem just repeats itself and it's still annoying as hell to minimize a window then refresh every other time I click on a link.  I've had this problem every since my installation of Dapper with a fresh install of Firefox 1.5.0.x, what's causing this strange, annoying glitch and how can I fix it?  The first solution that came to mind was simply updating Firefox to Firefox 2.0.0.x, but if this can be fixed some other way I'd rather do that.


Edit: Here are my Firefox Preference settings for Tabs:

Open links from other applications in:

[Selected] a new tab in the most recent window


[Check mark] Force links that open new windows to open in:

[Selected] a new tab


[Check mark] Hide the tab bar when only one web site is open

[Check mark] Warn when closing multiple tabs


And my list of extensions:

Adblock Plus
Add N Edit Cookies
Auto Copy
ChatZilla
Download Embedded
DownThemAll!
English (GB) Language Pack
Fasterfox
Firefox Extension Backup Extension (FEBE)
FireFTP
Foxmarks Bookmark Synchronizer
Linkification
User Agent Switcher
VideoDownloader

Note that all of them are updated and compatible with my Firefox installation, and that I have had this problem even before I installed any of them.  And while I'm on the topic of extensions, are the alternatives for DownThemAll! and VideoDownloader any better than what I have now?

---

### Post by kerry_s on 2007-04-11
Have you tried with a clean profile, as in renaming .mozilla to .mozilla.old then launching firefox and doing the same things with a clean profile.

Also how is that "Firefox Extension Backup Extension (FEBE)" is it any good?

---

### Post by moot on 2007-04-11
> **kerry_s said:**
> Have you tried with a clean profile, as in renaming .mozilla to .mozilla.old then launching firefox and doing the same things with a clean profile.

Also how is that "Firefox Extension Backup Extension (FEBE)" is it any good?

1. Where exactly would I name .mozilla to .mozilla.old and how can I upgrade Firefox from 1.5.0.0.x to 2.0.0.x?

2. Firefox Extension Backup Extension (FEBE) is very good, never again will I have to worry about losing my extensions, bookmarks and preferences on either Ubuntu or Windows.  How is FlashGot compared to DownThemAll!?  And isn't having both AdBlock Plus and Flashbock kind of superfluous since ABP can also block and unblock *.swf files?

Edit: When I run sudo firefox from the terminal, which runs a clean install of Firefox, I can't get the rendering glitch to occur, but Firefox crashes whenever I view a Myspace profile.

---

### Post by kerry_s on 2007-04-11
Open nautilus and press ctrl +h and it will show your hidden files. you should than see .mozilla and can right click it to rename it.

What i do is just download firefox.tar.gz from the site and unpack it, than i just put that firefox folder in place of the installed 1 in /usr/lib and copy the plugins to the new firefox folder. I rename the orignal firefox to firefox.old till i know it's working. You need to install libstdc++5 if you want to go that route. I don't like how ubuntu handles firefox they split it into 3 parts, i don't know why, so i always delete all of it /etc/firefox, usr/share/firefox, and then the /usr/lib/firefox is the 1 i use.

I've never used download them all so i wouldn't no the difference. I use a external command line program for my downloads called axle.

I don't want to block flash completely, i want to be able to choose when it plays. flash block just replaces it with a play button, so i can click on it if i want it to play. Adblock just gives a tab you have to click on, but the flash  would still play till you click the tab.

You should not run firefox with root privileges.

---

