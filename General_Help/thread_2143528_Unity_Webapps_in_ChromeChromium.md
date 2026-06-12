---
title: "Unity Webapps in Chrome/Chromium"
date: 2013-05-09
forum: General Help
---

### Post by JonPaul on 2013-05-09
Has anyone managed to get unity webapps working in either chrome or chromium? No problem with firefox

I also can't see my gmail in the indicator-messages when I run chromium of chrome but it is fine in firefox

---

### Post by georgelappies on 2013-05-09
You need to install a plugin from the software center for chrome. Just launch synaptic (or the software centre) and search for chromium (it is only available for chromium, chrome will not work). 

Install the unity webapps plugin and logout and back in, now the webapps will work correctly.

---

### Post by JonPaul on 2013-05-09
Hoeziet George

Maybe this is because I am using 13.04. If I bring up firefox and open gmail the gmail webapp icon will open (gmail is pinned) and I can see the number of unread emails and if I click on the gmail icon it goes to the correct tab with gmail in it.

In chromium or chrome no chance........ 

Cheers mate

JonPaul

---

### Post by cerda on 2013-05-09
This is somehow related. I really like the web apps, i can manage to get them working on chromium too just like georgelappies advised but they do work better on firefox for me too. The problem is I had to give up using this web app funcionality because I can't get flash to work in firefox or chromium. So i'm using right now google chrome and theres no support for webapps.

Is just me that can't get flash to work in firefox? If someone manage to get webapps on chrome please tell us how to do it!

---

### Post by georgelappies on 2013-05-09
> **JonPaul said:**
> 

In chromium or chrome no chance........ 

Cheers mate

JonPaul

JonPaul, that is 100% correct because for it to work in Chromium (Chrome will not work atm) you must first install an additional package. from the terminal type in:

```

sudo apt-get install unity-chromium-extension

```

Enter your password and type 'y' if prompted. Once this has installed logout and log back in to Unity (or just reboot).

---

### Post by JonPaul on 2013-05-09
Thanks boet! let me give it a traai.

Cheers

JP

---

### Post by JonPaul on 2013-05-09
George

You have made my day Geniet jou naweek.

JP

---

### Post by beejee on 2013-08-09
Hi and sorry to dig up this old thread but it's the closest to what I am experiencing at the moment.

In firefox the webapps function normal, and I have them pinned to the launcher. Now when i choose chromium as my default browser i can launch the webapps but there is no indicator of them running, and in the gmail one there is no indicator of amount of mails. So I can launch the webapps but there is no way to switch to them and the integration is not working. This started from ubuntu 13.10, clean install. It used to work in perfectly in previous versions :/ 

I checked and the unity-chromium-extension is installed. I've tried clearing my chromium profile and starting again, but nothing works.
Since I really like the webapp functionality but use chromium I have firefox installed just for the webapps. I would rather use them in chromium so I only need to launch one browser, also because they look more like an app in chromium (no tab bar)
Any ideas what's going on?

---

### Post by JonPaul on 2013-09-09
Hi beejee

That is exactly my problem and that is why I gave up on chrome/chromium. If you like the chrome look (I do) you can change the firefox appearance to fxchrome.
Also, if you use android chrome has no add-ons - I mean, get real google.

JonPAul

---

