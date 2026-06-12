---
title: "Duplicate icons of the same application"
date: 2015-06-04
forum: General Help
---

### Post by MantasJ on 2015-06-04
I am running Ubuntu 15.04 and Docky as my launcher. To run OriginPro under wine from launcher I created .desktop and pinned it to my Docky, but when it starts it opens seperate icon (which I can't pin to Docky by right-click) and I want it to run under the one I clicked. I had a similar problem with Matlab (not wine), but changing .desktop name to exactly match the one that opens when I click on it made them group, but it doesn't work for OriginPro. 
Looking for help !

---

### Post by kostkon on 2015-06-04
You could try this: add the following line into your .desktop file
```
StartupWMClass=wineapp.exe
```
whereas 'wineapp.exe' would be the wm class of your app.

To get the wm class, start your app, then in a terminal, do
```
xprop WM_CLASS
```
and when the cursor changes, click on the app's window.
It should print out 2 values, in this case use the one that contains the extension ".exe".

---

