---
title: "Finally got Internet Explorer working!"
date: 2005-08-18
forum: General Help
---

### Post by [censored] on 2005-08-18
First off, let me say that I do NOT like IE. Give me firefox or konqueror any day!

Unfortunately, most ppl in the world use IE. So if u'r designing web pages, you need to know what these pages are going to look like to about 90% of people on the internet.

'Till now, the problem installing IE, for me, has been that it always produced a "stub" error then hanged forever. The stub error was: 

fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub

Had the same problem whether I tried installing manually, using the instructions provided at frankscorner.org, or whether I used the "winetools" package provided from the ubuntu repositories.

Anyway, I did some googling, and found the solution is to open a terminal, cd to the directory where you've saved the IE installer (in this case, IE service pack 6), and type:

WINEDLLOVERRIDES="riched32=n" wine ie6setup.exe 

I found this solution here 
[http://groups.google.com.au/group/comp.emulators.ms-windows.wine/msg/104abec81ef8b4fe?hl=en&](http://groups.google.com.au/group/comp.emulators.ms-windows.wine/msg/104abec81ef8b4fe?hl=en&)

Reportedly, this is due to a bug in the wine 20050419, which is the only version I could find via ubuntu's apt-get repositories.

Anyway, just thought I'd share this, just incase anybody was suffering the same problem, and tearing their hair out as I was.

---

### Post by Donshyoku on 2005-08-18
Oh man, I have been dying for IE in Linux! :---) 

Joking, that is good accomplishment.  And I understand why you need to see how IE displays things in your field.  Rock on!

---

