---
title: "Strange Firefox Problem - please help"
date: 2015-06-16
forum: General Help
---

### Post by GrouchyGaijin on 2015-06-16
Hi Guys,

I am running Ubuntu 14.04 64 bit with Firefox version  38 for Ubuntu
This is complected and I've tried to explain everything clearly.


I noticed some strange behavior  today.
I have several URL saved as .desktop files.


I'll use webupd8.org as an example.
The code for the exec in the desktop file is:
```
 Exec=xdg-open http://www.webupd8.org/ 
```


Today I noticed that if I try to  go to webupd8.org, or most other sites, by launching the .desktop file for that site or by typing  the url 
```
http://www.webupd8.org/ 
``` in the Dash Firefox opens to a completely different site.  The site that opens up is a website I set up for my kids' grandparents to watch videos and see photos of the kids.  This website opens every time.  I am **not** being directed to a random site each time.  This is the case when I try to visit webupd8.org OR any of several different sites using the .desktop file or entering the desired url in the Dash.  Each time I am directed to my own domain.


It happens that I also have several sites saved in a quicklist in the Firefox icon in the sidebar launcher thing in Ubuntu.
**In the case of the quicklist the code for the exec is slightly different and it still responds as it should.**  In this case I have:
```
Exec=firefox -new-tab http://www.webupd8.org/ 
```


Furthermore, if I change my default browser to Opera, for example both the .desktop files and entering the url directly into the Dash work as they should.


To Recap:


When Firefox is the default browser entering a url into the Dash or using a .desktop file to surf to a desired site results in my being redirected to my own domain (which is remotely hosted and not on this computer).


If, however, I edit the Exec command in the .desktop file from ```
 Exec=xdg-open <url> 
``` to ```
Exec=firefox -new-tab  <url> 
``` the .desktop file will open Firefox and go to the desired website.


If I change the default browser from Firefox to another browser everything works as it should and always has until now.  That is, with Opera for example, both ```
 Exec=xdg-open <url> 
``` and ```
Exec=firefox -new-tab  <url> 
``` result in the browser opening and going to the intended site.  Typing a url into Dash is **not** a problem if the default browser is not Firefox.


Has anyone seen this before?  If so, how did you fix it?

---

### Post by Miykel on 2015-06-16
Sounds a bit like your home page is set to that url, perticulally if you go to new tab and it opens correctly

---

### Post by GrouchyGaijin on 2015-06-16
No it is not and even if it were that would not explain why entering a url in Dash would result in going to the wrong web site.

---

### Post by GrouchyGaijin on 2015-06-17
[U]UPDATE 
[/U]
I tried renaming the Firefox folder which is inside ~/.mozilla and then launched Firefox and set it as the default browser. 
I tried going to a website from the Dash and still went to the incorrect website. In other words, this did not help.

---

### Post by GrouchyGaijin on 2015-06-17
@Miykel

Apologies to Miykel, he was in a sense correct.
When I checked the home page url in the Firefox preferences the home page was set to startpage.com.
However, when I took a look at About this computer/Default applications next to Web the default application had somehow become set to the .desktop file I have that takes me to the admin login page of my website.

I changed it back to Firefox and the problem disappeared.

---

