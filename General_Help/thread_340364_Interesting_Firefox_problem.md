---
title: "Interesting Firefox problem"
date: 2007-01-17
forum: General Help
---

### Post by darweth on 2007-01-17
Sometimes a new window of Firefox will not pop up.  What I mean by that is that it WILL show up in the taskbar/window list (even the workspace box), but I cannot access it.  I maximize it and nothing happens.  Oddly enough the workspace box will show it as being open, but it sure as hell isn't actually open on my screen.  This does not normally happen, but it does happen often enough to be a pain in the butts.  Anyone else experience this behavior or have any solutions in mind?

On a related note: Is there anyway to FORCE Firefox to open all links in TABS without having to right-click and manually doing it?  I have it set in System-Preferences AND Firefox preferences... but links from within sites still insist on opening up a new Firefox window.  This often when the aforementioned problem occurs.

---

### Post by mcduck on 2007-01-17
I had the same problem some time ago when using Compiz/Beryl, but it has stopped happening without me doing anything about it..

Anyway, to your problem with tabs the solution is installing Tab Mix Plus extension, it allows you to configure the way Firefox uses tabs just the way you want.

---

### Post by darweth on 2007-01-17
Thank you for the reply.  I do use Beryl.  It was wowee at first but I am considering a switch to a simple Fluxbox. :)  I suppose that would correct the problem.

I will check out the extension!

---

### Post by NT4usB on 2007-01-17
Type in the browser window.:```
about:config
```Type in the search window.:```
browser.link.open
```
You should get three results.
(double click to) Set:
browser.link.open_external = 3
browser.link.open_newwindow = 3
browser.link.open_newwindow.restriction = 2

This will make everything open in a tab/new tab. no extra windows.
But you can tweak them (0-3) in one tab and load stuff in another to see how they affect opening in tabs/windows.
More reading:
[http://kb.mozillazine.org/Browser.link.open_external](http://kb.mozillazine.org/Browser.link.open_external)
[http://kb.mozillazine.org/Browser.link.open_newwindow.restriction](http://kb.mozillazine.org/Browser.link.open_newwindow.restriction)

---

### Post by josephmc on 2007-01-17
thanks! worked for me.

---

