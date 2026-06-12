---
title: "HBO Now and Google Chrome in Ubuntu 64 bit GNU/Linux"
date: 2015-08-08
forum: General Help
---

### Post by Welly Wu on 2015-08-08
I have both Lenovo IdeaPad Y510P and ZaReason Zeto PCs and I use Ubuntu 14.04.3 64 bit LTS GNU/Linux. I use Google Chrome 44.x 64 bit. I added the User Agent Switcher for Chrome and I added my own custom user agent for Microsoft Windows using the following information:

User Agent Name: Chrome
User Agent String: Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2228.0 Safari/537.36
Group: Append
Indicator Flag: 44

I am now able to play my Amazon Prime Instant Videos within Google Chrome 44 64 bit using Ubuntu 64 bit LTS GNU/Linux. Success! However, my HBO Now doesn't play videos. I know that I am in uncharted territory so I wanted to know if anyone else has made similar progress or has solved my problems. Is it possible to play HBO Now in Google Chrome 64 bit in GNU/Linux? If so, then please tell me how to do it. I feel like I am close to the solution, but I am also out of luck in terms of ideas. Please guide me if possible or tell me to stop now. Thank you.

---

### Post by Welly Wu on 2015-08-08
After more research, it seems that I need the Widevine plug-in which is not available for GNU/Linux within Google Chrome. This is why HBO Now is not playing videos. It does work with Mozilla Firefox as I did install the Pipelight Project to enable Microsoft Silverlight, Adobe Flash, and Widevine. However, I have a choice of trying Chromium and installing the Widevine dependencies by myself, but I am not interested in taking those steps yet. I may be up against a brick wall for now. Does anyone know when Google will include Widevine in future Chrome for GNU/Linux versions?

---

### Post by mc4man on 2015-08-08
There is a widevine plugin bundled in chrome already, maybe it doesn't work on HBO now in linux? 
(try checking 'always allow..'

---

### Post by Welly Wu on 2015-08-08
I clicked always allow and HBO Now still doesn't play videos. I did not know that the GNU/Linux version of Google Chrome already comes with Widevine CDM. What other options do I have left to make this work? What am I missing here?

---

### Post by mc4man on 2015-08-08
Sorry, don't know, seems all solutions for HBO now in linux  are for firefox..
(just wanted to save you time looking for a chrome plugin that's already there...

---

### Post by Welly Wu on 2015-08-08
Thank you for pointing out the Widevine CDM exists in Google Chrome and for your help. HBO Now told me that they don't support GNU/Linux including Ubuntu right now.

---

