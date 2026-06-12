---
title: "Chromium does not open links"
date: 2016-04-30
forum: General Help
---

### Post by izznogooood on 2016-04-30
When I have Chromium as my default Browser it will not open links. When i press the link it opens but with a blank tab.

The same goes for "programs" like Plex media server which opens in a web page. The system bypasses Chromium and opens it in Firefox. 

(I have none of these issues with Google Chromeas the default browser)

---

### Post by ajgreeny on 2016-04-30
Links where?
On an already open browser page, or for example, in an email in TBird?

Also I do not fully understand your comment about plexmediaserver; where is there a link for that?
PMS is opened in a web-browser using the **[http://localhost:32400/web/index.html](http://localhost:32400/web/index.html)** address

---

### Post by izznogooood on 2016-04-30
1: Links as in an email or any other link in any other "program" as/or from launcher
2: The Plex media server ads a link to launcher which is just a local web page.

---

### Post by ajgreeny on 2016-04-30
> **izznogooood said:**
> 1: Links as in an email or any other link in any other "program" as/or from launcher
2: The Plex media server ads a link to launcher which is just a local web page.
1: You change that in the preferences of the mail client , or other application you are using; certainly that is the case in TBird.
I am not using an OS with TB on it at the moment and can't remember the exact route to the detail of changing that preference but I'll search it out as I changed the default on my system so that it asks if I want to use FF or chromium.

2: That Plex link will presumably be a .desktop file that you can edit in a text editor and make it open in whatever browser you want.  I can't recall if my installation of PMS made a link for me, but if it did, I don't use it, as I added a .desktop file to my own panel in Xubuntu which is full of launchers, rather like unity's launchbar.
Where did Plex put that link; on the unity launchbar; on the desktop; in the menu; and which DE do you use?

---

### Post by izznogooood on 2016-05-01
Your not following, the link triggers Chromium. But Chromium opens a blank page, not the link its triggered from.

This happens when i have Chromium as my default browser, but NOT when i have chrome as my default browser.

I use unity.

---

### Post by ajgreeny on 2016-05-01
I think I remember a launchpad bug about that problem but I do not have time at the moment to search for it.  I will see if I can find it later and report back.
You might be able to find it yourself as well.

---

### Post by ajgreeny on 2016-05-01
Here you go; one for chromium and another for firefox. They are a bit old but may give you some clues.
[https://bugs.launchpad.net/bugs/1244884](https://bugs.launchpad.net/bugs/1244884)
[https://bugs.launchpad.net/bugs/1035221](https://bugs.launchpad.net/bugs/1035221)
Good luck.

---

### Post by izznogooood on 2016-05-01
I think you gave me links with your "metadata" because for me they are broken ;)

---

### Post by vasa1 on 2016-05-01
> **izznogooood said:**
> I think you gave me links with your "metadata" because for me they are broken ;)

That happens sometimes. Just go to launchpad and enter the bug number in the search box!

**Edit**: The links you refer to should now work.

---

### Post by ajgreeny on 2016-05-02
Sorry abut the links, and thanks vasa1 for the edit to correct them.

I can't remember where I found them now but such things can happen occasionally.

---

