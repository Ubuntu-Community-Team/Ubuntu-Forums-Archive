---
title: "Youtube Player Issue"
date: 2013-01-14
forum: General Help
---

### Post by wesy2kn1 on 2013-01-14
I have done hours of googling on this issue to no avail. I went from chromium to chrome because of the issue and it cleared up for weeks and now with the latest update from chrome its appeared again.

The issue is I'm having multi-colored specs show up in videos (as seen in the image below). I have disabled all plugins, turned off hardware acceleration in flash and rebooted to no result.

Does anyone know what's causing this and maybe a solution? It's enough to drive me nuts because of course it doesn't happen on ads, only video and only on youtube.

Many thanks in advance for anyone who knows.

Ubuntu 12.04 LTS by the way

---

### Post by vasa1 on 2013-01-14
Also here: [http://ubuntuforums.org/showpost.php?p=12452382&postcount=1](http://ubuntuforums.org/showpost.php?p=12452382&postcount=1)

---

### Post by hydn79 on 2013-01-14
I think its video hardware related. You may be able to tweak it out. What's your video hardware specs?

---

### Post by wesy2kn1 on 2013-01-14
Intel on-board integrated video graphics card, Intel GM965 express Crestline to be exact.

---

### Post by Gster4 on 2013-01-14
> **wesy2kn1 said:**
> Intel on-board integrated video graphics card, Intel GM965 express Crestline to be exact.

Intel cards aren't that great.

Or maybe chrome's integrated flash dosen't work right.

try  firefox with Flash-Aid.  thats the best flash for me

or if you don't want a new browser, try youtube HTML5 at: [https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by wesy2kn1 on 2013-01-14
> **Gster4 said:**
> Intel cards aren't that great.

Or maybe chrome's integrated flash dosen't work right.

try  firefox with Flash-Aid.  thats the best flash for me

or if you don't want a new browser, try youtube HTML5 at: [https://www.youtube.com/html5](https://www.youtube.com/html5)

beginning to believe its some sort of quicktime codec issue. I'm getting the same thing with HTML5 video on youtube and now on twit.tv when I put their player in HTML5.

---

### Post by d4m1r on 2013-01-14
Very well could be cause of your graphics card and drivers...Intel under Ubuntu aren't very well supported as previously related...A few tips:

1) Check your video card drivers and update to any newer version if available (beta included)

2) Install Flash-aid within Firefox and run the wizard. It will reconfigure your flash settings within Firefox.

3) Continue using Chromium. It is able to use the latest available version flash which firefox is not.

---

### Post by chrisbarnes1992 on 2013-01-14
Having same issue with on 2 pcs and laptop. The one of the pc's has a AMD/ATI and the other one has nVida. Laptop is running Intel on board and same thing. 

This is across FireFox, Chrome, Chromium and Opera. Have have tried totally removing Restricted extras on all machines and re installing. Still no luck. I have not looked at driver issues as it is happening across all of the machines.

Ihave tried to use HTML 5 version of YouTube and to be honest it looks worse and the sound is jumpy if any at all.

I have been googleing and not come to any sucess yet. I am not totally bothers about the laptop and one desktop as they are just work horses.

Has anyone had any luck fixing this?

---

### Post by wesy2kn1 on 2013-01-15
> **d4m1r said:**
> Very well could be cause of your graphics card and drivers...Intel under Ubuntu aren't very well supported as previously related...A few tips:

1) Check your video card drivers and update to any newer version if available (beta included)

2) Install Flash-aid within Firefox and run the wizard. It will reconfigure your flash settings within Firefox.

3) Continue using Chromium. It is able to use the latest available version flash which firefox is not.

Drivers are the current version, don't use firefox personally. What I don't understand is: 

a) why when I moved from chromium to chrome for this reason and it was working fine the latest version started all of this again and b)why it would be a video issue when its only one site in a particular browser.

I'm not saying you're wrong at all. Just curious more than anything.

---

### Post by wesy2kn1 on 2013-01-15
See here's a screenshot of youtube in firefox without the plugin.

---

### Post by wesy2kn1 on 2013-01-25
OK everyone. I've found the culprit and I'm happy to report this is now fixed. Here are the steps (More descriptive screenshots below)

[LIST=1]
[*]Go to chrome://plugins
[*]click on details in the top right corner on the blue bar
[*]look for flash/shockwave v 11.5 and disable it.
[*]close and reopen chrome for changes to take effect and enjoy!
[/LIST]

---

### Post by emeyal on 2013-03-07
Great! Thank you wesy2kn1 - this solved the problem for me! :D

> **wesy2kn1 said:**
> OK everyone. I've found the culprit and I'm happy to report this is now fixed. Here are the steps (More descriptive screenshots below)

[LIST=1]
[*]Go to chrome://plugins
[*]click on details in the top right corner on the blue bar
[*]look for flash/shockwave v 11.5 and disable it.
[*]close and reopen chrome for changes to take effect and enjoy!
[/LIST]


---

### Post by Sozin on 2013-04-02
Fixed, thank you!!

---

