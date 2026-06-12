---
title: "Browser not supported !!!"
date: 2007-07-30
forum: General Help
---

### Post by satimis on 2007-07-30
Hi folks,

Ubuntu 7.04 desktop
Firefox


"Browser NOT support"!!!  "Install Internet Explorer"!!!

I encountered this problem several years ago on visiting some websites with "Mozilla" and/or Konqueror".  I found a solution suggested by a folk on Internet which can config Mozilla and Konqueror simulating as IE overcoming such a barrier.  Now I encountered the same problem again using Firefox visiting some websites.  Unfortunately I can't find the said website again.

On googling it suggests to install "ies4linux".  It requires "wine". (I don't have it running on this box)  Other than that suggestion are there any other solutions.  TIA


B.R.
satimis

---

### Post by Daskies on 2007-07-30
Could this be what you're looking for?
[http://johnbokma.com/mexit/2004/04/24/changinguseragent.html](http://johnbokma.com/mexit/2004/04/24/changinguseragent.html)

---

### Post by yknivag on 2007-07-30
My suggestion would be to install Opera.  This has the facility to emmulate pretty much any popular browser (including MSIE) which can be changed at wil, and on the fly, from the menu.  Far more elegant than messing around with MSIE under Wine.

Good luck.

---

### Post by AlexThomson_NZ on 2007-07-30
Ditto what Daskies suggested (or try Opera- it's a good browser)

Be sure to let the web admin for that site know too!  Non IE browsers is a significant chunk of the internet population.  Excluding non-IE is sooo 1997

---

### Post by kevinlyfellow on 2007-07-30
You can install the [User agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59")

---

### Post by satimis on 2007-07-30
> **kevinlyfellow said:**
> You can install the [User agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59")
kevinlyfellow,

Tks for your URL

Installed it and enabled "Tools --> User Agent Switcher --> IE7 (Window Vista)

Visited the previous sites in problem.  Unfortunately they don't support IE7 Window Vista only a blank page popup.  They support IE6.

B.R.
satimis

---

### Post by satimis on 2007-07-30
Hi folks,


Installed Opera 9.22

Problem remains intact.  

Warning;```
Your browser is not suitable for eWin. 

Please use Microsoft Internet Explorer 5.5 or above. Please refer to System Requirements
```

satimis

---

### Post by kevinlyfellow on 2007-07-30
> **satimis said:**
> Hi folks,


Installed Opera 9.22

Problem remains intact.  

Warning;```
Your browser is not suitable for eWin. 

Please use Microsoft Internet Explorer 5.5 or above. Please refer to System Requirements
```

satimis

Does it require activex?  Maybe you can link us to the site?

My copy of UAS has ie6, you can create a new one with the extension, under the preferences.  

Description: Internet Explorer 6 (Windows XP)
User Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
App Name: Microsoft Internet Explorer
App Version: 4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Platform: Win32

---

### Post by satimis on 2007-07-30
> **kevinlyfellow said:**
> Does it require activex?  

I don't know.

> 
Maybe you can link us to the site?

[http://www.hkjc.com/english/betting/acc_notices.htm](http://www.hkjc.com/english/betting/acc_notices.htm)

> 
My copy of UAS has ie6, you can create a new one with the extension, under the preferences.  

Only 3 options;
IE7 (Window Vista)
Opera 9.2 (Window Vista)
Netscape 4.8 (Window Vista)

---

### Post by nowshining on 2007-07-30
are u sure that's a safe site? and legit, also where do u get that incompatible page as I use firefox 2.0.0.5 in default settings mostly (no extensions) and the link u gave to the homepage comes up fine for me..


edit: N/m I see the apply now..by the way do u have java installed ??

---

### Post by satimis on 2007-07-30
> **nowshining said:**
> are u sure that's a safe site? and legit

The site is safe and legal.  It is operated for charities;
[http://www.hkjc.com/english/charity/charity_racing.asp](http://www.hkjc.com/english/charity/charity_racing.asp)

> 
edit: N/m I see the apply now..by the way do u have java installed ??
Yes and enabled.

Preferences --> Contents
check - enable JavaScript
check - ebable Java

Java
/usr/java/jre1.6.0_02/


satimis

---

### Post by nowshining on 2007-07-30
i doubt the charity thing... but I wouldn't trust anything that wanted Only IE to be able to at least display as Internet Explorer has not got Top Security, and have you used/been to this site before? if not I would be very weary of this site...

---

### Post by satimis on 2007-07-30
> **nowshining said:**
> i doubt the charity thing... but I wouldn't trust anything that wanted Only IE to be able to at least display as Internet Explorer has not got Top Security, and have you used/been to this site before? if not I would be very weary of this site...
This is my first time visiting this site.  I have no doubt on this organization which has been operated for prolonged time.  It is recognised by local Government and formerly was under the Queen of UK.


I encountered similar problem several years ago on visiting banks' website only IE was allowed.  I overcame the difficulty by making either mozila/konqueror/opera (I  can't recall exactly) looking like IE.


satimis

---

### Post by kevinlyfellow on 2007-07-30
> **satimis said:**
> I don't know.


[http://www.hkjc.com/english/betting/acc_notices.htm](http://www.hkjc.com/english/betting/acc_notices.htm)


Only 3 options;
IE7 (Window Vista)
Opera 9.2 (Window Vista)
Netscape 4.8 (Window Vista)

I wasn't asking if you have the option, I'm saying you can create the option.  Go to Tools -> Addons,  click on the extension and press the preferrences button.  On the side, highligh user agents, and press the add button.  Fill in the information that I had given you.

---

### Post by satimis on 2007-07-30
> **kevinlyfellow said:**
> I wasn't asking if you have the option, I'm saying you can create the option.  Go to Tools -> Addons,  click on the extension and press the preferrences button.  On the side, highligh user agents, and press the add button.  Fill in the information that I had given you.
Hi kevinlyfellow,

I did it as per your advice on posting #8 and moved it up to the top.   Still failed a blank page resulted.  On clicking "View Default" it always indicates "Mozilla/5...." disregarding having checked IE6/IE7/etc. on Tools --> User Agent Switcher

satimis

---

### Post by nowshining on 2007-07-30
try this,

type in the address bar of about:config then hit enter.

right click - New - String

In the name type the following general.useragent.override press ok then in the next box input Internet Explorers 5.5 or above Useragent, I got mine Set to blank :) to do that I had to press the spacebar first but anyway you can try that... and that reminds me I gottal do that on this ubuntu install of mozilla firefox..hehe..


[http://www.user-agents.org/](http://www.user-agents.org/)


edit: the link below shows your browser info... find it after Full User Agent string = 

[http://www.geocities.com/tony-alicea/detect.html](http://www.geocities.com/tony-alicea/detect.html)
:)

---

### Post by pak33m on 2007-07-30
satimis,

I could not help but not respond.  Guess it is because I am a loyal Opera fan.  I just want to offer some advise and a bit of a how to in order to get your page rendered in IE.

Maybe you could try to Install Opera and mask as IE through site link preferences.

[LIST=1]
[*]Download and install Opera (There are a few ways to go about this): 

**From Opera**

[LIST]
[*]Go here: [http://www.opera.com/download](http://www.opera.com/download) and then either 
[*]Type (in the terminal) ```
sudo dpkg -i opera_9.22-20070716.6-shared-qt_en_i386.deb
``` or right-click on opera_9.22-20070716.6-shared-qt_en_i386.deb and select _O_pen with Gdebi Installer
[/LIST]

**From Opera with wget**

[LIST]
[*]Type (at the terminal) ```
wget http://mirror.publicns.net/pub/opera/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb
``` 
[*]Type (at the terminal) ```
sudo dpkg -i opera_9.22-20070716.6-shared-qt_en_i386.deb
```
[/LIST]

**From the Canonical repositoy**
[LIST]
Type (at the terminal) ```
sudo gedit /etc/apt/sources.list
```
[*]Enter the line [HTML]deb http://archive.canonical.com/ubuntu feisty-commercial main[/HTML]
[*]Save sources.list
[*]Type (in the terminal ```
sudo apt-get update && sudo apt-get install opera
```
[/LIST]

[*]Set site preferences in Opera
[/LIST]

[LIST]
Go to the web page in question
[/LIST]
[LIST]
Go to _T_ools->_Q_uick Preferences->E_d_it site preferences..., select the Network tab and under Browser identification choose Mask as Internet Explorer
[/LIST]

[LIST]
Refresh the web page in question to see if the masking works
[/LIST]

Whew! Hope that helps.

---

### Post by satimis on 2007-07-30
Hi nowshining,


Tks for your advice.

> 
type in the address bar of about:config then hit enter.

right click - New - String

In the name type the following general.useragent.override press ok then in the next box input Internet Explorers 5.5 or above Useragent,

Did as advised.  On the string box - typed "Useragent"

> 
 I got mine Set to blank :) to do that I had to press the spacebar first but anyway you can try that... and that reminds me I gottal do that on this ubuntu install of mozilla firefox..hehe..


[http://www.user-agents.org/](http://www.user-agents.org/)

Could you pls explain in more detail about "Set to blank" and the use of the URL.  Tks.

> 
edit: the link below shows your browser info... find it after Full User Agent string = 

[http://www.geocities.com/tony-alicea/detect.html](http://www.geocities.com/tony-alicea/detect.html)
:)
Clicking above URL showing;```

Browser and platform info:

Browser = Microsoft Internet Explorer
Full version string = 4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Full User Agent string = Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Browser is currently Java enabled
Browser's Java (JDK) version =
Your computer's name =
Your IP address =
Platform = Win32
Monitor screen size (resolution) = 1024x1280 pixels
Screen color depth = 24 bits

```

But still failed.  Clicking "Apply Now" of following URL;
[http://www.hkjc.com/english/betting/acc_notices.htm](http://www.hkjc.com/english/betting/acc_notices.htm)

popup a blank page with "Applet startVM started" at the foot".  Do I miss some component/package installed?


satimis

---

### Post by satimis on 2007-07-30
> **pak33m said:**
> satimis,

I could not help but not respond.  Guess it is because I am a loyal Opera fan.  I just want to offer some advise and a bit of a how to in order to get your page rendered in IE.

Maybe you could try to Install Opera and mask as IE through site link preferences.

[LIST=1]
[*]Download and install Opera (There are a few ways to go about this): 

**From Opera**

[LIST]
[*]Go here: [http://www.opera.com/download](http://www.opera.com/download) and then either 
[*]Type (in the terminal) ```
sudo dpkg -i opera_9.22-20070716.6-shared-qt_en_i386.deb
``` or right-click on opera_9.22-20070716.6-shared-qt_en_i386.deb and select _O_pen with Gdebi Installer
[/LIST]

**From Opera with wget**

[LIST]
[*]Type (at the terminal) ```
wget http://mirror.publicns.net/pub/opera/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb
``` 
[*]Type (at the terminal) ```
sudo dpkg -i opera_9.22-20070716.6-shared-qt_en_i386.deb
```
[/LIST]

**From the Canonical repositoy**
[LIST]
Type (at the terminal) ```
sudo gedit /etc/apt/sources.list
```
[*]Enter the line [HTML]deb http://archive.canonical.com/ubuntu feisty-commercial main[/HTML]
[*]Save sources.list
[*]Type (in the terminal ```
sudo apt-get update && sudo apt-get install opera
```
[/LIST]

[*]Set site preferences in Opera
[/LIST]

[LIST]
Go to the web page in question
[/LIST]
[LIST]
Go to _T_ools->_Q_uick Preferences->E_d_it site preferences..., select the Network tab and under Browser identification choose Mask as Internet Explorer
[/LIST]

[LIST]
Refresh the web page in question to see if the masking works
[/LIST]

Whew! Hope that helps.
Hi pak33m,


Tks for your advice.

I already have Opera 9.22 download on Ubuntu repo and installed.  It is now running.

_T_ools->_Q_uick Preferences->E_d_it site preferences
is grey out.  Clicking it without response.


satimis

---

### Post by nowshining on 2007-07-31
lolz on the second box, u don't put useragent, that's why i provided a link to find the IE 5.5 or above (ur choice) user agent strings, lolz...


if you want IE7s try this

go back into about:config find the useragent override and double click on the name in the box remove - delete useragent and input to 

Mozilla/4.0 (compatible; MSIE 7.0b; Windows NT 6.0)

I'll try it at first tho.. :) hope u got it resolved tho..

---

### Post by nowshining on 2007-07-31
okay tried nothing will work, I hope opera solved this for u.. :)

---

### Post by satimis on 2007-07-31
> **nowshining said:**
> lolz on the second box, u don't put useragent, that's why i provided a link to find the IE 5.5 or above (ur choice) user agent strings, lolz...


if you want IE7s try this

go back into about:config find the useragent override and double click on the name in the box remove - delete useragent and input to 

Mozilla/4.0 (compatible; MSIE 7.0b; Windows NT 6.0)

I'll try it at first tho.. :) hope u got it resolved tho..
Hi nowshining,



Something strange happened here before performing the steps as advised.

Clicking "Apply Now" caused Firefox crashes.  Java Console tried to start but crashed finally.

Clicking following URL;
[http://www.geocities.com/tony-alicea/detect.html](http://www.geocities.com/tony-alicea/detect.html)

Firefox also crached..


Performed steps as advised.  Firefox crashed on clicking "Apply Now".  Java Console was starting and crashed finally.

It also crashed on clicking the abovementioned URL


B.R.
satimis

---

### Post by yknivag on 2007-07-31
I suspect that if setting Firefox and Opera to pretend to be MSIE hasn't worked then the website (or more likely some javasript/ActiveX embedded in it) is so badly coded as it will only display correctly by relying on one (or more) bugs in MSIE.

To be honest your time may be better spent feeding this bug back to the owner of the website than trying to get Firefox to imitate MSIE any further.

---

### Post by satimis on 2007-07-31
> **yknivag said:**
> I suspect that if setting Firefox and Opera to pretend to be MSIE hasn't worked then the website (or more likely some javasript/ActiveX embedded in it) is so badly coded as it will only display correctly by relying on one (or more) bugs in MSIE.

To be honest your time may be better spent feeding this bug back to the owner of the website than trying to get Firefox to imitate MSIE any further.
Hi yknivag,


ies4linux works for me here.

I installed it by following;
Installation: Ubuntu
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

and JVM on;
Mathieu Bonnet's posting on Dec 13, 2006
[http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?p=2541#2541](http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?p=2541#2541)


I'm NOT interested to register online betting.  Additionally it needs e-certificate on registration which has to be purchased on local Post Office.

Curiosity pushes me to start this thread.  Several year ago I encountered the same problem on online banking.  It also required M$ IE to work.  Finally I made mozilla/konqueror/Opera to work instead. (I can't recall exactly which of them)  My bank refused to entertain my request adding mozilla to my a/c as browser on the ground of security.

It seems to me that Bill Gates is trying to push us back to M$ Windows.


Folks, lot of tks for your advice and effort in assisting me.


B.R.
satimis

---

