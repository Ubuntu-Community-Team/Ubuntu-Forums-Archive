---
title: "Fn+F10, Side arrow keys (right and left) and Ctrl don't work."
date: 2016-01-08
forum: General Help
---

### Post by Anomime on 2016-01-08
Hi my name is not important.. but I have a K450J Asus Laptop and i would like to troubleshoot closer and i recently installed XUbuntu (i still had the same problems with Ubuntu), formatted my disk and still have the problem, took my computer to the store and the keyboard is all good something in Linux is messing with my keyboard but i don't know what it is. Would like your help.
     Oh and yeah i already did ```
xev
``` and... no event from Fn+ F10, neither individually from both, no event either from Ctrl and side arrow keys. 
     Please i need your help.

---

### Post by egeezer on 2016-01-08
This will not answer your question, but it might point you toward some help.  I've encountered the same type of thing myself, and found the answer was beyond what I was willing to attempt.

If xev gives no return to your key press, try evtest, which you can install with:
```
                         sudo apt-get install evtest
  
```
Then run
```
                         sudo evtest
  
```
                        That will give you the scancodes, which are identifiers of the kernel events caused by pressing the two keys. If they register there, probably responding with something like 
```
Event: time 1435906588.943349, type 4 (EV_MSC), code 4 (MSC_SCAN), value 3b
```
you will know the keys operate electrically, but that the present kernel driver doesn't recognize them.

I can't help there, but the search page I've linked would be the first place to look.

I wish you more luck than I had in resolving this!

[URL="https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=keycodes+and+scancodes&sa=Search"]https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=keycodes+and+scancodes&sa=Search

My own earlier question on these forums:

[http://ubuntuforums.org/showthread.php?t=2307801](http://ubuntuforums.org/showthread.php?t=2307801)
[/URL]

---

### Post by Anomime on 2016-01-08
Thank you, I will try. 

Update:
I recently ran evtest but when i pressed the buttons wich were causing me trouble... They were unresponsive, they didn't even get the scan-code.

---

