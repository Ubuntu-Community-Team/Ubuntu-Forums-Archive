---
title: "How to set default browser in xubuntu?"
date: 2013-06-18
forum: General Help
---

### Post by jonawright on 2013-06-18
There seem to be several ways to set default browser, but all of them leave
Firefox as default browser.
Suppose I want to use Chrome
1) Can start Chrome and then it asks if you want to set it as default. doesn't work\
2) preferred applications.  I set it to chrome.  doesn't work and in fact after awhile
    it doesn't think i have set anything.
3)There is an icon labelled WebBrowser on the menu.  One can set the default browser.
   After a while, it also "forgets" that it has been set.  

Unfortunately My FireFox is broken so this is a real pain.  (haven't been able to fix firefox either
but that is a different issue.)

I am running xubuntu 13.04
   
There have been similar posts in the past, but apparently setting the default in preferred applications
worked for them.

---

### Post by vasa1 on 2013-06-18
What do you see when you run:
```
sudo update-alternatives --config x-www-browser
```?

---

### Post by Dennis N on 2013-06-18
The default browser comes into play when opening an html file when a browser is not yet open (such as a saved file).

Here is a method of setting the default browser you did not mention you had tried, and it is the only one I found that works in Lubuntu 13.04 - I understand you are using Xubuntu 13.04 - but perhaps it will work there too:

Right-click on an html file saved in your file system. Select "properties" then use the "Open With" list to select your desired web browser. I found this changes the default.

Note: I can't test this in Xubuntu 13.04, since I only have Firefox installed there.

---

### Post by Buntu Bunny on 2013-06-18
Xubuntu 12.04 here. I have launchers for both Firefox and Chrome on my bottom panel. I can select the one I want, depending on what I wish to do. Would that work for you?

---

### Post by HiImTye on 2013-06-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
what's the output of```
grep -E 'http|html|xml|chrome=' $HOME/.local/share/applications/mimeapps.list
```

---

